---
layout: post
title: Reading - Image Matting
comments: True
---

This article is a summary for PAMI 2013 paper - A closed-form solution to natural image matting.

## Problem & Challenge

* Goal
    * To extracting a foreground object from an image based on limited user input

* Challenge
    * Extremely challenging because it is massively ill-posed -- at each pixel we must estimate the foreground and the background colors, as well as the foreground opacity from a single color measurement

* **Introduction**
    * Formally, image matting methods take as input an image I, which is assumed to be a composite of a foreground image F and a background image B. The color of the i-th pixel is assumed to be a linear combination of the corresponding foreground and background color
$$
\begin{align}
I_i = \alpha_i * F_i + (1 - \alpha_i) * B_i
\end{align}
$$


## Previous Solution

## Their Approach


## Reference
[**[1]**](http://www.wisdom.weizmann.ac.il/~levina/papers/Matting-Levin-Lischinski-Weiss-PAMI.pdf)  A Closed-Form Solution to Natural Image Matting, Anat Levin, Dani Lischinski, and Yair Weiss, MIT, 2013 PAMI
