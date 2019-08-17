---
title: "COMPACT SPACE"
date: 2019-08-15
categories: Topology
tags:
  - topology
  - compact space
  - compact
use_math: true
---

Compact의 정의는 다음과 같다.

>Definition<br>
>A space X is said to be compact if every open covering $\mathcal{A}$ of $X$ contains a finite subcollection that also covers.<br>

다시 말해서 어떤 공간 $X$를 감싸는 open set들의 모임(open covering $\mathcal{A}$)이 있다면 그 중 임의로 유한개의 open set들을 뽑아서 다시 $X$를 감쌀 수 있을 때(또는 망라할 수 있을때) $X$는 compact이다.

>Lemma<br>
>Let $Y$ be a subspace of $X$. Then $Y$ is compact if and only if every covering of $Y$ by sets open in $X$ contains a finite subcollection covering $Y$.

>Proof<br>
> $(\iff)$ <br>
> If $Y$ is compact,then there must exist a finite subcollection $\mathcal{A}^{\prime}$ of open covering $Y$,defined by $\lbrace A^{\prime}_ {i} \rbrace_{i \in I}$ ,where $I$ is a finite index set, and this set is equivalent to $ \lbrace A^{\prime}_ {i} = A_{i} \cap Y \mid A_ {i} \subseteq_{open} X \rbrace_{i \in I}$, where $\lbrace A_{i}\rbrace_{i \in I}$ is a finite subcollection of $X$.<br>

위의 결론으로부터 $\lbrace A^{\prime}_ {i} \rbrace_{i \in I}$가 유한하다면 $\lbrace A_ {i} \rbrace_{i \in I}$도 유한함을 알 수 있다. 따라서 $Y$는 compact이며 $X$는 $Y$를 감싸는 유한한 subcollection을 가지고 있다.

>Theorem<br>
>Every closed subspace of a compact space is compact.

>Proof<br>
Let $X$ be a topological space and $Y$ be a closed subspace of $X$,then there exists open covering $\mathcal{A}$ of $Y$ such that $\mathcal{A} \cup \lbrace X - Y \rbrace$ is open covering of $X$ which is compact. hence $\mathcal{A}$ is finite subcollection covering $Y$, and $Y$ is compact.

$\mathcal{A} \cup \lbrace X - Y \rbrace$는 compact인 $X$의 open covering이고 따라서 finite open covering일 수 있다. 여기서 open set인 $\lbrace X - Y \rbrace$를 제거 하더라도 supspace $Y$는 여전히 finite open covering $\mathcal{A}$로 감쌀 수 있으므로 compact이다.
