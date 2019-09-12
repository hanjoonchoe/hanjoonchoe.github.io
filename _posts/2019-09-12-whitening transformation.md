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

Whitening transformation은 Sphering transformation이라고도 부르며 어떤 covariance matrix를 identity matrix $I$로 바꿔주는 테크닉이다. 다르게 말하면 $cov(X_i,X_j) = 1$ with $i=j$ or $0$ with $i \neq j$로 variance가 1이고 다른 변수들 간의 covriance를 0(uncorrelated)으로 바꿔주는 방법이다.
