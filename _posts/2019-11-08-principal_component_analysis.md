---
title: "PRINCIPAL COMPONENT ANALYSIS"
date: 2019-11-08
categories: Machine_Learning
tags:
  - machine learning
  - optimization
  - classification
use_math: true
---

## PCA(Principal Component Analysis)

PCA는 전통적인 unsupervised classification method이자 dimensional reduction technique 중 하나로 알려져 있다.<br>
PCA에서는 서로 intercorrelated되어 있는 feature axis를 다시 uncorrelated axis(Principal Components)로 바꿔 새롭게 표현한다.
그리고 더 나아가 이 PCs들 중 데이터 포인트의 분산이 가장 큰 몇개의 PCs를 추려서 dimensional reduction을 시도한다.<br>
본 포스팅에서는 PCA에 대한 수학적 기반 일부분에 대해  알아보겠습니다.<br>

먼저 $\mathbb{R}^n$ 에서 데이터 포인트가 분포한다고 가정하자. 그렇다면 이 데이터 포인트들 간의 분산은 다음과 같이 표현 되어질 수 있다.<br>
$$\mathbb{V}[X] = \mathbb{E}[(X-\bar{X})(X-\bar{X})^\top]\ = S$$ in the case when calculated by sample mean<br>
$$\mathbb{V}[X] = \mathbb{E}[(X-\mu)(X-\mu)^\top]\ = \Sigma$$<br>
$\textbf{x}_i = {x_1,...,x_n}$ 그리고 $\textbf{x}_i \in X$

따라서 , 분산은 $n \times n$의 Matrix로 표현되고 정방대칭 행렬이다. 왜냐하면 $(\textbf{x}_i-\mu)^\top (\textbf{x}_j-\mu) = (\textbf{x}_j-\mu)^\top (\textbf{x}_i-\mu)$ for all $i,j$
또 하나의 중요한 사실은 이 분산행렬은 positive definite이다. 다르게 말하면 $a\Sigma a^\top \succ 0$ for all $a$

만약 매트릭스가 positive definite이라면 다음과 같은 특성을 가진 것으로 알려져 있다. <br>
1. Diagonalizable<br><br>
2. Positive Eigenvalues.<br>

Diagonalizable이므로 eigenvalue decomposition이 가능하고 이 말은 $P^{-1}DP$ 꼴로 표현이 가능하다는 것을 말한다. 여기서 $P$는 orthogonal basis로 구성된 Matrix이다.<br>
Orthogonal matrix의 특성은 $P^{-1}P = I = P^{\top}P$ 그리고 $D$는 diagonal matrix이며 각각의 entry는 $P$의 orthogonal basis의 scaling을 담당하는 역할을 한다. 다르게 말해서, $P$의 orthogonal basis들은 eigenvector 역할을 $D$의 diagonal entry들은 eigenvalue역할을 한다. PCA에서 $D$에 있는 scaling scalar값이 최대가 되는 orthogonal basis를 찾는 것이 목표가 된다. 그리고 orthogonal basis는 orthonormal basis로 한정하기도 한다.<br> orthonormal basis는 앞서 말한 orthogonal basis와 같은 특성을 가지고 있으면서도 basis자체의 norm이 1인 경우이다. 여기서는 $P$가 orthonormal matrix임을 가정하겠다.<br>

우리가 해결해야할 objective function은 다음과 같은 표현이 될 것이다.<br>

$\underset{a_i}{\text{maximize}} \  a_{i}^{\top} \Sigma a_{i}$<br>
$\text{subject to} \  a_{i}^{\top} a_{i} = 1 $

여기서  $a_{i}$는 $\Sigma$ 를 eigenvalue decomposition했을 때의 orthonormal basis이고 $\lambda_i$는 i번째 orthogonal basis의 eigenvalue이다.<br>

그렇다면 $\underset{a_i}{\text{maximize}} \ a_{i} \Sigma a_{i}^{\top} =  \ a_{i} P^{\top} D P a_{i}^\top = \  \lambda_{i}$<br>

