---
layout: post
title:  "Human Action Recognition"
date:   2019-03-18 21:55:55 +0200
math: true
mathjax: true
tags: [cnn, deep learning, action recognition]
---

In this post we will discuss the problem of human action recognition - an application of video analysis / recognition. The task is simply to identify a single action from a video. The typically setting is a dataset consisting of $$ N $$ action classes, where each class has a set of videos associated with it relating to that action. We will focus on the approaches typically taken in early action recognition research, and then focus on the current state-of-the-art approaches. There is a recurring theme in action recognition of extending conventional two-dimensional algorithms into three dimensions to accommodate for the extra (temporal) dimension when dealing with videos instead of images.

Early research tends to focus on hand-crafting features. The benefit of this is that you are incorporating domain knowledge into the features, which should increase performance. The high-level idea behind these approaches is as follows:

- Use interest point detection mechanism to localise points of interest to be used as the basis for feature extraction.
- Compute descriptions of these interest points in the form of (typically, gradient-based) descriptors.
- Quantise local descriptors into global video feature representations.
- Train an SVM of some form to learn to map from gloval video representation to action class.

Interest points are usually detected using a three-dimensional extension of the well-known Harris operator - space-time interest points (STIPs). However, in later research simple dense sampling was instead preferred for its resulting performance and speed. Interest points are also detected at multiple spatial and temporal scales to account for actions of differing speed and temporal extent. Descriptors are commonly computed within a local three-dimensional volume of the interest points (i.e. a cuboid). These descriptors are typically one of the following three (into some or other form): 1. histogram of oriented gradients; 2. histogram of optical flow; 3. motion boundary histograms.

The quantisation step to encode these local features into a global, fixed-length feature representation is usually done using either: 1. K-Means clustering using a bag-of-visual-words approach; or 2. Fisher vectors. Fisher vectors typically result in higher performance, but at a cost of dimensionality exploding. The normalisation applied to these features is important. The common approach was applying $$ L_2 $$ normalisation, however power normalisation is preferred more recently. An SVM then learns the mapping to action classes from the normalised versions of the representations. The most successful of these hand-crafted approaches is iDT (improved dense trajectories). iDTs are often used in tandem with deep networks in state-of-the-art approaches as they are able to encode some pertinent, salient information about the videos / actions that is difficult for the networks to capture.



