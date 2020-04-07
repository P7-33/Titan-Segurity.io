---
title: 'A Thought Experiment: Using the ECS Pattern Outside of Game Engines'
date: 2019-12-28T08:01:00+01:00
draft: false
---

classDiagram GraphicalEntity

The diagonal lines in a `Hatch` don’t actually exist on the drawing though. Instead they’re rendered a fixed distance apart regardless of the zoom level, so we’ll also need to add a `zoom_level` parameter to the `decompose()` function. It’s a little annoying because things like `Line` and `Circle` don’t actually care about how far we’re zoomed in, but we’re already bloating the `GraphicalEntity` class with unused properties like `stroke` so what harm will a little extra bloat do?

You can see where this is going. For every new property we could try to reuse code by introducing intermediate classes, but it won’t be long before we code ourselves into a corner. Unfortunately, the real world doesn’t fit into a tidy inheritance hierarchy.

It’s not long before your class hierarchy is ten levels deep, bloated with loads of unnecessary data and methods, and there are so many levels of “abstraction” it’s hard to figure out what’s actually going on.

Another problem is you’ll frequently fall into the [Refused Bequest anti-pattern](https://refactoring.guru/smells/refused-bequest). This is where a parent class exposes a method that doesn’t actually make sense for some child classes so the child class overrides it to always throw a `throw new InvalidOperationException()`. Everything still compiles, but now every time you invoke the method on the parent class there’ll be a niggling feeling in the back of your head that things may blow up at runtime.

That’s not a fun feeling. Especially when you’re letting your project manager demo the application and he starts experimenting with combinations of operations you never anticipated or tested for… Don’t ask me how I know this 😑

As an aside, have you ever heard of the [Circle-Ellipse Problem](https://wiki.c2.com/?CircleAndEllipseProblem)?

> If we have an application that uses circles and ellipses (e.g. a graphics program), should we have two classes `Circle` and `Ellipse`? Which should inherit from which, if at all? A circle is a special kind of ellipse, viz. one where the two foci coincide. But if an `Ellipse` is mutable, a `Circle` is mutable too, and can be made a non-circle.
> 
> Or should we only have an `Ellipse`? But if we then create an `Ellipse` that happens to represent a circle, we cannot ask it for its radius, because `Ellipse` has no `radius()` method.

Most object-oriented languages are designed so that an object’s underlying type will be the same for its entire lifetime. This makes things interesting when users want to scale a `Circle` without maintaining aspect ratio. It means you can’t just give the `GraphicalEntity` a `scale()` method which mutates the object in-place, you need to change the entire API so a `Circle` can return an `Ellipse` when the `x` and `y` scale factors aren’t the same.

If you’ve been programming for a while you will have probably come across the mantra, _“Composition over Inheritance”_. It’s exactly these sorts of design problems composition is attempting to solve, and ECS is just one way to formalise composition… By breaking the world up into `Components` (data that can be attached to things) and `Systems` (behaviour).

Creating an ECS-based CAD Library
---------------------------------

I’m a big fan of the [`specs`](https://crates.io/crates/specs) crate, so that’s what I used when trying to implement an ECS-based CAD library.

I’m also really boring when it comes to naming things, so the project is simply called [_A Rust CAD System_](https://github.com/Michael-F-Bryan/arcs), or `arcs` for short. This is also a nice pun on the fact that one of the basic drawing primitives of any CAD library is the _Arc_ 😁

All graphical entities have a `DrawingObject` component which contains the data which is needed while rendering.

```
// arcs/src/components/drawing_object.rs  /// Something which can be drawn on the screen. #[derive(Debug, Clone, PartialEq)]  pub  struct DrawingObject  {  pub  geometry: Geometry,  /// The [`Layer`] this [`DrawingObject`] is attached to.  pub  layer: Entity,  }  impl  Component  for  DrawingObject  {  type Storage  =  FlaggedStorage<Self,  DenseVecStorage<Self>>;  }  /// The geometry of a [`DrawingObject`]. #[derive(Debug, Clone, PartialEq)]  #[non_exhaustive]  pub  enum Geometry  {  Line(Line),  Arc(Arc),  Point(Point),  ...  } 
```

You may have noticed that we’re explicitly implementing `Component` for `DrawingObject` instead of using the custom derive. This is because we want to store this component using `FlaggedStorage`, a wrapper type which lets you subscribe to change notifications.

You’ll see why change notifications are useful later on.

Rendering
---------

I’m using the [`piet` crate](https://crates.io/crates/piet) as an abstraction over a drawing canvas. This is awesome because not only has all the hard work been implemented, including tricky things like fonts and gradients, but there are also backends for all the major platforms. Including the browser. This means we can create a an online demo later on by compiling to WebAssembly, which is a massive boon when trying to show other people your work… It’s also just a well-written library and does exactly what I need.

The `piet-web` backend introduces a minor complication (in the form of mental overhead) because its `RenderContext` borrows JavaScript objects. That means every time we need to render we’ll have to create a temporary `System` which holds a reference to a particular piet backend, instead of implementing `System` on the `Renderer` directly.

```
// arcs/render/renderer.rs  /// Long-lived state used when rendering. #[derive(Debug, Clone)]  #[non_exhaustive]  pub  struct Renderer  {  pub  viewport: Viewport,  pub  background: Color,  }  impl  Renderer  {  pub  fn new(viewport: Viewport,  background: Color)  -> Self  {  Renderer  {  viewport,  background,  }  }  /// Get a [`System`] which will render using a particular [`RenderContext`].  pub  fn system<'a,  R>(  &'a  mut  self,  backend: R,  window_size: Size,  )  -> impl  System<'a>  +  'a  where  R: RenderContext  +  'a,  {  RenderSystem  {  backend,  window_size,  renderer: self  }  }  }  #[derive(Debug, Clone, PartialEq)]  pub  struct Viewport  {  /// The location (in drawing units) this viewport is centred on.  pub  centre: Vector,  /// The number of pixels each drawing unit should take up on the screen.  pub  pixels_per_drawing_unit: f64,  }  /// The [`System`] which actually renders things. /// /// This needs to be a temporary object "closing over" the [`Renderer`] and some /// [`RenderContext`] due to lifetimes. /// /// In particular, the `RenderContext` for the `piet_web` crate takes the HTML5 /// canvas by `&mut` reference instead of owning it, and we don't want to tie our /// [`Renderer`] to a particular stack frame because it's so long lived (we'd end /// up fighting the borrow checker and have self-referential types). #[derive(Debug)]  struct RenderSystem<'renderer,  B>  {  backend: B,  window_size: Size,  renderer: &'renderer  mut  Renderer,  } 
```

Going through the entire rendering system is out of scope for this article, but I’ll walk you through how we use specs `Component`s to nicely manage things like the different styling information attached to the various graphical entities.

The `RenderSystem`’s `System` impl is surprisingly simple. We break the task up into calculating the draw order (the user can specify that certain objects should be drawn on top of others) and then iterating through each entity to be drawn and calling `self.render()` on them.

```
// arcs/render/renderer.rs  impl<'world,  'renderer,  B: RenderContext>  System<'world>  for  RenderSystem<'renderer,  B>  {  type SystemData  =  (DrawOrder<'world>,  Styling<'world>);  fn run(&mut  self,  data: Self::SystemData)  {  // make sure we're working with a blank screen  self.backend.clear(self.renderer.background.clone());  let  (draw_order,  styling)  =  data;  let  viewport_dimensions  =  self.viewport_dimensions();  for  (ent,  obj)  in  draw_order.calculate(viewport_dimensions)  {  self.render(ent,  obj,  &styling);  }  }  } 
```

We’ve created helper struct called `DrawOrder` which holds a reference to each set of `Component`s we’ll need while calculating the draw order.

```
// arcs/src/render/renderer.rs  /// The state needed when calculating which order to draw things in so z-levels /// are implemented correctly. #[derive(SystemData)]  struct DrawOrder<'world>  {  entities: Entities<'world>,  drawing_objects: ReadStorage<'world,  DrawingObject>,  layers: ReadStorage<'world,  Layer>,  bounding_boxes: ReadStorage<'world,  BoundingBox>,  }  impl<'world>  DrawOrder<'world>  {  fn calculate(  &self,  viewport_dimensions: BoundingBox,  )  -> impl  Iterator<Item  =  (Entity,  &'_  DrawingObject)>  +  '_  {  type EntitiesByZLevel<'a>  =  BTreeMap<Reverse<usize>,  Vec<(Entity,  &'a  DrawingObject)>>;  // Iterate through all drawing objects, grouping them by the parent  // layer's z-level in reverse order (we want to yield higher z-levels  // first)  let  mut  drawing_objects  =  EntitiesByZLevel::new();  // PERF: This function has a massive impact on render times  // Some ideas:  // - Use a pre-calculated quad-tree so we just need to check items  // within the viewport bounds  // - use a entities-to-layers cache so we can skip checking whether to  // draw an object on a hidden layer  for  (ent,  obj,  bounds)  in  (  &self.entities,  &self.drawing_objects,  MaybeJoin(&self.bounding_boxes),  )  .join()  {  let  Layer  {  z_level,  visible  }  =  self  .layers  .get(obj.layer)  .expect("The object's layer was deleted");  // try to use the cached bounds, otherwise re-calculate them  let  bounds  =  bounds  .copied()  .unwrap_or_else(||  obj.geometry.bounding_box());  if  *visible  &&  viewport_dimensions.intersects_with(bounds)  {  drawing_objects  .entry(Reverse(*z_level))  .or_default()  .push((ent,  obj));  }  }  drawing_objects.into_iter().flat_map(|(_,  items)|  items)  }  } 
```

It’s not uncommon for a drawing to contain hundreds of thousands of graphical entities, so it’s really important to reduce the amount of work that gets done. You can see from the `PERF` comment that we’re willing to trade off extra memory usage if it means we can reduce the rendering system’s execution time.

Let me know if you can see possible bugs or other improvements by making an issue against [the project’s issue tracker](https://github.com/Michael-F-Bryan/arcs/issues). I’m especially keen to hear if you’ve had to tackle these sorts of problems before!

When rendering a `Point`, there are a couple pieces of information we’ll need. These are stored using the `PointStyle` component.

```
// arcs/components/styles.rs  #[derive(Debug, Clone, Component)]  #[storage(DenseVecStorage)]  pub  struct PointStyle  {  pub  colour: Color,  pub  radius: Dimension,  }  impl  Default  for  PointStyle  {  fn default()  -> PointStyle  {  PointStyle  {  colour: Color::BLACK,  radius: Dimension::default(),  }  }  }  /// A dimension on the canvas. #[derive(Debug, Copy, Clone, PartialEq)]  pub  enum Dimension  {  /// The dimension should always be the same size in pixels, regardless of  /// the zoom level.  Pixels(f64),  /// A "real" dimension defined in *Drawing Space*, which should be scaled  /// appropriately when we zoom.  DrawingUnits(f64),  }  impl  Dimension  {  pub  fn in_pixels(self,  pixels_per_drawing_unit: f64)  -> f64 {  match  self  {  Dimension::Pixels(px)  =>  px,  Dimension::DrawingUnits(units)  =>  units  *  pixels_per_drawing_unit,  }  }  }  impl  Default  for  Dimension  {  fn default()  -> Dimension  {  Dimension::Pixels(1.0)  }  } 
```

Rendering a `Point` then becomes a process of:

1.  Find the `PointStyle` to use for this entity
2.  Define a `kurbo::Shape` for the point’s outline, in this case a `Circle`
3.  Tell the backend to fill the `Circle` with the desired colour
    
    ```
    // arcs/src/render/renderer.rs  impl<'world,  'renderer,  B: RenderContext>  RenderSystem<'renderer,  B>  {  fn render(  &mut  self,  ent: Entity,  drawing_object: &DrawingObject,  styles: &Styling,  )  {  match  drawing_object.geometry  {  Geometry::Point(ref  point)  =>  {  self.render_point(ent,  point,  drawing_object.layer,  styles)  },  ...  }  }  /// Draw a [`Point`] as a circle on the canvas. fn render_point(  &mut  self,  entity: Entity,  point: &Point,  layer: Entity,  styles: &Styling,  )  {  let  fallback  =  PointStyle::default();  let  style  =  styles  .point_styles  // the style for this point may have been overridden explicitly  .get(entity)  // otherwise fall back to the layer's PointStyle  .or_else(||  styles.point_styles.get(layer))  // fall back to the global default if the layer didn't specify one  .unwrap_or(&fallback);  let  point  =  Circle  {  center: self.to_viewport_coordinates(point.location),  radius: style  .radius  .in_pixels(self.renderer.viewport.pixels_per_drawing_unit),  };  self.backend.fill(point,  &style.colour);  }  /// Translates a [`Vector`] from drawing space to a [`kurbo::Point`] on the /// canvas. fn to_viewport_coordinates(&self,  point: Vector)  -> kurbo::Point  {  super::to_canvas_coordinates(  point,  &self.renderer.viewport,  self.window_size,  )  }  } 
    ```
    

Bounding Boxes
--------------

To make sure we only try to draw things within the rendering system’s viewport each graphical object is given an [axis-aligned `BoundingBox`es](https://stackoverflow.com/questions/22512319/what-is-aabb-collision-detection) component. To avoid needing to remember to update this `BoundingBox` component every time an object is updated we can make use of the `DrawingObject`’s `FlaggedStorage` and create a `SyncBounds` system which will subscribe to changes and ensure object bounds are kept in sync.

The `SyncBounds` implementation is copied almost directly from the docs for `FlaggedStorage`.

```
// arcs/systems/bounds.rs  /// Lets us keep track of a [`DrawingObject`]'s rough location in *Drawing /// Space*. #[derive(Debug)]  pub  struct SyncBounds  {  changes: ReaderId<ComponentEvent>,  to_update: BitSet,  removed: BitSet,  }  impl  SyncBounds  {  pub  const  NAME: &'static  str  =  module_path!();  pub  fn new(world: &World)  -> SyncBounds  {  SyncBounds  {  changes: world.write_storage::<DrawingObject>().register_reader(),  to_update: BitSet::new(),  removed: BitSet::new(),  }  }  }  impl<'world>  System<'world>  for  SyncBounds  {  type SystemData  =  (  WriteStorage<'world,  BoundingBox>,  ReadStorage<'world,  DrawingObject>,  Entities<'world>,  );  fn run(&mut  self,  data: Self::SystemData)  {  // clear any left-over flags  self.to_update.clear();  self.removed.clear();  let  (mut  bounds,  drawing_objects,  entities)  =  data;  // find out which items have changed since we were last polled  for  event  in  drawing_objects.channel().read(&mut  self.changes)  {  match  *event  {  ComponentEvent::Inserted(id)  |  ComponentEvent::Modified(id)  =>  {  self.to_update.add(id);  },  ComponentEvent::Removed(id)  =>  {  self.removed.add(id);  },  }  }  for  (ent,  drawing_object,  _)  in  (&entities,  &drawing_objects,  &self.to_update).join()  {  bounds  .insert(ent,  drawing_object.geometry.bounding_box())  .unwrap();  }  for  (ent,  _)  in  (&entities,  &self.removed).join()  {  bounds.remove(ent);  }  }  } 
```

We may also want to override the `System::setup()` method to go through all `DrawingObject` entities and make sure they’ve got a `BoundingBox` component.

In general, if we ever need to cache something we’ll create one of these bookkeeping `System`s. We can take advantage of the `DispatcherBuilder` to register any necessary bookkeeping tasks with a `Dispatcher` using a function defined in the `systems` module.

```
// arcs/systems/mod.rs  /// Register any necessary background tasks with a [`DispatcherBuilder`]. pub  fn register_background_tasks<'a,  'b>(  builder: DispatcherBuilder<'a,  'b>,  world: &World,  )  -> DispatcherBuilder<'a,  'b>  {  builder.with(SyncBounds::new(world),  SyncBounds::NAME,  &[])  } 
```

Conclusion
----------

As far as I can tell, using an ECS for managing the data in a CAD library seems to work pretty well. I’m thinking of building an online editor for Ladder Logic programs (`specs` can be compiled to WebAssembly without a problem), so I’ll hopefully make another article later on telling you how things go.

I’ve also [experimented](https://github.com/Michael-F-Bryan/iec) with using `specs` as the backend for a compiler in the past. When writing a compiler you often end up implementing a poor man’s ECS anyway (i.e. IR nodes are entities, each “pass” is a `System`, and the various side-tables and metadata can be attached to IR nodes as `Components`) so from a theoretical perspective using a proper ECS in a compiler makes a lot of sense.

Once I’ve got a basic editor for Ladder Logic programs I’m planning to revisit this way idea when compiling programs to an executable form (e.g. [WebAssembly](http://adventures.michaelfbryan.com/posts/wasm-as-a-platform-for-abstraction/)).

See Also:

  
  
from Hacker News https://ift.tt/2Q26Vdu