결과적으로 D의 entry인 $\lambda_i$을 최대화하는 orthonormal basis를 찾는 것이라 할 수 있다.

이 objective function의 조건을 충족하는 orthonormal basis를 찾기위해서 Lagrangian form 으로 변환 다음과 같은 형태가 된다.

$a_i \Sigma a_i^\top - \lambda a_i^\top x_i - 1 = 0$

$\Sigma$가 positive definite이므로 $ a_i \Sigma a_i^\top$는 언제나 $\succ 0$이다. 따라서 convex인 것을 알 수 있다.<br>

$x_i$에 대해 편미분 해주고 critical point를 찾으면 그 지점에서  global optimal point을 찾을 수 있다.

$\nabla_{a_i} \Sigma a_i - \lambda(a_i^\top a_i - 1)$<br>

$\rightarrow 2 \Sigma a_i - \lambda a_i = 0 $

$\rightarrow \Sigma a_i = \lambda a_i$

$\rightarrow \Sigma = \lambda$

이 결과를 원래의 optimization problem에 대입하면

$\underset{a_i}{\text{maximize}} \  a_{i}^{\top} \lambda_i a_{i}$<br>
$\text{subject to} \  a_{i}^{\top} a_{i} = 1 $

$\underset{a_i}{\text{maximize}} \  \lambda_i$ <br>
$\text{subject to} \  a_{i}^{\top} a_{i} = 1 $

따라서 orthonormal vector $a_i$는 $\lambda_i$ 값을 최대화하는 eigenvector이다.
그리고 $\lambda_i$는 $\Sigma$를 eigenvalue decomposition하여 얻을 수 있는 eigenvalue 값들 중 최대값이 된다.

2번째로 높은 Principal component는 어떻게 찾을 수 있을까?

우선 첫번째로 찾은 PC에서 eigenvector $a_i$ 는 두번째로 찾은 eigenvector $a_j$와 orothogonal 해야한다. 
(i.e.  $a_i^\top a_j = 0$)

그렇다면 다음과 같은 optimization problem이 설정된다.

$\underset{a_j}{\text{maximize}} \  a_j^{\top} \Sigma a_j$<br>
$\text{subject to} \  a_j^{\top} a_j = 1 ,\  a_i^{\top} a_j = 0 $

Lagrangian form을 취해주면 $a_j^{\top} \Sigma a_j - \lambda_j(a_j^{\top} a_j - 1) - \gamma(a_i^{\top} a_j)$

$\nabla_{a_j} a_j^{\top} \Sigma a_j - \lambda_j(a_j^{\top} a_j - 1) - \gamma(a_j^{\top} a_i) $<br>
$\rightarrow \Sigma a_j - \lambda_j a_j - \gamma a_i = 0$<br>

Multiply by $a_i$

$\rightarrow a_i^\top  \Sigma a_j - \lambda_j a_i^\top a_j - \gamma a_i^\top a_i = 0$<br>
$\rightarrow \gamma = 0$<br>


다음과 같은 결과를 대입하면 

$\rightarrow \Sigma a_j - \lambda_j a_j = 0 $<br>

$\rightarrow \Sigma a_j = \lambda_j a_j$<br>

따라서 두번 째 PC는 $\lambda_i$ 다음으로 큰 eigenvalue $\lambda_j$를 가지는 orthonormal vector(eigenvector) $a_j$이다.

이런식으로 3번째는 제약조건을 하나 더 추가해서 구할 수 있고 4번째 PC도 마찬가지이다.

솔직히 수식을 많이 적긴 했지만 생각보다 간단하게 생각할 수 있다고 생각한다.

Covariance Matrix $\Sigma$가 존재하면 그냥 eigenvalue decomposition해서 D부분의 diagonal entry중에 가장 큰 값을 순서적으로 찾아서 이에 해당하는 orthonormal vector 를 P에서 찾으면 끝이 아닐까 한다.
