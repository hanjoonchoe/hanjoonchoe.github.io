---
title: "NAIVE BAYES CLASSIFIER"
date: 2019-08-19
categories: Machine Learning
tags:
  - statistics
  - bayesian
  - machine learning
  - classification
use_math: true
---

# BAYE'S RULE

> $p(c|f) = \frac{p(f|c)p(c)}{p(f)}$

만약 어떤 단서(feature)들이 주어졌을 때 그 단서들이 $c$를 추정할 확률은 얼마나 될까? 일단 확률을 추정하는 수식은 다음과 같다.

$p(c|f_{1},f_{2},...,f_{n})$, where $c$ and $f$ are "choice" and "feature" respectively.

그리고 이 수식은 baye's rule을 이용해 다음과 같이 표현할 수 있다.

> $p(c|f_{1},f_{2},...,f_{n}) = \frac{p(f_{1},f_{2},...,f_{n}|c)p(c)}{p(f_{1},f_{2},...,f_{n})} $


>$p(c,f_{1},f_{2},...,f_{n}) = p(f_{1},f_{2},...,f_{n}|c)p(c)$<br>
$\ = p(f_{2},f_{3},...,f_{n}|f_{1},c)p(f_{1}|c)p(c)$<br>
$\ = p(f_{3},f_{4},...,f_{n}|f_{1},f_{2},c)p(f_{1},f_{2}|c)p(c)$<br>
$\ = p(f_{4},f_{5},...,f_{n}|f_{1},f_{2},f_{3},c)p(f_{3}|f_{1},f_{2},c)p(f_{2}|f_{1},c)p(f_{1}|c)p(c)$<br>
$\ \cdots$<br>
$\ = p(f_{1}|f_{2},f_{3},...,f_{n},c)p(f$
