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
$$\mathbb{V}[X] = \mathbb{E}[(X-\bar{X})(X-\bar{X})^\top]\ = S$$ in the case when calculated by sample mean<br>
$$\mathbb{V}[X] = \mathbb{E}[(X-\mu)(X-\mu)^\top]\ = \Sigma$$<br>
$X_j = {x_1,...,x_n}$ 그리고 $X_j \in X$

따라서 , 분산은 $n \times n$의 Matrix로 표현되고 정방대칭 행렬이다. 왜냐하면 $(x_i-\mu)(x_j-\mu)^\top = (x_j-\mu)(x_i-\mu)^\top$ for all $i,j$
또 하나의 중요한 사실은 이 분산행렬은 Positive definite이다. 다르게 말하면 $\a\Sigma\a^\top \succ 0$ for all $a$

만약 매트릭스가 Positive definite이라면 다음과 같은 특성을 가진 것으로 알려져 있다. 1. Diagonalizable 2. Positive Eigenvalues.<br>
Diagonalizable이므로 eigenvalue decomposition이 가능하고 이 말은 $P^-1AP$ 꼴로 표현이 가능하다는 것을 말한다. 여기서 $P$는 orthogonal basis로 구성된 Matrix이다. Orthogonal Matrix의 특성은 $P^{-1}P = I = P^\topP$ 그리고 $A$는 Diagonal Matrix이며 각각의 entry는 P의 orthogonal basis의 scaling을 담당하는 역할을 한다. 다르게 말해서, $P$의 orthogonal basis들은 eigenvector 역할을 $A$의 diagonal entry들은 eigenvalue역할을 한다.
