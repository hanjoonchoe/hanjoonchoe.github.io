---
title: "THOMPSON SAMPLING"
date: 2019-08-24
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

# THOMPSON SAMPLING

## Bayesian update for beta distribution

## Beta distribution

Thompson sampling을 설명할 때 보통 probability update과정을 beta-multinomial distribution을 가지고 설명한다.

먼저 beta distribution의 probability density function은 다음과 같다.

> $$p(\theta} = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)}x^{\theta -1}(x-1)^{\theta -1}$$

