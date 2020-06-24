---
layout: post
title:  "All About Convex Hulls"
date:   2020-06-24 21:55:55 +0200
math: true
mathjax: true
tags: [computational geometry, geometry, computer vision]
---

The convex hull is a very important concept in geometry, and has many applications in fields such as computer vision, mathematics, statistics, and economics. Essentially, a convex hull of a shape or set of points is the smallest convex set that contains that shape or set of points. Many algorithms exist to compute a convex hull. Many of these algorithms have focused on the 2D or 3D case, however, the general $$ d $$-dimensional case is of big interest in many applications.

It is important to first build up some background knowledge so that we can effectively talk about convex hulls. We will be working with the general $$ d $$-dimensional case, but will visualise in 2D. First, we have the concept of a $$ d $$-simplex, which is just a generalisation of the concept of a triangle to arbitrary dimensions (similar to what a cube is to a square or a hyperplane to a line). Additionally, a $$ d $$-dimensional convex hull is represented by its "faces", which are essentially $$ d - 1 $$-dimensional affine hyperplanes.
