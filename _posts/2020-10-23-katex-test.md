---
layout: post
title: KaTeX test
date: 2020-10-23 14:46 +0100
---

{% include katex.html %}

{% katexmm %}

Gaussian integral: $$\int_{-\infty}^{\infty}e^{-x^2}dx=\sqrt{\pi}$$

j invariant: $$j(q)=\frac{1}{q}+744+196884q+\cdots$$

Binomial expansion:

$$\begin{aligned}
(x+y)^2 &= (x+y)(x+y) \\
&= x(x+y)+y(x+y) \\
&= x^2+xy+xy+y^2 \\
&= x^2+2xy+y^2
\end{aligned}$$

Let $p$ be a prime, then $2^{p-1}\equiv -1\mod p$.

Matrix:

$$
\left[\begin{matrix}
1 & 2 & 3 & 4 \\
0 & 1 & 2 & 3 \\
0 & 0 & 1 & 2 \\
0 & 0 & 0 & 1
\end{matrix}\right]
\cdot
\left[\begin{matrix}
1 \\ 2 \\ 3 \\ 4
\end{matrix}\right]
=
\left[\begin{matrix}
30 \\ 20 \\ 11 \\ 4
\end{matrix}\right]
$$

{% endkatexmm %}
