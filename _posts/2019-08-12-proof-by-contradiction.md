---
title: "MATHEMATICAL_PROOF"
date: 2019-08-12
categories: Mathematical_Proof
tags:
  - Linear_Algebra
  - Basis
use_math: true
---

Proof by contradiction

Proof by contradiction은 조건을 부정한 뒤 나온 결과가 결과 모순관계임을 보여 이 참임을 증명하는 방법이다.<br>

필자는 처음 본 증명방법을 접했을 때 직관적으로 이해하기 어려웠으나 조건논리에 대해 조금만 알면 이 방법이 어떻게 쓰이는지 통찰을 할 수 있다.<br>

우선 if p, then q (또는 $p \rightarrow  q$)라는 조건문의 Truth table을 그려보자.<br>
| Column 1       | Column 2     | Column 3     |
| :------------- | :----------: | -----------: |
|  Cell Contents | More Stuff   | And Again    |
| You Can Also   | Put Pipes In | Like this \| |

여기서 확인할 수 있는 것은 p $\rightarrow$ q에서 거짓이 되는 조건은 p가 참이고 q가 거짓일 때 뿐이다.<br>

그말은 다르게 표현해 q가 거짓이면 무조건 p는 참이어야만 조건문의 관계가 참이라는 말과 같다.<br>

proof by contradiction에서는 조건의 부정이 참임을 가정하고 결과가 모순임을 보여<br>
$$\neg p \rightarrow q(c \land \neg c)$$
가 거짓 따라서 $p$가 참임을 보여주는 테크닉이라고 할 수 있다.<br>
(여기서 $c$는 원래 나와야하는 결과 $\neg c$는 조건을 부정하여 나온 결과이고 $c$와 $\neg c$는 서로 모순관계이므로 양립할 수 없어 거짓이다.)<br>

$\neg p \rightarrow q(c \land \neg c)$ 에서 $(c \land ~c)$가 거짓이므로 $\neg p가 거짓이어야 한다. 따라서, $\neg (\neg p) = p$는 참이다.
