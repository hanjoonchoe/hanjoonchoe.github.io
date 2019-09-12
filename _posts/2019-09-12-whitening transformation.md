---
title: "WHITENING TRANSFORMATION"
date: 2019-09-12
categories: Machine_Learning
tags:
  - machine learning
  - data science
  - classification
  - linear algebra
use_math: true
---

# Whitening Transformation

Whitening transformation은 Sphering transformation이라고도 부르며 어떤 covariance matrix를 identity matrix $I$로 바꿔주는 테크닉이다. 다르게 말하면 $cov(x_i,x_j) = 1$ with $i=j$ or $0$ with $i \neq j$로 variance가 1이고 다른 변수들 간의 covriance를 0(uncorrelated)으로 바꿔주는 방법이다.

먼저 feature matrix $X$를 다음과 같이 정의하자. 

$X \in \mathbb{R}^{n\times n} =  [x_1, x_2,...,x_n ]$, where $x_i \in \mathbb{R}^{n\times 1}$ 여기서 각각의 $x_i$ n개의 샘플을 가진 하나의 feature vector이다.  그리고 $\bar{X} = 1^T\cdot [\bar{x_1},\bar{x_2},...,\bar{x_n}]$ where $1^T \in \mathbb{R}^{n\times 1}$
