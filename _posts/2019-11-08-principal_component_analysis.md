---
title: "Principal Component Analysis"
date: 2019-08-25
categories: Machine_Learning
tags:
  - machine learning
  - optimization
  - classification
use_math: true
---

## PCA(Principal Component Analysis)

PCA는 전통적인 unsupervised classification method이자 dimensional reduction technique 중 하나로 알려져 있다.<br>
PCA에서는 서로 intercorrelated되어 있는 feature axis를 다시 uncorrelated axis(Principal Components)로 바꿔 새롭게 표현한다.
그리고 더 나아가 이 PCs들 중 데이터 포인트의 분산이 가장 큰 몇개의 PCs를 추려서 dimensional reduction을 시도한다.<br>
본 포스팅에서는 PCA의 수학적인 기반에 대해서 공부하고 써보겠습니다.<br>

먼저 $\mathbb{R}^n$ 에서 데이터 포인트가 분포한다고 가정하자. 그렇다면 이 데이터 포인트들 간의 분산은 다음과 같이 표현 되어질 수 있다.<br>
$$\mathbb{V}[X] = \mathbb{E}[(X-\bar{X})(X-\bar{X})^\top]\ = S$$<br> in the case when calculated by sample mean
$$\mathbb{V}[X] = \mathbb{E}[(X-\mu)(X-\mu)^\top]\ = \Sigma$$<br>
그리고, $S or \Sigma \in \mathbb{R}^{n\times n}$$

따라서 분산읜 $n \times n$의 Matrix로 표현될 수 있고, 이 Matrix는 정방대칭 행렬이다.
