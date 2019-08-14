---
title: "LINEAR ALGEBRA"
date: 2019-08-11
categories: Linear_Algebra
tags:
  - Linear_Algebra
use_math: true
---

# LINEAR ALGEBRA

## BASIS

### Definition of Basis

  >Definition<br>
  >A basis is a list of vectors in $V$ that is linearly independent and spans $V$.
  
  예시<br>
  $V = \lbrace(0,1),(0,1)\rbrace$은 $R^2$의 basis이다. 이런 형태의 basis를  *standard basis*라고 부른다.

### Properties of Basis

#### Basis는 한 vector에 대해서 오직 유일한 표현(unique linear combination)을 가진다.
  >**증명**<br>
  >Suppose $v$ can be spanned by two different sets ${a_{i}}$ and ${b_{i}}$<br>
  >Substracting two linear combinations of $v$<br>
  >$$(a_{1}-b_{1})x_{1}+(a_{2}-b_{2})x_{2}+(a_{3}-b_{3})x_{3}+...++(a_{n}-b_{n})x_{n} = 0$$
  >implies $(a_{i}-b_{i}) = 0$ for each i since $x_{i}'s$ are linearly independent.

  증명에서 linearly independent한 vector들의 linear combination값이 0이 되기 위해서는 $a_{i} = b_{i}$가 되어야 을 알 수 잇다.

#### Spanning list는 언제나 Basis를 포함하고 있다.
  >**증명**<br>
  >Suppose $A = \lbrace v_{1},...,v_{n} \rbrace$ is a spanning list<br>
  >We want to obtain basis by removing some vectors from spanning list<br>
  >Remove redundant vectors by checking that it is spanned by the other elements <br>
  >i.e If $v_{i}$ is **in** $span(A \backslash v_{i})$, then **delete** $v_{i}$ from $A$ <br>
  >This process can be done iteratively, and we can get a basis from original $A$.
  
  위의 증명을 통해 추가적으로 
  - finite-dimensional vector space는 basis를 반드시 포함
  - linearly independent list를 basis에 추가하여 새로이 basis를 만들 수 있다.
  
#### 만약 V가 finite-dimensional이고 $U$가 $V$의 subspace라면 $V = U \oplus W$가 되는 또다른 subspace $W$가 존재한다.
  여기서 $\oplus$ 기호는 direct sum으로  $ V= U + W$  그리고  $U \cap W = \emptyset$임을 나타낸다.
  
  >**증명**<br>
  >Step 1 Show that $V = U + W$<br>
  >Since V is finite-dimensional, U is also finite-dimensional and has a basis.<br>
  >This basis can be added to a basis of $V$, and it spans $V$.<br>
  >Step 2 Show that $U \cap W = \emptyset$<br>
  >Suppose there exists $v \in U \cap W$, then v can be spanned by basis of U and W respectively<br>
  >i.e $v = span(u_{1},..,u_{j})=span(w_{1},...,w_{k}) \iff a_{1}u_{1}+...+a_{j}w_{j}=b_{1}w_{1}+...+b_{k}w_{k}$<br>
  >$(a_{1}u_{1}+...a_{j}u_{j})-(w_{1}u_{1}+w_{k}u_{k})=0$ implies $a_{1}=...=a_{j}=b_{1}=...=b_{k}=0$<br>
  >because it is a linear combination of linearly independent vectors<br>
  >Hence $U \cap W = \emptyset$
  
## SHUR'S UNITARY TRIANGULARIZATION THEOREM

>정의<br>
>Given $A \in \mathcal{M}$ with eigenvalues $\lambda_{1},...,\lambda_{n}$, there exsits a unitary matrix $U \in \mathcal{M}$ such that $A = UTU^{\ast}$ where $T$ is upper-triangular matrix with the eigevalues in $T$.

여기서 Unitary matrix $U$는 $UU^{\ast} = I = U^{\ast} U$를 만족하는 matrix이다. 그리고, $A = UBU^{\ast}$의 형태를 unitary equivalent하다라고 부른다.

>증명<br>
>본 증명에서는 proof by induction을 사용할 것이다.<br>
>Base case n=1<br>
>trivially true<br>
>Assume that $n=k$ is true,that is, there exists $\widetilde{A} \in \mathcal{M}$ such that $\widetilde{A} = \widetilde{U}\widetilde{T}\widetilde{U}^{\ast}$ , where $\widetilde{U}$ is $k \times k$ unitary matrix and $\widetilde{T}$ is $k \times k$ upper trinagular matrix.<br>
>Let $A$ be $k+1 \times k+1$ matrix having eigenvalues $\lbrace \lambda_{1},...,\lambda_{k+1} \rbrace$.<br>
>Choose normalized eigenvector $v_{1}$,which is $\parallel v_{1} \parallel_{2} = 1$, corresponding to eigenvalue $\lambda_{1}$. We can construct an orthonormal basis of A(we can use gram-schmidt process)<br>


