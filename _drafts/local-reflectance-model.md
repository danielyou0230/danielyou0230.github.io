---
layout: post
title: "Computer Graphics: Understanding Local Reflectance Model"
comments: True
categories: "dig-deep"
---

Illumination and reflectance over objects makes image looks real, since light-material interaction in real world caused each point of the object have different colors and shades.This post is written to discuss some factors about illumination and reflectance models(global, local, etc.), and explore how computer graphic deals with illumination and reflectance of objects.

<!--More-->

### Illumination

* Importance
  * Visual Realism with surface appearance
  * Provides 3D cues

* Differences between illumination and Shading
  * illumination: calculates intensity at a point on a surface
  * shading: uses these calculated intensities to shade the whole surface or the whole scene

* Assumptions at this stage
  * Local illumination
    * Every point is shaded independently, as if no other objects exist in the scene. Hence:
    * No iterreflections + No shadows
    * Ignore frequency composition and care about its component-wise intensity (energy) - R, G, B
  * One Single Point Light
