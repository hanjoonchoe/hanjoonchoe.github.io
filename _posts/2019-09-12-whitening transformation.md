---
title: "WHITENING TRANSFORMATION"
date: 2019-09-12
categories: Machine_Learning
tags:
  - machine learning
  - data science
  - classification
  - linear algebra
use_math: true
---

# Whitening Transformation

Whitening transformation은 Sphering transformation이라고도 부르며 어떤 covariance matrix를 identity matrix $I$로 바꿔주는 테크닉이다. 다르게 말하면 $cov(x_i,x_j) = 1$ with $i=j$ or $0$ with $i \neq j$로 variance가 1이고 다른 변수들 간의 covriance를 0(uncorrelated)으로 바꿔주는 방법이다.

먼저 feature matrix $X$를 다음과 같이 정의하자. 

$X \in \mathbb{R}^{n\times n} =  [x_1, x_2,...,x_n ]$, where $x_i \in \mathbb{R}^{n\times 1}$ 여기서 각각의 $x_i$는 n개의 샘플을 가진 하나의 feature vector이다.<br>
그리고 $\bar{X} = 1^T\cdot [\bar{x_1},\bar{x_2},...,\bar{x_n}]$ where $1^T \in \mathbb{R}^{n\times 1}$ with $1$ in the entries and $\bar{x_i}$ is the mean of $i$th column vector.<br>
따라서 $\bar{X} \in \mathbb{R}^{n\times n}$가 되고 각 column들은 feature vector들의 평균값들로 채워진다.

## Centering

$\tilde{X}$를 다음과 같이 정의한다. $\tilde{X}$ = $X - \bar{X}$ 각 column vector의 entry들에 mean값을 빼준 matrix의 형태가 되고 이를 centering이라고 부른다.<br>

그리고 다음과 같은 특징을 가진다.<br>
$\mathbb{E}[\tilde{X}]=0$<br>
왜냐하면 $\mathbb{E}[\tilde{X}] = \mathbb{E}[X - \bar{X}] = \mathbb{E}[X]-\mathbb{E}[\bar{X}] = \bar{X} - \bar{X} = 0$

$\tilde{X}$의 covariance matrix는 다음과 같다.<br>
$\mathrm{Cov}[\tilde{X}] = \mathbb{E}[\tilde{X}\tilde{X^T}]$<br>
왜냐하면 $\mathbb{E}[\tilde{X}\tilde{X^T}] = \mathbb{E}[(X - \bar{X})(X - \bar{X})^T] $<br>

## Eigenvalue Decomposition
$\mathrm{Cov}[\tilde{X}]$ matrix를 $\Sigma$라고 하자.

$\Sigma$는 음이 아닌 정수의 entry를 가진 정방대칭행렬이다. 그말인 즉, positive semi definite(PSD)이다.<br>

PSD행렬은 eigenvalue decomposition이 가능하고 $\Sigma = VDV^T$ 형태로 치환이 가능하다. 여기서 $V$는 각 column들의 norm $\rvert\rvert \cdot \rvert\rvert$이 1인 orthonormal vector이다. 그리고 $D$는 diagonal matrix로 각각의 orthonormal vector들의 magnitude의 정보를 담고 있다.<br>

## Orthogonal Transformation
$Y$를 다음과 같이 정의하자.<br>

$Y = V^{T}\tilde{X}$ <br>

이는 $\tilde{X}$를 orthonormal matrix에 의해 $Y$로 transformation하는 형태인데 다음과 같은 특징을 가진다.

$T : R^{n\times n} \rightarrow R^{n\times n}$ via $\tilde{X} \mapsto V^T\tilde{X}$<br>

여기서 $T$를 orthonormal transformation이라고 부르고 다음과 같은 특징을 가진다.<br>

$\rvert\rvert x \rvert\rvert = \rvert\rvert Tx \rvert\rvert$

왜냐하면 $\rvert\rvert Tx \rvert\rvert = <Tx,Tx> = <x,T^{\ast}Tx> = <x,x> = \rvert\rvert x \rvert\rvert$

Operator $T$의 역할을 하는게 orthonormal matrix $V^T$이고 $T^{\ast}$ 는 $T$의 transpose conjugate이므로 $V$이다. 따라서 $T^{\ast}T = V^TV = I$이다.<br>

정리하자면, $V^{T}$는 $\tilde{X}$의 거리 norm을 유지한 채 orthonormal basis에 따라서 좌표를 옮긴 형태의 $Y$로 만들어주는 것이 된다.<br>

다시 covariance matrix $\Sigma$로 돌아가서 eigenvalue decomposition을 통해 $\Sigma = VDV^T$형태로 변환된 것을 다시 $VDV^T = VD^{1/2}D^{1/2}V^T$ 형태로 변환 가능하다. diagonal matrix들 끼리의 matrix multiplication은 diagonal entry들끼리 pairwise multiplication이나 다름이 없으므로 가능..

$VD^{1/2}$만 쪼개서 보면 $V$는 아까 말했듯이 orthonormal matrix이고 $D^{1/2}$는 $V$의 orthonormal vector(column vector)들의 magnitude를 결정 짓는 scalar역할을 한다.

$Y = V^T\tilde{X}$에서 각각의 term에 $D^{1/2}$의 역행렬을 곱해주면 어떻게 될까? 여기서 우리는 $D$를 $\tilde{X}\tilde{X}^T$로 부터 추출 했다는 사실을 기억하자.

Eigenvalue decomposition의 의미를 되새길 필요가 있다.<br> 어떤 행렬이 eigenvalue decomposition이 가능하다는 것은 행렬의 성분을 orthonormal basis들로 쪼갤 수 있고 각 basis의 magnitude를 diagonal matrix에 담을 수 있다는 이야기가 된다. $\tilde{X}\tilde{X}^T$는 $X$ 성분의 제곱이므로 $D$의 entry maginitude가 두번 곱해진 형태라고 볼 수 있다. 따라서 $D^{1/2}$는 $X$라는 성분을 어떤 orthonormal basis로 표현했을 때 그 basis의 magnitude가 된다.

따라서, $V^TVD^{1/2} = V^TX = Y$ 그리고 $D^{-1/2}V^TVD^{1/2} = D^{-1/2}Y$<br>
$\Longleftrightarrow V^TVD^{-1/2}D^{1/2} = D^{-1/2}Y$<br>
$\Longleftrightarrow I = D^{-1/2}Y$
