---
layout: post
title:  "Reducing the dimensionality of data with neural networks"
date:   2020-06-26 21:55:55 +0200
math: true
mathjax: true
tags: [deep learning, autoencoder, dimensionality reduction]
---

Reducing the dimensionality of data has many valuable potential uses. The low-dimensional version of the data can be used for visualisation, or for further processing in a modelling pipeline. The low-dimensional version should capture only the salient features of the data, and can indeed be seen as a form of compression. Many techniques for dimensionality reduction exists, including [PCA](https://www.tandfonline.com/doi/abs/10.1080/14786440109462720) (and its kernelized variant Kernel PCA), [Locally Linear Embedding](https://cs.nyu.edu/~roweis/lle/papers/lleintro.pdf), [ISOMAP](https://web.mit.edu/cocosci/Papers/sci_reprint.pdf), [UMAP](https://arxiv.org/pdf/1802.03426.pdf), [Linear Discriminant Analysis](https://www.ics.uci.edu/~welling/teaching/273ASpring09/Fisher-LDA.pdf), and [t-SNE](http://www.jmlr.org/papers/volume9/vandermaaten08a/vandermaaten08a.pdf). Some of these are linear methods, while others are non-linear methods. Many of the non-linear methods falls into a class of algorithms known as manifold learning algorithms.

The dimensionality reduction technique discussed in this paper is based on neural networks, and is known as the [autoencoder](https://www.cs.toronto.edu/~hinton/science.pdf). The autoencoder architecture consists of an encoder network and decoder network, with a latent code bottleneck layer in the middle (see below figure).
