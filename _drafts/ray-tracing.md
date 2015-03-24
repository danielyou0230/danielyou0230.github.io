---
layout: post
title: "Graphics: Ray Tracing"
comments: True
date: 2015-03-24
categories: "graphics"
---

Ray tracing is a procedure of object rendering, which differs from Rasterization-based rendering in the whole pipeline. It is pixel by pixel rather than primitive by primitive. And to reflect inter-reflection, a usual method is to allow recursion in this process, so as to get a realism image.

<!--more-->

### Overview
{: .text-center}

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

### A simple ray tracing algorithm
{: .text-center }

{% highlight c++ %}

Shape scene_definition(void){
  // define the primitive objects...
}

Image ray_tracing(int width, int height){
  Image image = new Image(width, height);

  for( int i = 0; i < width; i++){
    for( int j = 0; j < height; j++){
      // First shoot a single ray at a pixel
      Ray ray = camera.getCameraRay(i, j);

      // Find the intersection point between ray and the object
      hit = IntersectScene(ray);

      // Calculate specular reflectance, diffuse reflectance, ambient color,
      // and emmision color
      image[i][j] = getShadingColor(ray, hit);

    }
  }
  return image
}

int main(void){
  ...

  int im_wid = 400, im_height = 500;

  shapes = scene_definition();
  Image im = ray_tracing(im_wid, im_height);

  render_image(im);
  save_image(im);

  ...
}
{% endhighlight %}


* __Ray-shape Intersection__
  * Task: take ray, compute intersection and return hit structure
* Rays
  * __t value__
    * A distance along the ray
  * Any point along the ray with origin($x_S$, $y_S$, $z_S$) and direction ($x_d$, $y_d$, $z_d$) can be described using t
    * $x = x_s + t \cdot x_d$
    * $y = y_s + t \cdot y_d$
    * $z = z_s + t \cdot z_d$
