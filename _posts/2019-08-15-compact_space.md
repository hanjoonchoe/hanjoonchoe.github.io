---
title: "TOPOLOGY"
date: 2019-08-12
categories: Topology
tags:
  - topology
  - compact space
  - compact
use_math: true
---

# COMPACT SPACE

Compact의 정의는 다음과 같다.

>Definition<br>
>A space X is said to be compact if every open covering $\mathcal(A)$ of X contains a finite subcollection that also covers.<br>

다시 말해서 어떤 공간 X를 감싸는 open set들의 모임(open covering)이 있다면 그 중 임의로 유한개의 open set들을 뽑아서 다시 X를 감쌀 수 있을 때(또는 망라할 수 있을때) X는 compact이다.

>Lemma<br>
>Let $Y$ be a subspace of $X$. Then $Y$ is compact if and only if every covering of $Y$ by sets open in $X$ contains a finite subcollection covering $Y$

>Proof<br>
> $(\Rightarrow)$ <br>
> If $Y$ is compact, then there must exist a finite subcollection $\mathcal{A}^{'}$ of open covering $Y$, which is defined by $\mathcal{A}^{'} = \lbrace A^{'}_{n}\rbrace$$_{\lbrace n \in N \rbrace}$, where $N$ is finite index set, and this set is equivalent to $\lbrace A_{n} \cap Y A_{n} \subseteq_{open} X \rbrace _\lbrace n \in N \rbrace $, where $\lbrace A_{n}\rbrace_\lbrace n \in N\rbrace$ is finite subcollection of $X$.