$$\begin{pmatrix}a & b\\\ \hline c & d\end{pmatrix}$$


$$\begin{array}{|c|c|}
  1 & 1/6 \\ \hline
  2 & 1/6 \\ \hline
  3 & 1/6 \\ \hline
  4 & 1/6 \\ \hline
  5 & 1/6 \\ \hline
  6 & 1/6 \\ \hline
\end{array}$$

$$\begin{pmatrix}{c|c}a & b\\\ c & d\end{pmatrix}$$

## ADJOINT

>정의<br>
>Suppose $T \in \mathcal{L}(V,W)$. The **adjoint** of $T$ is the function $T^{\ast} : W \rightarrow V$ such that
$$<Tv,w> = <v,T^{\ast}w>$$
for every $v \in V$ and $ w \in W$

### Adjoint는 linear map이다
아래의 두가지 조건이 충족 되었을 때 linear map이라 부른다.
 - $f(u+v) = f(u)+f(v)$
 - $f(\lambda u) = \lambda f(u)$
  
>증명<br>
>Suppose $T \in \mathcal{L}(V,W)$, Fix $w_{1},w_{2} \in W$. If $v \in V$, then<br>
$$<v,T^{\ast}(w_{1}+w_{2})>=<Tv,w_{1}+w_{2}>$$<br>
$$= <Tv,w_{1}>+<Tv,w_{2}>$$<br>
$$= <v,T^{\ast}w_{1}>+<Tv,T^{\ast}w_{2}>$$<br>
$$= <v,T^{\ast}w_{1}+T^{\ast}w_{2}>$$<br>
Hence, $T^{\ast}(w_{1}+w_{2}) = T^{\ast}w_{1}+T^{\ast}w_{2}.$<br><br>
Fix $w \in W$ and $\lambda \in F$ If $v \in V$,then<br>
$$<v,T^{\ast}({\lambda}w_{1})> = <Tv,{\lambda}w_{1}>$$<br>
$$ = \bar\lambda<Tv,w_{1}>$$<br>
$$ = \bar\lambda<v,T^{\ast}w_{1}>$$<br>
$$ = <v,{\lambda}T^{\ast}w_{1}>$$<br>
Hence, $T^{\ast}({\lambda}w_{1}) = {\lambda}T^{\ast}w_{1}$


## SELF-ADJOINT
>정의<br>
>An operator $T \in \mathcal{L}(V)$ is called **self-adjoint** if $T = T^{\ast}$. In other words,<br>
$T \in \mathcal{L}(V)$ is self-adjoint if and only if<br>
$$<Tv,w>=<v,Tw>$$<br>
for all $v,w \in V.$

여기서
Operator는 $T:V \rightarrow V$로 가는 linear map을 operator라고 부른다.<br>
이 정의를 통해 $T=T^{\ast}$일 때 self-adjoint임을 알 수 있다.

## NORMAL OPERATOR
>정의<br>
$T \in \mathcal{L}(V)$ is **normal** if<br>
$$TT^{\ast}=T^{\ast}T$$

다르게 말해서 operator $T$는 $T^{\ast}$와 교환법칙이 성립할 때 normal이라 부른다.

## THE SPECTRAL THEOREM

Spectral theorem이 시사하는 바는 어떤 Vector space $V$에 대하여 괜찮은 Operator가 존재한다면 orthonormal한 base들과 이에 대응하는 eigenvalue가 존재한다는 것이다. base들이 eigenvalue를 가지고 있다는 것은 이것이 eigenvector이기도 하는 말이다.

### Complex spectral theorem

본 항목에서는 $F$가 complex field일때 spectral theorem의 동치조건과 증명을 소개한다.

$F$가 complex field이고 $T \in \mathcal{L}(V)$ 일때, 다음 세가지가 동치이다.
>1. T is normal.
>2. V has an orthonormal basis consisting of eigenvectors of T.
>3. T has an diagonal matrix with respect to some orthonormal basis.

### Real spectral theorem

본 항목에서는 $F$가 real field일때 spectral theorem의 동치조건과 증명을 소개한다.

