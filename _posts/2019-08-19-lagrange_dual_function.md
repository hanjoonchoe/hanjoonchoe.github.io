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

>$$g(\lambda, \upsilon) \leq L(\widetilde{x},\lambda,\upsilon) \leq f_{0}(x)$$
,where $\widetilde{x}$ is any feasible point in $\mathcal{D}$

## Dual problem
위의 부등식이 항상 성립하므로 $f_{0}(x)$의 lower bound는 $g(\lambda, \upsilon)$이다.<br>

이러한 사실은 그전의 optimization problem을 다음과 같은 형태로 치환할 수 있다.<br>

>$\underset{\lambda \geq 0}{\text{maximize}} \  g(\lambda, \upsilon)$<br>
$\text{subject to} \ \lambda_{i} \geq 0 , i=1,...,m$<br>

기존의 optimization problem으로 돌아가서
$g(\lambda, \upsilon)$는 affine function들의 pointwise infimum이므로 concave이다.<br>
그리고 이것은 $g(\lambda, \upsilon)$가 global optimal point $x^{\ast}$가 존재한다는 말과 동치이다.(concave이므로 optimal point는 maximum point이다.)

그렇다면 dual problem은 제약조건 안에서 $x^{\ast}$이 최대가 되는지 찾는 문제가 된다.<br>
다르게 말해서 $x^{\ast}$가 최대가 되는 지점은 $g(\lambda, \upsilon)$의 greatest upper bound이고, 이 지점은 $f_{0}$가 최소가 되는 point와 가장 근접할 것이다.

> $$\max g(\lambda, \upsilon) = d^{\ast} \leq p^{\ast} = \min f_{0}(x)$$

## Example

### Standard form LP

다음과 같은 standard form LP(linear programming)을 optimzation하는 문제가 주어졌다고 하자.
>$\underset{x}{\text{minimize}} \  c^{T}x$<br>
$\text{subject to} \ Ax = b$<br>
$\qquad\qquad\  x \succeq 0$<br><br>

이에 대한 lagrange dual function은

>$g(\lambda,\upsilon) = \inf\limits_{x \in \mathcal{D}}(c^{T}x+\lambda^{T}(Ax-b) + \upsilon^{T}x )$<br>
$\quad\quad\quad = \inf\limits_{x \in \mathcal{D}}((c^{T}+\lambda^{T}A+\upsilon^{T})x - \lambda^{T}b)$<br>
$\quad\quad\quad = \inf\limits_{x \in \mathcal{D}}((c^{T}+\lambda^{T}A+\upsilon^{T})x) - \lambda^{T}b$

다음과 같은 형태는 linear function의 pointwise infimum을 찾는 것이므로 concave이다.

concave function은 global optimal point가 존재하고 이 지점은 $\nabla_{x}g(\lambda,\upsilon) = 0$ 를 만족하는 $x$가 될 것이다.<br>
따라서
> $$\nabla_{x}g(\lambda,\upsilon) = \inf\limits_{x \in \mathcal{D}}(c^{T}+\lambda^{T}A+\upsilon^{T}) = 0$$
