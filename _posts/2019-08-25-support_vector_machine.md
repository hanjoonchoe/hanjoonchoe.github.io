---
title: "SUPPORT VECTOR MACHINE"
date: 2019-08-24
categories: Machine_Learning
tags:
  - machine learning
  - optimization
  - classification
use_math: true
---

# SUPPORT VECTOR MACHINE

## Linear SVM(support vector machine)

### Hyperplane

hyperplane은 다음과 같이 정의된다

$$\lbrace \vec{x} \mid \vec{w}^{T}\vec{x}=b \rbrace$$
where $\vec{x} \in \mathbb{R}^{n}$ and $b \in \mathbb{R}$

다시말해서 위의 등식을 만족시키는 $\vec{x}$의 집합이다.

예를들어 $\vec{x} \in \mathbb{R}^{2}$라면,<br><br>

$$\lbrace (x_{1},x_{2}) \mid ax_{1}+bx_{2}=b \rbrace$$를 만족하는 해집합 $(x_{1},x_{2})$은 $\mathbb{R}^{2}$을 가르는 직선형태를 띌 것이다.
(마찬가지로 $\mathbb{R}^{3}$라면 $\vec{x}$의 해집합은 평면)

일반화 해서 $\vec{x} \in \mathbb{R}^{n}$에서 $\lbrace \vec{x} \mid \vec{w}^{T}\vec{x}=b \rbrace$의 해집합은 $\mathbb{R}^{n-1}$에서 span할 것이다.


<p align="center">
  <img src="https://raw.githubusercontent.com/hanjoonchoe/hanjoonchoe.github.io/master/_posts/images/hyperplane.png" width="30%" height="30%"><br>
그림 1. Hyperplane
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/hanjoonchoe/hanjoonchoe.github.io/master/_posts/images/linear_svm.png" width="30%" height="30%"><br>
그림 2. Linear SVM with margin
</p>
Linear SVM은 $\mathbb{R}^{n}$상에 분포된 data point들과 그것을 가르는 hyperplane 사이의 margin(거리)을 최대화 하는 $\vec{w}$를 optimization 기법이다.

### Find large margin under constraint

임의의 hyperplane $\vec{w}^{T}\vec{x^+}=b$이 존재한다고 하자. 그리고 이 hyperplane을 $\pm$ 1만큼 translation하면,<br>

$\vec{w}^{T}\vec{x^+}=b+1$<br><br>
$\vec{w}^{T}\vec{x^-}=b-1$ 이 된다.

두 등식의 차이는 hyperplane들 사이의 width(거리)가 된다.

$\vec{w}^{T}\vec{x^+} - \vec{w}^{T}\vec{x^-} =2$<br><br>

아래쪽 hyperplane과 위쪽 hyperplane의 거리는 equidistance이므로 절반으로 나누고 \vec{w}를 normalize하면,<br><br>
$ = \frac{1}{2}\frac{\vec{w}^{T}}{\parallel w \parallel}(\vec{x^+}-\vec{x^-}) = \frac{1}{\parallel w \parallel}$, where $\frac{1}{\parallel w \parallel}$ is width(margin)

>여기서 임의로 hyperplane을 $\pm$ 얼마만큼 translation을 하는지는 별로 중요하지 않다. 왜냐하면 $\parallel w \parallel$를 조절해서 얼마든지 이 값을 변화시킬 수 있기 때문이다.

Linear SVM은 이 width를 최대화 하는 것이므로 $\parallel w \parallel$를 최소화 해야한다. 따라서 다음과 같은 optimization problem이 된다.

$\underset{\vec{w},b}{\text{minimize}} \  \frac{1}{2}\parallel w \parallel^2$<br>
$\text{subject to} \  y_{i}(\vec{w}^{T}\vec{x}_ {i}+b) \geq 1 , i=1,...,n$<br>

여기에 추가로 constraint를 추가하여 $y_{i}(\vec{w}^{T}\vec{x}_ {i}+b) \geq 1$라는 조건을 동시에 충족하여야 한다.

$y_{i}$는 $\mathbb{R}^{n}$안의 data point가 $\vec{w}^{T}\vec{x}_ {i}+b = 1$ 기준으로 위쪽일 때 1의 값을 $\vec{w}^{T}\vec{x}_ {i}+b = -1$ 기준으로 아래쪽일 때 -1의 값을 가진다. 그리고 $\vec{w}^{T}\vec{x}_ {i}+b$는 -1이거나 1이다.<br>
따라서 $y_{i}(\vec{w}^{T}\vec{x}_ {i}+b) \geq 1$라는 조건은 data point들이 아랫쪽 hyperplane에 맞닿거나 그 아래 그렇지 않으면 위쪽 hyperplane에 맞닿거나 그 위에 위치해야 한다는 것을 의미한다.<br>
만약 아래쪽 hyperplane의 위쪽 그리고 위쪽 hyperplane의 아래쪽에 data point가 자리하고 있으면 부등식이 성립하지 않게된다.

>$\frac{1}{2}\parallel w \parallel^2$는 $\parallel w \parallel$를 최소화하는 문제를 좀 더 손쉽게 풀기 위해서 변형한 형태이며 이렇게 변형해도 최소의 $\parallel w \parallel$를 찾는데에는 아무런 영향이 없다. 다시말해 $\parallel w \parallel$를 최소화 하는 문제는 $\frac{1}{2}\parallel w \parallel^2$를 최소화 하는 문제와 같다.
