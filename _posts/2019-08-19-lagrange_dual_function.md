---
title: "LAGRANGE_DUAL_FUNCTION"
date: 2019-08-15
categories: Optimization
tags:
  - analysis
  - optimization
  - lagrangian
  - lagrange multiplier
  - duality
use_math: true
---

# LAGRANGE DUAL FUNCTION

만약 아래와 같은 형태의 optimization problem이 있다면 Lagrange dual function은 다음과 같이 정의된다.
>$\underset{x}{\text{minimize}} \  f_0(x)$<br>
$\text{subject to} f_i(x) \leq 0$
>$g(\lambda,\upsilon) = \inf\limits_{x \in \mathcal{D}}L(x,\lambda,\upsilon)= \inf\limits_{x \in \mathcal{D}}(f_{0}(x)+\sum_{i=1}^{m} \lambda_{i}f_{i}(x) + \sum_{i=1}^{p} \upsilon_{i}g_{i}(x) )$
