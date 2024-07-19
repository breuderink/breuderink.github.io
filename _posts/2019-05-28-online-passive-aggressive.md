---
layout: post
title:  Online passive-aggressive algorithms
categories: papers, embedded
---

One of my favorite papers is the paper on [online passive-aggressive
algorithms](http://www.jmlr.org/papers/volume7/crammer06a/crammer06a.pdf) by
Koby Crammer et al. In this paper, a set of algorithms is presented, that can be
used to learn classifiers and regressors with a simple, closed form update. The
underlying intuition is that when a prediction is good enough, the model is not
updated (i.e. it is passive). When the prediction is not good enough, the model
is aggressively updated not to make that mistake again. This is done after every
data point. Extensions are presented for multi-class predictions, one-class
prediction and structured prediction. 

What I like so much about the paper is that is is very clear about the objective
of the algorithm, and that the derivation of the update is straight forward to
follow. It results in a set of algorithms (with regret bounds!) that is very
easy to implement, even in low-level programming languages. A side effect of the
online update is no additional state needs to be tracked nor stored.

I have [used](https://github.com/breuderink/epsilon) passive-aggressive
regression (PA-I), for example for an online learning regressor on an embedded
system. The fact that the online update is numerically stable, and never
diverges makes it a very robust tool. Contrast that with gradient descent, where
we have to be careful with learning rates.

One can implicitly do a non-linear feature mapping in the passive aggressive
algorithms with the [kernel-trick](https://en.wikipedia.org/wiki/Kernel_method).
This transforms the passive aggressive models into non-linear model, not unlike
a support vector machine. [Wang and Vucetic
show](http://proceedings.mlr.press/v9/wang10b/wang10b.pdf) how to limit the
number of support vectors to a small budget, so that it still can be used in an
online fashion. This extension is also easy to implement in low-level languages,
such as C.