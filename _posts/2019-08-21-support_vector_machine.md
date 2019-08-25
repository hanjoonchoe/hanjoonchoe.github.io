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

Thompson sampling을 설명할 때 보통 probability update과정을 beta-binomial distribution로 설명하기가 쉬우므로 많이 쓴다.

먼저 beta distribution의 probability density function은 다음과 같다.

> $$p(\theta,\alpha,\beta) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)}\theta^{\alpha -1}(\theta-1)^{\beta -1}$$
> <p align="center"> <img src="/_posts/images/beta_distribution.png" width="50%" height="50%"> <br> 그림 1. Beta distribution</p>

예시 그림에서와 같이 $\alpha$값이 상대적으로 높을수록 positive skew된, $\beta$값이 상대적으로 높을수록 negative skew된 것을 볼 수 있다.<br>
그리고 $\alpha$와 $\beta$값일 높을 수록 좌우가 좁고 peak이 높은 형태를 나타내는 것도 확인 할 수 있다.

## Gamma function

Beta distribution의 gamma function은 다음과 같은 형태를 가지고 있다.
> $$ \Gamma(\alpha) =  \int_{0}^{\infty} t^{\alpha - 1} e^{-t} dt $$

Ingetration by parts를 적용하여 풀어주면,
> $ \int_{0}^{\infty} t^{\alpha - 1} e^{-t} dt $<br>

$\left (x-1)t^{\alpha - 2}e^{-t} \right \bigg|^{t=0}^ {\infty}$
