---
layout: post
title:  "Optical Flow"
date:   2018-12-23 16:23:55 +0200
math: true
mathjax: true
---

Optical flow is a method for motion analysis and image registration that aims to compute displacement of intensity patterns. Optical flow is used in many different settings in the computer vision realm, such as video recognition and video compression. The key assumption to many optical flow algorithms is known as the brightness constancy constraint, as is defined as:

$$ f(x, y, t) = f(x + dx, y + dy, t + dt) $$

This constraint simply states that the intensity of moving pixels remains constant during motion. If we take the MacLaurin series expansion of this equation, we obtain $$ f_x dx + f_y dy + f_t dt = 0 $$. Dividing by $$ d_t $$ yields:

$$ f_x u + f_y v + f_t = 0 $$

where $$ u = \frac{dx}{dt} $$, and $$ v = \frac{dy}{dt} $$. This equation is known as the optical flow (constraint) equation. Since we want to solve for $$ u $$ and $$ v $$, the system is underconstrained.

The first optical flow algorithm that will be discussed is perhaps the most well-known - Lucas Kanade, otherwise known as KLT. In order to perform optical flow, one first needs to detect some interest points (pixels) we want to track. In the case of the KLT tracker, these are usually a set of sparse interest points, such as Shi-Thomasi good features to track.

Since the system is underconstrainted, KLT considers local optical flow - a $$ 2k+1 \times 2k+1 $$ window. This yields a system of equations $$ A u = f_t $$. Using the pseudo-inverse of $$ A $$, we can obtain a solution: 

$$ u = (A^T A)^{-1} A^T f_t $$.