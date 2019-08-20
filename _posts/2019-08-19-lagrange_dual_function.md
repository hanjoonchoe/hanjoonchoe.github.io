---
title: "LAGRANGE DUAL PROBLEM"
date: 2019-08-20
categories: Optimization
tags:
  - analysis
  - optimization
  - lagrangian
  - lagrange multiplier
  - duality
use_math: true
---

# LAGRANGE DUAL PROBLEM

만약 다음과 같은 형태의 optimization problem이 주어졌다고 하자.
>$\underset{x}{\text{minimize}} \  f_0(x)$<br>
$\text{subject to} \ f_i(x) \leq 0 , i=1,...,m$<br>
$\qquad\qquad\  g_i(x) = 0 , i=1,...,p$<br><br>

## Lagrange dual funtion
그렇다면 **lagrange dual function**은 다음과 같이 정의된다.

>$g(\lambda,\upsilon) = \inf\limits_{x \in \mathcal{D}}L(x,\lambda,\upsilon)= \inf\limits_{x \in \mathcal{D}}(f_{0}(x)+\sum_{i=1}^{m} \lambda_{i}f_{i}(x) + \sum_{i=1}^{p} \upsilon_{i}g_{i}(x) )$

여기서 $L(x,\lambda,\upsilon)$은 Lagrangian function으로<br> 
>$$L:\mathbb{R}^m \times \mathbb{R}^p \rightarrow \mathbb{R} \ \text{with} \ \mathcal{D} = \lbrace x \mid \bigcap_{i=1}^m \text{dom} \ f_i(x) \wedge \bigcap_{i=1}^p \text{dom} \ g_i(x) \rbrace $$
$$(x,\lambda,\upsilon) \mapsto f_{0}(x)+\sum_{i=1}^{m} \lambda_{i}f_{i}(x) + \sum_{i=1}^{p} \upsilon_{i}g_{i}(x)$$

그리고 각각의 constraint에 곱해지는 $\lambda_{i}$와 $\upsilon_{i}$는 "dual" 또는 "lagrange multiplier"라고 부른다.

만약 lagrange multiplier들이 0보다 큰 양수라면 constraint의 조건과 합쳐져 다음과 같은 부등식이 성립된다.

>$$g(\lambda, \upsilon) = \inf\limits_{x \in \mathcal{D}} L(x,\lambda,\upsilon) \leq L(\widetilde{x},\lambda,\upsilon) \leq f_{0}(x^{\ast})$$
,where $\widetilde{x}$ is any feasible point in $\mathcal{D}$

## Lower bound
위의 부등식이 항상 성립하므로 $f_{0}(x)$의 lower bound는 $g(\lambda, \upsilon)$가 최대일 때 이다.<br><br>
그렇다면 $g(\lambda, \upsilon)$가 최대인 지점은 어떻게 찾을 수 있을까?<br>

그 해답은 우선 다음과 같은 사실에서 출발한다.
$g(\lambda, \upsilon)$은 affine function들의 pointwise infimum이므로 concave이다.<br>
그리고 이 사실은 $g(\lambda, \upsilon)$가 global optimal point가 존재한다는 말과 동치이다.

이러한 사실은 다음과 같은 optimization problem으로 치환된다.<br>

>$\text{maximize} \  g(\lambda, \upsilon)$<br>
$\text{subject to} \ \lambda_{i} \geq 0 , i=1,...,m$<br>
