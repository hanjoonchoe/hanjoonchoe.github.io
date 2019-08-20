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

만약 다음과 같은 형태의 optimization problem이 주어졌다고 하자.
>$\underset{x}{\text{minimize}} \  f_0(x)$<br>
$\text{subject to} \ f_i(x) \leq 0 , i=1,...,m$<br>
$\qquad\qquad\  g_i(x) \leq 0 , i=1,...,p$<br><br>

그렇다면 lagrange dual problem은 다음과 같이 정의된다.
>$g(\lambda,\upsilon) = \inf\limits_{x \in \mathcal{D}}L(x,\lambda,\upsilon)= \inf\limits_{x \in \mathcal{D}}(f_{0}(x)+\sum_{i=1}^{m} \lambda_{i}f_{i}(x) + \sum_{i=1}^{p} \upsilon_{i}g_{i}(x) )$

여기서 $L(x,\lambda,\upsilon)$은 Lagrangian function으로 $L:\mathbb{R}^m \times \mathbb{R}^p \rightarrow \mathbb{R}$, $\text{dom} \ L = \lbrace x \mid \text{dom}\bigcap_{i=1}^m f_i(x) \wedge \text{dom}\bigcap_{i=1}^p g_i(x) \rbrace $
