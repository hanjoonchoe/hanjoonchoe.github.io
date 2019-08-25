---
title: "THOMPSON SAMPLING"
date: 2019-08-24
categories: Machine_Learning
tags:
  - bernoulli
  - thompson sampling
  - machine learning
  - optimization
  - classification
  - bayesian
use_math: true
---

# THOMPSON SAMPLING

## Bayesian update for beta distribution

## Beta distribution

Thompson sampling을 설명할 때 보통 probability update과정을 beta-binomial distribution로 설명하기가 쉬우므로 많이 쓴다.

먼저 beta distribution의 probability density function은 다음과 같다.

> $$p(\theta,\alpha,\beta) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)}\theta^{\alpha -1}(\theta-1)^{\beta -1}$$
> <p align="center"> <img src="https://raw.githubusercontent.com/hanjoonchoe/hanjoonchoe.github.io/master/_posts/images/beta_distribution.png" width="30%" height="30%"> <br> 그림 1. Beta distribution</p>

예시 그림에서와 같이 $\alpha$값이 상대적으로 높을수록 positive skew된, $\beta$값이 상대적으로 높을수록 negative skew된 것을 볼 수 있다.<br>
그리고 $\alpha$와 $\beta$값일 높을 수록 좌우가 좁고 peak이 높은 형태를 나타내는 것도 확인 할 수 있다.

## Gamma function

Beta distribution의 gamma function은 다음과 같은 형태를 가지고 있다.
> $$ \Gamma(\alpha) =  \int_{0}^{\infty} t^{\alpha - 1} e^{-t} dt $$

Intgeration by parts를 적용하여 풀어주면,
> $ \int_{0}^{\infty} t^{\alpha - 1} e^{-t} dt $<br><br>
$=-t^{\alpha - 1}e^{-t} \bigg\rvert_{t=0}^{\infty} + \int_{0}^{\infty} (x-1)t^{\alpha -2}e^{-t} dt$<br><br>
$= 0 + \int_{0}^{\infty} (x-1)t^{\alpha -2}e^{-t} dt$<br><br>
$=(x-1)\Gamma(x-2)$<br>

이 방법을 연속적으로 취해주면 $ \Gamma (x) = (x-1)! $임을 알 수 있다.

## Beta-binomial distribution

위의 두 사실을 바탕으로 다음과 같은 등식이 성립한다.

> $${\frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)}\theta^{\alpha -1}(\theta-1)^{\beta -1} = \frac{(\alpha+\beta -1)!}{(\alpha-1)!(\beta-1)!}\theta^{\alpha-1}(\theta-1)^{\beta-1}}$$


다음으로 위의 사실이 어떻게 Binomial distribution과 연관되는지 알아보도록 하자.

### Binomial distribution with bayesian update

> $bin(n,k,\theta) = \binom{n}{k}\theta^{k}\theta^{n-k}$

Binomial distribution에서 posterior를 계산하는 방법은 다음과 같다.

> $$posterior \propto likelihood \ast prior$$<br><br>
$p(\theta \mid x) = \frac{p(x \mid \theta)p(\theta)}{p(x)}$<br><br>
$= \frac{\binom{n}{k}\theta^{k}(\theta-1)^{n-k}}{\int_{\theta}\binom{n}{k}\theta^{k}{(\theta-1)}^{n-k}d\theta}$<br><br>
$= \frac{\theta^{k}(\theta-1)^{n-k}}{\frac{\Gamma(x+1)\Gamma(x-k+1)}{\Gamma(x+2)}}$<br><br>
$= \frac{\Gamma(x+2)}{\Gamma(x+1)\Gamma(x-k+1)}\theta^{k}(\theta-1)^{n-k}$<br><br>
