---
layout: post
title:  "Ensemble Learning"
date:   2018-12-10 21:55:55 +0200
math: true
mathjax: true
---

Ensemble learning is one of the most useful methods in the machine learning, not least for the fact that it is essentially agnostic to the statistical learning algorithm being used. Ensemble learning techniques are a set of algorithms that define how to combine multiple classifiers to make one strong classifier. There are various ensemble learning techniques, but this post will focus on the two most popular - bagging and boosting. These two approach the same problem in very different ways.

To explain these two algorithms, we assume a binary classification context, with a dataset consisting of a feature set $$ D $$ and a target set $$ Y $$, where $$ y \in \{-1, 1\} $$ $$ \forall y \in Y $$.

Bagging, otherwise known as bootstrap aggregation, depends on a sampling technique known as the boostrap. This is a resampling method where we sample, with replacement, over each step of the aggregation. Essentially we obtain bootstrapped samples from $$ X_t \subset D $$, and train a weak learner $$ h_t : X_t \mapsto Y $$, for $$ t = 1, \dots, M $$, where $$ M \in \mathbb{N} $$ is the number of so-called weak learners in the ensemble. Then, on a test example $$ x \in S $$, we make a prediction by taking the mode of the prediction of the $$ M $$ weak learners: $$ y_p = \text{mode}([h_1(x), h_2(x), \dots, h_M(x)]) $$. Random Forests, for example, employ bagging in their predictions. However, the bootstrapped samples used to train each of the weak learners (usually a decision stump - a decision tree of depth 1), consist of random samples of both the examples and the features. In this way, the decision trees in the random forest are made to be approximately de-correlated from each other, which gives the algorithm its effectiveness. The main reason for using bagging is to reduce the variance of an estimator. Such estimators are usually ones with a large VC-dimension or capacity, such as random forests.

Boosting is another very popular ensemble learning method. Unlike bagging, the current learner in the ensemble depends on the results of the previous learner in the ensemble. We will discuss the popular boosting algorithm known as Adaboost. Adaboost adaptively reweights samples such that the difficult-to-classify samples are given more weight as the emsemble progresses. A prediction scheme is then introduced to incorporate the predicitons of each learner in the ensemble.

