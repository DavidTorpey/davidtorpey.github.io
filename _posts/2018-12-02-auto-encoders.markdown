---
layout: post
title:  "Autoencoders"
date:   2018-12-02 21:55:55 +0200
math: true
mathjax: true
---

Autoencoders fall under the unsupervised learning category, and are a special case of neural networks that map the inputs (in the input layer) back to the inputs (in the final layer). This can be seen mathematically as $$ f : \mathbb{R}^m \mapsto \mathbb{R}^m $$. Autoencoders were originally introduced to address dimensionality reduction. In the original paper, Hinton compares it with PCA, another dimensionality reduction algorithm. He showed that autoencoders outperform PCA when non-linear mappings are needed to represent the data. They are able to learn a more realistic low-dimensional manifold than linear methods due to their non-linear nature.

Okay, enough with the introduction; let's get into it. Autoencoders can be thought of as having two networks in one grand network. We refer to the first network as the encoder network. This takes in the actual data as the input and runs to the network to the output, similar to a vanilla neural network. The second network is the decoder network. This takes the output of the encoder as inputs to the network and uses the original input data as targets.
  
Usually, when we speak about autoencoders, we refer to the under-complete structure. This means that the "code" layer has less neurons than the input layer. The "code" layer, also sometimes referred to as the "latent variables", is the layer we described above. That is, the output layer of the encoder and the input layer of the decoder. Now, using a under-complete structure starts to make sense since we are essentially decreasing the dimensionality of our data. As research continued over the past few years, people have become much more interested in what the network learns in the code layer and a lot of research has gone into investigating this.

Generally the decoder is a reflection of the encoder along the code layer. However, in encoder-decoder models we can have various combinations in that we can add LSTM cells in the encoder and not in the decoder or vice-versa.

Since math makes everything easier, let's represent the above mathematically as follows: $$ f : \mathbb{R}^m \rightarrow \mathbb{R}^n $$ and $$ g : \mathbb{R}^n \rightarrow \mathbb{R}^m $$, where $$f$$ is the encoder and $$ g $$ is the decoder. If we are considering an under-complete structure then $$ m > n $$.

Autoencoders seek to describe the low-dimensional smooth structure of our high dimensional data, otherwise referred to as high-dimensional surfaces.

There are many variations of autoencoders that have been developed over the past few years, these include: over-complete autoencoders, de-noising autoencoders, variational auroencoders, etc. The basic idea for all these models are the same as the normal autoencoder.

Applications of these models can vary from dimensionality reduction to information retrieval. 

Some great resources can be found at:

[Autoencoders - tutorial](http://ufldl.stanford.edu/tutorial/unsupervised/Autoencoders/)

[Understanding Autoencoders](https://becominghuman.ai/understanding-autoencoders-unsupervised-learning-technique-82fb3fbaec2)
