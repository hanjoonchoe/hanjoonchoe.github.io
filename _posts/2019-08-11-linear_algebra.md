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
  >Suppose v can be spanned by two different sets ${a_{i}}$ and ${b_{i}}$<br>
  >Substracting two linear combinations of v<br>
  >$$(a_{1}-b_{1})x_{1}+(a_{2}-b_{2})x_{2}+(a_{3}-b_{3})x_{3}+...++(a_{n}-b_{n})x_{n} = 0$$
  >implies $(a_{i}-b_{i}) = 0$ for each i since $x_{i}'s$ are linearly independent.

  증명에서 linearly independent한 vector들의 linear combination값이 0이 되기 위해서는 $a_{i} = b_{i}$가 되어야 을 알 수 잇다.

#### Spanning list는 언제나 Basis를 포함하고 있다.
  >**증명**<br>
  >Suppose $A = \lbrace v_{1},...,v_{n} \rbrace$ is a spanning list<br>
  >We want to obtain basis by removing some vectors from spanning list<br>
  >Remove redundant vectors by checking that it is spanned by the other elements <br>
  >i.e If $v_{i}$ is **not** in $span(A \backslash v_{i})$, then **delete** $v_{i}$ from $A$ <br>
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
  

## SELF-ADJOINT AND NORMAL OPERATOR

## Adjoint

>정의<br>
>Suppose $T \in \mathcal{L}(V,W)$. The **adjoint** of $T$ is the function $T^{\ast} : W \rightarrow V$ such that
$$<Tv,w> = <w,T^{\ast}w>$$
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
Hence $T^{\ast}(w_{1}+w_{2}) = T^{\ast}w_{1}+T^{\ast}w_{2}.$<br>
Fix $w \in W$ and $\lambda \in F$ If $v \in V$,then<br>
<br>
$$<v,T^{\ast}(\lambda w_{1})> = <Tv,\lambda w_{1}>$$<br>
$$\bar\lambda <Tv,w_{1}>$$<br>
$$\bar\lambda <v,T^{\ast}w_{1}>$$<br>
$$<v,\lambda T^{\ast}w_{1}>$$<br>
Hence $T^{\ast}(\lambda w_{1} = \lambda T^{\ast}w_{1}$

## Spectral theorem


