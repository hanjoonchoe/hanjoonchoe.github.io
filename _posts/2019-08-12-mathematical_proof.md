---
title: "MATHEMATICAL_PROOF"
date: 2019-08-12
categories: Mathematical_Proof
tags:
  - Mathematical Proof
use_math: true
---

# PROOF BY CONTRADICTION

Proof by contradiction은 조건을 부정한 뒤 나온 결과가 결과 모순관계임을 보여 이 참임을 증명하는 방법이다.<br>

필자는 처음 본 증명방법을 접했을 때 직관적으로 이해하기 어려웠으나 조건논리에 대해 조금만 알면 이 방법이 어떻게 쓰이는지 통찰을 할 수 있다.<br>

우선 if p, then q (또는 $p \rightarrow  q$)라는 조건문의 Truth table을 그려보자.<br>

| $p$ 	| $q$ 	|  $p \rightarrow  q$ 	|
|---	|---	|---	|
|  T 	|  T 	|  T 	|
|  T 	|  F 	|  F 	|
|  F 	|  T 	|  T 	|
|  F 	|  F 	|  T 	|

여기서 확인할 수 있는 것은 $p \rightarrow q$에서 거짓이 되는 조건은 $p$가 참이고 $q$가 거짓일 때 뿐이다.<br>

그말은 다르게 표현해 $q$가 거짓이면 무조건 $p$는 참이어야만 조건문의 관계가 참이라는 말과 같다.<br>

proof by contradiction에서는 조건의 부정이 참임을 가정하고 결과가 모순임을 보여<br>
$$\neg p \rightarrow q(c \land \neg c)$$
가 거짓 따라서 $p$가 참임을 보여주는 테크닉이라고 할 수 있다.<br>
(여기서 $c$는 원래 나와야하는 결과 $\neg c$는 조건을 부정하여 나온 결과이고 $c$와 $\neg c$는 서로 모순관계이므로 양립할 수 없어 거짓이다.)<br>

$\neg p \rightarrow q(c \land \neg c)$ 에서 $(c \land ~c)$가 거짓이므로 $\neg p$가 거짓이어야 한다. 따라서, $\neg \neg p = p$는 참이다.

# PROOF BY INDUCTION

본 증명원리는 .

>Suppose $P(1)$ is, and $P(k+1)$ is true whenever $P(k)$ is true.

다시 말해서
Base case $n=1$일 때의 어떤 proposition이 참인 것을 확인하고 $n=k$일 때 참이라는 것을 가정 했을때 $n=k+1$이 참이라는 것을 확인하는 방법이다.

proof by induction은 well-ordering principle에 기반한다.

>Every non-empty set of positive integers(natural number) contains a least element.

>증명<br>
>Assume that there does not exist such a set called $A$. Since $A$ does not contains a smallest element, $B(= \mathbb{N} \setminus A)$ is a set containing element $k$ which is smaller than all elements in $A$, then $k+1$ is the smallest element in $A$. contradiction.

well-odering principle이 어떻게 위의 증명방법에 타당성을 주는지 확인하도록 하자.

>증명<br>
>Assume that $A$ be a non-empty set defined by $\lbrace k$ | $P(k)$ is false $\rbrace$. By well-ordering principle, $k'$ is the smallest element in A, That is, $P(k'-1)$ is true as $k'-1$ is not in $A$. But then $k'-1$ is smaller than $k'$ which contradicts well-ordering principle.

여기서 $k'$는 1이 될 수 없다. 왜냐하면 $P(1)$ is true 이기 떄문에 $A$에 속하지 않는다. 따라서, $k'>1$이다.<br>
증명에서 밝히고자 하는 핵심은 $n=k'$가 거짓일때 $k'-1$가 참인 케이스는 존재하지 않는다는 것이다. 다르게 말해서, $k'-1$가 참이면 $k'$도 참이다. (A를 충족시키는 set은 empty이다.)
