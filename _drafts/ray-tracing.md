---
layout: post
title: "Graphics: Ray Tracing"
comments: True
date: 2015-03-24
categories: "graphics"
---

Ray tracing is a procedure of object rendering, which differs from Rasterization-based rendering in the whole pipeline. It is pixel by pixel rather than primitive by primitive. And to reflect inter-reflection, a usual method is to allow recursion in this process, so as to get a realism image.

<!--more-->
### Overview {: .text-center}

* Basic Idea
  * trace the ray in a reverse order from the eye to the light source, and determine what color a pixel is from the tracing result.
  * It works because optical properties ramain the same under path reversal

* Advantages
  * Esay to handle complex illumination effects (reflections, refractions, soft shadows, indirect illumination)
  * Very flexible in handling various shapes
    * only need an intersection routine

* Disadvantages
  * Performance (due to weak object space coherence)
  * Typically needs preprocessing to build fast intersection structure
  * Difficult to handle dynamic scenes
*
