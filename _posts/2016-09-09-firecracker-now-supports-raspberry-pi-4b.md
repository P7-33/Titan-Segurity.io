---
title: 'Firecracker now supports raspberry pi 4B'
date: 2019-11-05T04:29:00+01:00
draft: false
---

![](https://avatars2.githubusercontent.com/u/44477506?s=400&v=4 "gicv2 support by bchalios · Pull Request #1235 · firecracker-microvm/firecracker · GitHub")  

I think that this logic can be nicely abstracted and moved in the trait:

*   `init_device()` is already a trait method
*   for the logic related to setting the device attributes we can have a trait method

```
 fn init_device_attributes(fd: &DeviceFd, vcpu_count: u64) -> Result<()> where Self: Sized; 
```

and implement it differently for GICv2 vs GICv3. v2 impl for example:

*   `finalize_device` is already defined in the trait
*   the part that actually creates the device can also be abstracted in a method that is declared in the trait and defined separately for GICv2 and GICv3:

trait :

```
 fn create_device(fd: DeviceFd, vcpu_count: u64) -> Box where Self: Sized; 
```

v2 impl:

```
fn create_device(fd: DeviceFd, vcpu_count: u64) -> Box { Box::new(GICv2 { fd: fd, properties: [ GICv2::get_dist_addr(), GICv2::get_dist_size(), GICv2::get_cpu_addr(), GICv2::get_cpu_size(), ], }) } 
```

And then we can have `new` defined in the trait:

```
 fn new(vm: &VmFd, vcpu_count: u64) -> Result> where Self: Sized, { let vgic_fd = Self::init_device(vm)?; Self::init_device_attributes(&vgic_fd, vcpu_count); Self::finalize_device(&vgic_fd)?; Ok(Self::create_device(vgic_fd, vcpu_count)) } 
```

The only problem here is that we would have to pass all the creation params for any GIC implementation. For example GICv2 doesn't need the vcpu\_count but we have to pass it anyway. So it's not ideal. Also there would be some coupling. Which for the moment seems ok but I don't know how it will affect future GIC devices support.

Do you think it would make sense to refactor it like this ? Considering extensibility and future GIC devices support.

  
  
from Hacker News https://ift.tt/338r8Cr