---
title: "THOMPSON SAMPLING"
date: 2019-08-25
categories: Machine_Learning
tags:
  - bernoulli
  - thompson sampling
  - machine learning
  - optimization
  - classification
  - bayesian
use_math: true
---


.. math::

  -{(y\log(p) + (1 - y)\log(1 - p))}

If :math:`M > 2` (i.e. multiclass classification), we calculate a separate loss for each class label per observation and sum the result.

.. math::

  -\sum_{c=1}^My_{o,c}\log(p_{o,c})
