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

$$\lbrace \vec{x} \mid w^{T}x=b \rbrace$$
where $\vec{x} \in \mathbb{R}^{n}$ and $b \in \mathbb{R}$

다시말해서 위의 등식을 만족시키는 x의 집합이다.

예를들어 $\vec{x} \in \mathbb{R}^{2}$라면,<br><br>

$$\lbrace (x_{1},x_{2}) \mid ax_{1}+bx_{2}=b \rbrace$$를 만족하는 해집합 $(x_{1},x_{2})$은 $\mathbb{R}^{2}$에서 직선 형태를 띌 것이다.
(마찬가지로 $\mathbb{R}^{2}$라면 $x$의 해집합은 평면)

일반화 해서 $\vec{x} \in \mathbb{R}^{n}$에서 $\lbrace \vec{x} \mid w^{T}\vec{x}=b \rbrace$의 해집합은 $\vec{x} \in \mathbb{R}^{n-1}$이다.
