---
layout: post
title:  "Dimensionality Reduction"
date:   2019-01-31 21:55:55 +0200
math: true
mathjax: true
---


In machine learning, we often work with very high-dimensional data. For example, we might be working in a genome prediction context, in which case our feature vectors would contains thousands of dimensions, or perhaps we're dealing in another context where the dimensions reach of hundreds of thousands or possibly millions. In such a context, one common way to get a handle on the data - to understand it better - is to visualise the data by reducing its dimensions. The can be done using conventional dimensionality reduction techniques such as PCA and LDA, or using manifold learning techniques such as t-SNE and LLE.

For the purposes of this post, let's assume the input features are $$ M $$-dimensional.

The most popular, and perhaps simplest, dimensionality reduction technique. In it, we assume that the relationships between the variables / features are linear. "Importance" in the PCA algorithm is defined by variance. This assumption that variance is the important factor often holds (but not always!). To get the so-called principal components of the data, we find the orthogonal directions of maximum variance. These are the components that maximize the variance of the data.

We obtain these principal components via finding the eigen decomposition of the covariance matrix of the input matrix - that is, its eigenvalues and eigenvectors. Since computing the covariance matrix is often prohibitive to compute for a large number of features, the eigenvalues and eigenvectors are often found by using the SVD algorithm which decomposes the input matrix down into three separate matrices, two of which are the eigenvalues and eigenvectors. In this way, we need to directly compute the covariance matrix. The data must be centered in order for this SVD trick to work.

The $$ N $$ principal components are then the $$ N $$ eigenvectors with largest associated absolute eigenvalues. These are linear combinations of the input features, where is each feature contributes different amounts to the principal component. If there are strong linear relationships between the input variables, relatively few principal components will capture the majority of the variance in the data. However, if not much of the variance is captured by relatively few components, this does not necessarily mean that there are no relationships or underlying structure in the data - the structure might be in the form of non-linear interactiions and relationships. This is the reason non-linear dimensionality reduction and manifold learning techniques exist.

Manifold learning allows us to estimate the hypothesised low-dimensional non-linear manifold (or set of manifolds) on which our high-dimensional data lies. Different manifold learning algorithms optimise for different criteria depending on what type of structure of the data they want to capture - local or global or a combination.
