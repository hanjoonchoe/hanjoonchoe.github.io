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

Whitening transformation은 Sphering transformation이라고도 부르며 어떤 데이터를 transformation시켜 norm covariance matrix를 identity matrix $I$로 바꿔주는 테크닉이다. 다르게 말하면 $cov(x_i,x_j) = 1$ with $i=j$ or $0$ with $i \neq j$로 variance가 1이고 다른 변수들 간의 covriance를 0(uncorrelated)으로 바꿔주는 방법이다.

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
$\mathrm{Cov}[\tilde{X}]$ 를 $\Sigma$라고 하자.

$\Sigma$는 음이 아닌 정수의 entry를 가진 정방대칭행렬이다. 그말인 즉, positive semi definite(PSD)이다.<br>

PSD matrix는 eigenvalue decomposition이 가능하고 $\Sigma = VDV^T$ 형태로 치환이 가능하다. 여기서 $V$는 각 column들의 norm $\rvert\rvert \cdot \rvert\rvert$이 1인 orthonormal vector이다. 그리고 $D$는 diagonal matrix로 각각의 orthonormal vector들의 magnitude(양의 값)의 정보를 담고 있다.<br>

> PSD matrix가 eigenvalue decomposition이 가능함을 보이기 위해서는 우선 spectral theorem부터 설명해야 될 것 같아서 따로 포스팅...

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

## Whitening/Sphering

다시 covariance matrix $\Sigma$로 돌아가서 eigenvalue decomposition을 통해 $\Sigma = VDV^T$형태로 변환된 것을 다시 $VDV^T = VD^{1/2}D^{1/2}V^T$ 형태로 변환 가능하다. diagonal matrix들 끼리의 matrix multiplication은 diagonal entry들끼리 pairwise multiplication이나 다름이 없으므로 가능..

$VD^{1/2}$만 쪼개서 보면 $V$는 아까 말했듯이 orthonormal matrix이고 $D^{1/2}$는 $V$의 orthonormal vector(column vector)들의 magnitude를 결정 짓는 scalar역할을 한다.

$Y = V^T\tilde{X}$에서 각각의 term에 $D^{1/2}$의 역행렬을 곱해주면 어떻게 될까? 여기서 우리는 $D$를 $\tilde{X}\tilde{X}^T$로 부터 추출 했다는 사실을 기억하자.

Eigenvalue decomposition의 의미를 되새길 필요가 있다.<br> 어떤 행렬이 eigenvalue decomposition이 가능하다는 것은 행렬의 성분을 orthonormal basis들로 쪼갤 수 있고 각 basis의 magnitude를 diagonal matrix에 담을 수 있다는 이야기가 된다. $\tilde{X}\tilde{X}^T$는 $\tilde{X}$ 성분의 제곱이므로 $D$의 entry maginitude가 두번 곱해진 형태라고 볼 수 있다. 따라서 $D^{1/2}$는 $X$라는 성분을 어떤 orthonormal basis로 표현했을 때 그 basis의 magnitude가 된다.

따라서, $D^{-1/2} V^T X = D^{-1/2} Y$는 $V^T$를 통해 orthogonal transformation한 뒤에 orthonormla basis를 $D^{1/2}$가 가지고 있는 entry의 magnitude 나눠 준 형태가 된다.

$D^{-1/2} Y$를 $W$라고 하고 $\mathrm{Cov}[W]$가 어떻게 되는지 살펴보도록 하자.<br>
$\mathrm{Cov}[W]$<br>
$\Longleftrightarrow  \mathbb{E} [W W^T]$<br>
$\Longleftrightarrow  \mathbb{E}[D^{-1/2}Y Y^T D^{-1/2}]$<br>
$\Longleftrightarrow  D^{-1/2}\mathbb{E}[Y Y^T]D^{-1/2}$<br>
$\Longleftrightarrow  D^{-1/2}\mathbb{E}[V^T\tilde{X} \tilde{X}^T V]D^{-1/2}$<br>
$\Longleftrightarrow  D^{-1/2}V^T \mathbb{E}[\tilde{X} \tilde{X}^T]VD^{-1/2}$<br>
$\Longleftrightarrow  D^{-1/2} V^T \Sigma V D^{-1/2}$<br>
$\Longleftrightarrow  D^{-1/2} V^T V D V^T V D^{-1/2}$<br>
$\Longleftrightarrow  D^{-1/2}  D  D^{-1/2}$<br>
$\Longleftrightarrow  D^{-1/2}  D^{1/2}D^{1/2}  D^{-1/2}$<br>
$\Longleftrightarrow  I$<br>

따라서 $\mathrm{Cov}[W] = I$

정리해서 centering matrix $\tilde{X}$에  $D^{-1/2}V^T$를 곱해 $W= D^{-1/2}V^T\tilde{X}$를 만들어 주면 norm은 유지하면서 covariance matrix가 $I$인 데이터로 변환이 가능하다. <br><br>
reference: https://www.projectrhea.org/rhea/images/1/15/Slecture_ECE662_Whitening_and_Coloring_Transforms_S14_MH.pdf
