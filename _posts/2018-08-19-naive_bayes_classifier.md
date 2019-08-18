---
title: "NAIVE BAYES CLASSIFIER"
date: 2019-08-19
categories: Machine_Learning
tags:
  - statistics
  - bayesian
  - machine learning
  - classification
use_math: true
---
# NAIVE BAYES CLASSIFIER

## Bayes rule

> $p(c \mid f) = \frac{p(f \mid c)p(c)}{p(f)}$

만약 어떤 단서(feature)들이 주어졌을 때 그 단서들이 $c$를 추정할 확률은 얼마나 될까? 일단 확률을 추정하는 수식은 다음과 같다.

>$p(c \mid f_{1},f_{2},...,f_{n})$, where $c$ and $f$ are "choice" and "feature" respectively.

그리고 이 수식은 baye's rule을 이용해 다음과 같이 표현할 수 있다.

> $p(c \mid f_{1},f_{2},...,f_{n}) = \frac{p(f_{1},f_{2},...,f_{n},c)p(c)}{p(f_{1},f_{2},...,f_{n})} = \frac{p(f_{1},f_{2},...,f_{n},c)}{p(f_{1},f_{2},...,f_{n})} $


>$p(c,f_{1},f_{2},...,f_{n}) =$<br><br>
$\ = p(f_{1},f_{2},...,f_{n} \mid c)p(c)$<br><br>
$\ = p(f_{2},f_{3},...,f_{n} \mid f_{1},c)p(f_{1} \mid c)p(c)$<br><br>
$\ = p(f_{3},f_{4},...,f_{n} \mid f_{1},f_{2},c)p(f_{2},f_{1} \mid c)p(c)$<br><br>
$\ = p(f_{4},f_{5},...,f_{n} \mid f_{3},f_{2},f_{1},c)p(f_{3}\mid f_{2},f_{1},c)p(f_{2} \mid f_{1},c)p(f_{1} \mid c)p(c)$<br><br>
$\ \ \ \ \ \ \ \vdots$<br><br>
$\ = p(f_{n} \mid f_{n-1},f_{n-2},...,f_{1},c)p(f_{n-1} \mid f_{n-2},f_{n-3},...,f_{1},c)...p(f_{3} \mid f_{2},f_{1},c)p(f_{2} \mid f_{1},c)p(f_{1} \mid c)p(c)$<br>

Naive bayes classfier에서는 각 feature들이 서로 연관성이 없다고 가정한다. 따라서 feature들이 상호 독립적(independent)이라고 가정한다면 다음과 같이 표현가능하다.

>$\ = p(f_{n} \mid f_{n-1},f_{n-2},...,f_{1},c)p(f_{n-1} \mid f_{n-2},f_{n-3},...,f_{1},c)...p(f_{3} \mid f_{1},f_{2},c)p(f_{2} \mid f_{1},c)p(f_{1}\mid c)p(c)$<br><br>
$\ = p(f_{n} \mid c)p(f_{n-1} \mid c)...p(f_{3} \mid c)p(f_{2} \mid c)p(f_{1} \mid c)p(c)$<br><br>
$\ = p(c){\displaystyle \prod_{i=1}^{n}p(f_{i} \mid c)}$

## Gaussian Naive Bayes Classifier

확률이 gaussian distribution(정규분포)을 따르고 이에 대해 NB(naive bayes)방법으로 분류하는 것을 **gaussian naive bayes classifier**라고 부른다.

gaussian distribution은 좌우대칭의 종모양의 분포를 따르고 수식은 다음과 같다.

>$p(x \mid \mu,\sigma^2) = \frac{1}{\sigma \sqrt {2\pi}}e^\frac{-(x - \mu)^2}{2\sigma^2}, X \sim \mathcal{N}(\mu,\sigma^{2})$
