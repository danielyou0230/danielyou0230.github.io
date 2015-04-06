---
layout: post
title: "Graphics: Ray Tracing"
comments: True
date: 2015-03-24
categories: "graphics"
---

In this post, I targets to share my understanding towards ray tracing pipeline and will give an intuitive structure for ray tracing program design

<!--more-->

### Introduction

As wiki-pdia defines, [*Ray tracing*](https://en.wikipedia.org/wiki/Ray_tracing_(graphics)) is __a procedure of object rendering__, which differs from Rasterization-based rendering in the whole pipeline. It is pixel by pixel rather than primitive by primitive. And to reflect inter-reflection, a usual method is to allow recursion in this process, so as to get a realism image.

### Pipeline Overview

![alt pl](/images/posts/2015-04-06-ray-tracing-pipeline.png){:height="320px"}
{: .text-center }

In the above graph, different from other computer graphic rendering pipeline, ray tracing is a procedure that __mimics the imaging process in the real world__. It simulates the procedure of catching direct ray from light source, reflected ray from object surface, refracted ray through transparent object, etc, and thus achieves a superior realism effect.

In the following section, I will introduce the general ray tracing pipeline based on my personal practice, and will give a graph to help you with your [__ray tracer design__](#ray-tracer-design).

### Pipeline Details

#### Start from image plane and camera ray
{: .text-center}

![alt model](/images/posts/2015-04-06-ray-tracing-model.png){:height="320px"}
{: .text-center}

We first define a image plane at a particular space, consists of several pixels. The whole process goes in a __pixel by pixel__ manner. At each pixel, we produce a ray shot from the camera center towards a particular point in current pixel.

#### Find Ray-Scene intersection
{: .text-center}

#### Adding local illuminance effect at intersection point
{: .text-center}

#### Shadow test
{: .text-center}

#### Reflection Ray
{: .text-center}

#### Refraction Ray
{: .text-center}

#### Fine-graining scene through __shooting more ray__ at each pixel
{: .text-center}

### Accelerate the process

#### Direction 1: Fewer Ray
{: .text-center}

#### Direction 2: Faster Intersection
{: .text-center}

#### Direction 3: Generalized Ray
{: .text-center}


### A Sample Ray Tracing Program Structure
{: #ray-tracer-design}

#### __Program Structure__
{: .text-center}

![alt struct](/images/posts/2015-04-06-ray-trace-program.png){:height="512px"}
{: .text-center}

Above graph is a basic structure for a simple ray tracer. The __blue__ part represents the primitive classes and object classes that together form the ray trace scene. The __Red__ part gives the logic for tracing a single pixel's effective color in the scene. You would also need a simple image utility function to deal with image format, so as to store output image to disk.

#### __Output Result__
{: .text-center}

![alt scene](/images/posts/2015-04-06-traced-scene.png){:height="256px"}
{: .text-center}


Here is an _output image_ from my __ray tracer__.
{: .maxim .text-center}


### References

[1] [**SFU - CMPT 361 Introduction To Computer Graphics by Prof. Ping Tan**](http://www.cs.sfu.ca/~pingtan/)

[2] [**Ray Tracing Acceleration Techniques**](http://www.cs.virginia.edu/~gfx/Courses/2003/ImageSynthesis/scribed_notes/03_acceleration.pdf)

[3] [**Berkley X - Foundation of computer graphics**](https://courses.edx.org/courses/BerkeleyX/CS-184.1x/2013_October/info)
