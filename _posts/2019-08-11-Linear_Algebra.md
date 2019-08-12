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
  >A basis is a list of vectors in V that is linearly independent and spans V.

  또 다르게 표현하면<br>

  >A basis is a list of vectors called V which satisfies
  > $$V = \lbrace x_{i} \| \sum_{i=1}^{n} a_{i}x_{i} = 0,a_{i}\in F \, x_{i} \in F^{n} \rbrace$$


  예시<br>
  $V = \lbrace(0,1),(0,1)\rbrace$은 R^2의 basis이다. 이런 형태의 basis를  *standard basis*라고 부른다.

### Properties of Basis

#### Basis는 한 vector에 대해서 오직 유일한 표현(linear combination)을 가진다.
  >증명
  >Suppose v can be spanned by two different sets ${a_{i}}$ and ${b_{i}}$<br>
  >Substracting two linear combinations of v<br>
  >$$(a_{1}-b_{1})x_{1}+(a_{2}-b_{2})x_{2}+(a_{3}-b_{3})x_{3}+...++(a_{n}-b_{n})x_{n} = 0$$
  >implies $(a_{i}-b_{i}) = 0$ for each i since $x_{i}'s$ are linearly independent.

  증명에서 linearly independent한 vector들의 linear combination값이 0이 되기 위해서는 $a_{i} = b_{i}$가 되어야 을 알 수 잇다.

#### Spanning list는 언제나 Basis를 포함하고 있다.
  >증명<br>
  >Suppose A=$\lbrace v_{1},...,v_{n} \rbrace$ is spanning list.</br>
  >We want to obtain basis by removing some vectors from spanning list.</br>
  >Remove redundant vectors by checking that it is spanned by spanning list<br>
  >i.e if v_{i} is in span(A\v_{i}}, then delete v_{1} from A.
  >This process can be done iteratively, and we can get Basis from original A.
