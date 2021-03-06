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

## Bayes Rule

> $p(c \mid \theta) = \frac{p(\theta \mid c)p(c)}{p(\theta)} \iff p(c , \theta) = p(\theta \mid c)p(c) $

만약 어떤 단서(feature)들이 주어졌을 때 그 단서들이 $c$를 추정할 확률은 얼마나 될까? 일단 확률을 추정하는 식은 다음과 같다.

>$p(c \mid \theta_{1},\theta_{2},...,\theta_{n})$, where $c$ and $\theta$ are "choice" and "feature" respectively.

그리고 이 식은 baye's rule을 이용해 다음과 같이 표현할 수 있다.

> $p(c \mid \theta_{1},\theta_{2},...,\theta_{n}) = \frac{p(\theta_{1},\theta_{2},...,\theta_{n},c)p(c)}{p(\theta_{1},\theta_{2},...,\theta_{n})} = \frac{p(\theta_{1},\theta_{2},...,\theta_{n},c)}{p(\theta_{1},\theta_{2},...,\theta_{n})} $

여기서 bayes rule의 특성을 이용해 대수적 조작을 해주면

>$p(c,\theta_{1},\theta_{2},...,\theta_{n}) =$<br><br>
$\ = p(\theta_{1},\theta_{2},...,\theta_{n} \mid c)p(c)$<br><br>
$\ = p(\theta_{2},\theta_{3},...,\theta_{n} \mid \theta_{1},c)p(\theta_{1} \mid c)p(c)$<br><br>
$\ = p(\theta_{3},\theta_{4},...,\theta_{n} \mid \theta_{1},\theta_{2},c)p(\theta_{2},\theta_{1} \mid c)p(c)$<br><br>
$\ = p(\theta_{4},\theta_{5},...,\theta_{n} \mid \theta_{3},\theta_{2},\theta_{1},c)p(\theta_{3}\mid \theta_{2},\theta_{1},c)p(\theta_{2} \mid \theta_{1},c)p(\theta_{1} \mid c)p(c)$<br><br>
$\ \ \ \ \ \ \ \vdots$<br><br>
$\ = p(\theta_{n} \mid \theta_{n-1},\theta_{n-2},...,\theta_{1},c)p(\theta_{n-1} \mid \theta_{n-2},\theta_{n-3},...,\theta_{1},c)...p(\theta_{3} \mid \theta_{2},\theta_{1},c)p(\theta_{2} \mid \theta_{1},c)p(\theta_{1} \mid c)p(c)$<br>

이에 더해 Naive bayes classfier에서는 각 feature들이 서로 연관성이 없다고 가정한다. 다시말해 다른 feature들이 조건으로 붙어도 또는 붙지 않아도 확률에는 영향을 미치지 않는다. 따라서 feature들이 상호 독립적(mutually independent)이라고 가정한다면 다음과 같이 표현가능하다.

>$\ = p(\theta_{n} \mid \theta_{n-1},\theta_{n-2},...,\theta_{1},c)p(\theta_{n-1} \mid \theta_{n-2},\theta_{n-3},...,\theta_{1},c)...p(\theta_{3} \mid \theta_{1},\theta_{2},c)p(\theta_{2} \mid \theta_{1},c)p(\theta_{1}\mid c)p(c)$<br><br>
$\ = p(\theta_{n} \mid c)p(\theta_{n-1} \mid c)...p(\theta_{3} \mid c)p(\theta_{2} \mid c)p(\theta_{1} \mid c)p(c)$<br><br>
$\ = p(c){\displaystyle \prod_{i=1}^{n}p(\theta_{i} \mid c)}$

## Gaussian Naive Bayes Classifier

확률이 gaussian distribution(정규분포)을 따르고 이에 대해 NB(naive bayes)방법으로 분류하는 것을 **gaussian naive bayes classifier**라고 부른다.

gaussian distribution은 좌우대칭의 종모양의 분포를 따르고 수식은 다음과 같다.

>$p(x \mid \mu,\sigma^2) = \frac{1}{\sigma \sqrt {2\pi}}e^\frac{-(x - \mu)^2}{2\sigma^2}, X \sim \mathcal{N}(\mu,\sigma^{2})$

방법은 단순한 편이다.<br>
Choice set $\mathcal{C} = \lbrace c_{1},c_{2},...,c_{k} \rbrace$가 있다고 한다면 각 $\theta_{i}$와 $c_{j}$ 대해 특정한 $\mu_{i,j}$ 와 $\sigma_{i,j}^2$를 가지는 정규분포를 따른다고 가정하고 각각의 확률을 정규분포 pdf(probability density function)로 치환해 주면된다.

>$p(c_{j},\theta_{1},\theta_{2},...,\theta_{n}) = {\displaystyle \prod_{i=1}^{n} \frac{1}{\sigma_{i,j} \sqrt {2\pi}}e^\frac{-(x - \mu_{i,j})^2}{2\sigma_{i,j}^2} }$, where $\mu_{i,j}$ and $\sigma_{i,j}^2$ are given by $c_{j}$

따라서 각 $c_{i}$에 대한 단서로 구성된 feature들의 정규분포상 확률들을 제각기 곱한 결과가 제일 큰 쪽으로 분류가 진행된다.

> $c^{\ast} = \text{arg}\max\limits_{c_{j} \in \mathcal{C}}\ p(c_{j}, \theta_{1},\theta_{2},...,\theta_{n}) $

혹시 포스팅을 진지하게 읽으신 분 중, 어째서 $ p(c \mid \theta_{1},\theta_{2},...,\theta_{n}) $대신 $p(c,\theta_{1},\theta_{2},...,\theta_{n})$로 계산했는지 의문점이 드시는 분을 위해 추가 설명을 하자면,

> $ p(c_{j} \mid \theta_{1},\theta_{2},...,\theta_{n}) = \frac{p(c_{j}, \theta_{1},\theta_{2},...,\theta_{n})}{p(\theta_{1},\theta_{2},...,\theta_{n})}$ , where $p(\theta_{1},\theta_{2},...,\theta_{n})$ is common term for all $c_{j} \in \mathcal{C}$

따라서, $p(c_{j}, \theta_{1},\theta_{2},...,\theta_{n})$만 계산해 주는 것으로 어떤 선택이 제일 확률이 큰지 확인할 수 있다.

