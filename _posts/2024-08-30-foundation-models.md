---
layout: post
title: Advantages of foundation models for algorithm development.
tags: [pretraining, foundation models, embeddings]
---

Yesterday, I presented the idea of using a foundation model for biosignals to a
client.  

With a foundation model, one trains large neural network on a large volume of
unlabeled data using a property of the data itself, for example by
reconstructing masked parts of the input. Since no labels are needed, a much
larger volume of data can be used to train the model. After training, one can
use the activations from the last layer to embed the input signals. This
embedding retains the important information, so that we can train a light-weight
model on the embeddings of dataset with labels for the task we care about.

This is not new, Apple [published work on a foundation
model](https://machinelearning.apple.com/research/large-scale-training) using
the signals from the Apple Watch.

It resulted in an interesting discussion,
mainly because the audience interpreted what a foundation model is, and what
it's advantages are in different ways.

In the presentation I emphasized advantages in centralization and scaling of
data, infrastructure, engineering, resulting in quicker feedback and more
accurate predictions on downstream tasks.

However, some in the audience was more interested in gains in inference
efficiency. A single foundation model can be used to extract an embedding for
many downstream tasks. On embedded systems, this can substantially decrease the
computational load if these downstream tasks are implemented efficiently. This
could be as simple as matrix multiplication.

Another advantage I didn't express well enough was data efficiency for the
downstream tasks. When a foundation model has learned to embed biosignals well,
a dataset for a downstream task can be much smaller, since only the relation
with the target label needs to be learned. When the data needs to be collected
and labeled, needing less data means saving a lot of costs and effort.

In summary, foundation models offer a powerful approach to leveraging large
volumes of unlabeled data to improve the accuracy and efficiency of downstream
tasks. If you're interested in exploring how foundation models can benefit your
organization, I'd be happy to discuss the possibilities with you and help you
get started.