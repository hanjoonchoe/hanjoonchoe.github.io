---
title: Highlight Test
categories:
 - Test
tags:
---


# COMPACT SPACE

Compact의 정의는 다음과 같다.

>Definition<br>
>A space X is said to be compact if every open covering $\mathcal{A}$ of $X$ contains a finite subcollection that also covers.<br>

다시 말해서 어떤 공간 $X$를 감싸는 open set들의 모임(open covering $\mathcal{A}$)이 있다면 그 중 임의로 유한개의 open set들을 뽑아서 다시 $X$를 감쌀 수 있을 때(또는 망라할 수 있을때) $X$는 compact이다.

>Lemma<br>
>Let $Y$ be a subspace of $X$. Then $Y$ is compact if and only if every covering of $Y$ by sets open in $X$ contains a finite subcollection covering $Y$.

>Proof<br>
> $(\iff)$ <br>
> If $Y$ is compact,then there must exist a finite subcollection $\mathcal{A}^{\prime}$ of open covering $Y$,defined by $\lbrace A^{\prime}_ {i} \rbrace_{i \in I}$ ,where $I$ is a finite index set, and this set is equivalent to $ \lbrace A^{\prime}_ {i} = A_{i} \cap Y \mid A_ {i} \subseteq_{open} X \rbrace_{i \in I}$, where $\lbrace A_{i}\rbrace_{i \in I}$ is a finite subcollection of $X$.<br>
This is a highlight test.

# Normal block

```
alert('Hello World!');
```

    print 'helloworld'

# Highlight block

```javascript
alert( 'Hello, world!' );
```

```python
print 'helloworld'
```

```ruby
def foo
  puts 'foo'
end
```

{% highlight ruby %}
def foo
  puts 'foo'
end
{% endhighlight %}

{% highlight ruby linenos %}
def foo
  puts 'foo'
end
{% endhighlight %}

```c++
#include <iostream>

using namespace std;

void foo(int arg1, int arg2)
{

}

int main()
{
  string str;
  foo(1, 2);
  cout << "Hello World" << endl;
  return 0;
}
```
