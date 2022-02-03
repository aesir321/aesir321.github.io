---
layout: post
title:  "Dimensionality reduction"
date:   2022-02-03 08:35:49 +0100
categories: data-science machine-learning
---

Dimensionality reduction is a term that most people working in machine learning / data science will have heard of before and even probably used before.  It's definitely a technique I have used before, however, coming from an applied background, I haven't ever given it much additional thought except as a way to reduce the feature space whilst attempting to retain as much information as possible.  This can then be used to see which features are driving a problem, but also as a tool for data visualisation, when you want to try and understand how your data might be clustered and related to each other.  In this post I am going to explore a little deeper why techniques such as dimensionality reduction exist and how to apply them.

## What is high dimensional data?

When a dataset has a large number of features it can be said to be highly dimensional, where the number of features is equal to the number of dimensions.  It is extremely difficult to think in more than three dimensions as a person, as these are the typically the number of dimensions within which we experience our everyday lives.

## Why can high dimensional data be problematic?

There is an interesting phenomenon called the [Curse of Dimensionality](https://en.wikipedia.org/wiki/Curse_of_dimensionality) where 

>"The common theme of these problems is that when the dimensionality increases, the volume of the space increases so fast that the available data become sparse."

that is to say that there is a lot of room between datapoints in a high dimensional space i.e. most datapoints in a high dimensional space are very far apart from each other.  It follows in turn that, any new prediction made by a model in this space is also likely to produce a datapoint that is far apart from any datapoint given in the training dataset.  Logically we can also conclude that as the points are prone to being far apart, that the amount of extrapolation involved in predicting the new point is high which directly leads to a **high probability of overfitting**.

If this is hard to see, it is possible to think about it in terms of datapoints and purely overfitting from the models perspective.  If you have a low dimensional datset (one with a small number of features) and now restrict each feature so that it can only take fixed inputs say $f_1 \in \{1, 2, 3\}$ f or example.  Now think of each feature as contributing to a unique identifier for that particular datapoint. When the number of features is low there will also be a low number of possible combinations and therefore the model has a better chance of generalising well, as many datapoints will share the same or similar unique identifiers.  If you now introduce many more features and keep the number of datapoints the same, there is a much higher chance that each datapoint now really has a unique identifier.  If the model has sufficient capacity it can then easily learn or "locate" each datapoint in the feature space and will overfit this data.

Of course, this occurs because we increased the number of features without increasing the number of datapoints, probably to a point where our problem is not well-posed, that is, the number of features exceeds the number of datapoints.  So why not also increase the number of datapoints?  Problem solved.  Well, not really.  Assuming that we actually are in a position where we can easily get hold of more samples (which often isn't the case), it turns out that in order to increase the density of the samples in a given space, the number of required samples to achieve this grows exponentially with the number of dimensions, which quickly make such a problem intractable.

## Introducing dimensionality reduction (for the second time)

We therefore have techniques to handle such situations that fall into the category called dimensionality reduction.  There are two main approaches to dimensionality reduction, **Projection** and **Manifold Learning**.   Which one you use depends on your data.  It sounds great, by reducing the number of dimensions, you are able to reduce the chance of your model overfitting and as a by-product speed up the training time of your model.  Like most things in life, you don't get something for nothing.  Reducing the number of dimensions will cause a loss of information, but in most cases it is possible to reduce the amount of dimensions whilst retaining the majority of that information, but it is something to be aware of.


