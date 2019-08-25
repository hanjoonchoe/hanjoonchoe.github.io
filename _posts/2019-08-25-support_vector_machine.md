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
$ = \frac{1}{2}\vec{w}^{T}(\vec{x^+}-\vec{x^-}) = 1$<br><br>
아래쪽 hyperplane과 위쪽 hyperplane의 거리는 equidistance이므로 절반으로 나누면,<br><br>
$ = \frac{1}{2}\frac{\vec{w}^{T}}{\parallel w \parallel}(\vec{x^+}-\vec{x^-}) = \frac{1}{\parallel w \parallel}$, where $\frac{1}{\parallel w \parallel}$ is width(margin)

>여기서 임의로 hyperplane을 $\pm$ 얼마만큼 translation을 하는지는 별로 중요하지 않다. 왜냐하면 $\parallel w \parallel$를 조절해서 얼마든지 이 값을 변화시킬 수 있기 때문이다.

Linear SVM은 이 width를 최대화 하는 것이므로 $\parallel w \parallel$를 최소화 해야한다. 따라서 다음과 같은 optimization problem이 된다.

minimize $\parallel w \parallel$
