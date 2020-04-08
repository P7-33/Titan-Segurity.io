---
title: 'Streamlit: Turn a Python script into an interactive data analysis tool'
date: 2019-10-06T01:46:00+01:00
draft: false
---

![](https://miro.medium.com/freeze/max/1000/1*Mbn2SxozueUkGKPW1NJkOw.gif "Turn Python Scripts into Beautiful ML Tools - Towards Data Science")  

Turn Python Scripts into Beautiful ML Tools
===========================================

Introducing Streamlit, an app framework built for ML engineers
--------------------------------------------------------------

Coding a semantic search engine with real-time neural-net inference in 300 lines of Python.

In my experience, every nontrivial machine learning project is eventually stitched together with bug-ridden and unmaintainable internal tools. These tools — often a patchwork of Jupyter Notebooks and Flask apps — are difficult to deploy, require reasoning about client-server architecture, and don’t integrate well with machine learning constructs like Tensorflow GPU sessions.

I saw this first at Carnegie Mellon, then at Berkeley, Google X, and finally while building autonomous robots at Zoox. These tools were often born as little Jupyter notebooks: the sensor calibration tool, the simulation comparison app, the LIDAR alignment app, the scenario replay tool, and so on.

As a tool grew in importance, project managers stepped in. Processes sprouted. Requirements flowered. These solo projects gestated into scripts, and matured into gangly maintenance nightmares.

The machine learning engineers’ ad-hoc app building flow.

When a tool became crucial, we **called in the tools team**. They wrote fluent Vue and React. They blinged their laptops with stickers about declarative frameworks. They had a _design process_:

The tools team’s clean-slate app building flow.

Which was awesome. But these tools all needed new features, like weekly. And the tools team was supporting ten other projects. They would say, “we’ll update your tool again in two months.”

So we were back to building our own tools, deploying Flask apps, writing HTML, CSS, and JavaScript, and trying to version control everything from notebooks to stylesheets. So my old Google X friend, Thiago Teixeira, and I began thinking about the following question: **What if we could make building tools as easy as writing Python scripts?**

We wanted machine learning engineers to be able to create beautiful apps without needing a tools team. These internal tools should arise as a natural byproduct of the ML workflow. Writing such tools should _feel_ like training a neural net or performing an ad-hoc analysis in Jupyter! At the same time, we wanted to preserve all of the flexibility of a powerful app framework. We wanted to create beautiful, performant tools that engineers could show off. Basically, we wanted this:

The Streamlit app building flow.

With an amazing beta community including engineers from Uber, Twitter, Stitch Fix, and Dropbox, we worked for a year to create [Streamlit](https://streamlit.io/), a [completely free and open source](https://github.com/streamlit/streamlit/) app framework for ML engineers. With each prototype, the core principles of Streamlit became simpler and purer. They are:

**#1: Embrace Python scripting.** Streamlit apps are really just scripts that run from top to bottom. There’s no hidden state. You can factor your code with function calls. If you know how to write Python scripts, you can write Streamlit apps. For example, this is how you write to the screen:

```
import streamlit as stst.write('Hello, world!')
```

Nice to meet you.

**#2: Treat widgets as variables.** There are _no callbacks in Streamlit_! Every interaction simply reruns the script from top to bottom. This approach leads to really clean code:

```
import streamlit as stx = st.slider('x')  
st.write(x, 'squared is', x \* x)
```

An interactive Streamlit app in three lines of code.

**#3: Reuse data and computation.** What if you download lots of data or perform complex computation? The key is to _safely reuse_ information across runs. Streamlit introduces a cache primitive that behaves like a persistent, immutable-by-default, data store that lets Streamlit apps safely and effortlessly reuse information. For example, this code **downloads data only once** from the [Udacity Self-driving car project](https://github.com/udacity/self-driving-car), yielding a simple, fast app:

Using st.cache to persist data across Streamlit runs. To run this code, please [follow these instructions](https://gist.github.com/treuille/c633dc8bc86efaa98eb8abe76478aa81#gistcomment-3041475).

The output of running the st.cache example above.

In short, Streamlit works like this:

1.  The entire script is run from scratch for each user interaction.
2.  Streamlit assigns each variable an up-to-date value given widget states.
3.  Caching allows Streamlit to skip redundant data fetches and computation.

Or in pictures:

User events trigger Streamlit to rerun the script from scratch. Only the cache persists across runs.

If this sounds intriguing, you can try it right now! Just run:

```
$ pip install --upgrade streamlit   
$ streamlit hello **You can now view your Streamlit app in your browser.** **Local URL:** [http://localhost:8501](http://localhost:8501)  
**Network URL:** [http://10.0.1.29:8501](http://10.0.1.29:8501)
```

This will automatically pop open a web browser pointing to your local Streamlit app. If not, just click the link.

To see more examples like this fractal animation, run **streamlit hello** from the command line.

  
  
from Hacker News https://ift.tt/31Mxjez