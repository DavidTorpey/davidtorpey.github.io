---
layout: post
title:  "Representation Learning (1)"
date:   2019-12-28 21:55:55 +0200
math: true
mathjax: true
tags: [representation learning, fisher vectors, deep learning]
---


For a while I've been interested in representation learning in the context of deep learning. Concepts such as self-supervised learning, unsupervised representation learning using GANs or VAEs, or simply through a vanilla supervised learning of some neural network architecture. Upon reading the literature, I had an idea that serves as a nice integration of two very interesting and useful models / techniques - the Fisher vector (which I've previously posted about in my blog [here](https://davidtorpey.com/2018/11/25/feature-quantisation.html)), and the variational autoencoder (which I've been meeting to write a blog post about!). This blog post just serves to flesh out the idea, should I choose to pursue or revisit it at some point.

The Fisher vector is a state-of-the-art patch encoding technique. It can be seen a soft / probabilistic version of VLAD (vector of locally-aggregated descriptors), which itself is very similar to the bag of visual words encoding / quantisation technique, except that you quantise the residuals of local descriptors to their cluster center, instead of the actual visual word occurrences. The Fisher vector is based on the Fisher kernel, and assumes that the generation process of the descriptors being encoded can be modelled by some parametric probability distribution $$ u_{\theta} $$, where $$ u $$ is the PDF and $$ \theta $$ are the associated parameters of this distribution. Typically, in the context of Fisher vectors, $$ u_{\theta} $$ is chosen to be a $$ K $$-mode GMM. Thus, $$ \theta = \{\alpha_i, \mu_i, \Sigma_i\}_{i=1}^{K} $$ are the $$ K $$ mixture weights, means, and covariances matrices of the GMM. EM can then be used to compute the maximum likelihood estimates of the parameters of the GMM. The Fisher vector is then defined to be the concatenation of the gradients of the log likelihood function of the GMM with respect to each of the parameters. What should be emphasised here is that the $$ u_{\theta} $$ can be **any**, and the estimation of its parameters can be done in any way we prescribe, not necessarily using MLE/EM.

