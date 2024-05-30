---
title: 'The Norm of Lebesgue Space'
date: 2024-05-20
permalink: /posts/2024/05/The Norm of Lebesgue Space/
tags:
---

In statistical learning, regulataztion methods such as lasso and ridge regression restrict the values that the parameters can take using the $\ell^1$ and $\ell^2$ norm, which are special cases of the more general $\ell^p$ norm. In this article, we will try to introduce more about **norm** and the norm of Lebesgue measurable functions.

Perhaps the norm gives us an impression of "length", but it does not seem to be that direct or obvious. Let us recall what characteristics are needed to describe the length of a vector in an $n$-dimensional Euclidean space. The first characteristic is that the value representing the length of a vector is always non-negative. Additionally, if a vector is scaled by $k$, its corresponding length will also be scaled by $k$. Furthermore, the length of a vector must satisfy the triangle inequality. These three [properties](https://en.wikipedia.org/wiki/Norm_(mathematics)) align with our intuition about the "length" in $n$-dimensional Euclidean space.

<!--
<blockquote>
<h3>The definition of norm</h3>

Let $X$ be a vector space, a norm on $X$ is any mapping $\parallel\cdot\parallel: X \rightarrow \mathbb{R}$ that satisfies the following properties: 

<ol>
<li> $\parallel x\parallel \geq 0$, for all $x \in X$ and $\parallel x\parallel=0$ if and only if $x=0$. </li>
<li> $\parallel k x\parallel = \parallel k\parallel \parallel x\parallel$, for all $x \in X$ and all scalars $k$. </li>
<li >$\parallel x + y\parallel \leq \parallel x\parallel + \parallel y\parallel $, for all $x, y \in X$. </li>
</ol>
</blockquote>
-->

Then for the mapping $\parallel \cdot \parallel_p$ of $x$ in a finite-dimensional space $X$ defined by $x \rightarrow \parallel x \parallel_p = (\sum\limits_{i=1}^n\lvert x_i \rvert^p)^{1/p}$ $(1 \leq p \leq \infty)$
is a norm on $X$. In the proof of the aforementioned three properties, the triangle inequality is the only nontrivial one, which can be done by the *Minkowski inequality for sequences*.


Then we extend norms to vector spaces consisting of infinite sequences. Let $\ell^p$ denote the set of all infinite sequence $x_{i=1}^{\infty}$ that satisfiy $\sum\limits_{i=1}^{\infty}\lvert x_i\rvert^p < \infty$, then the mapping $\parallel \cdot \parallel_p$ defined by 
{% raw %}
$$x=(x_i)_{i=1}^{\infty} \in \ell^{p} \rightarrow \parallel x \parallel_p = (\sum\limits_{i=1}^{\infty}\lvert x_i \rvert^p)^{1/p} \text{ , if } 1 \leq p < \infty.$$
{% endraw %}
{% raw %}
$$x=(x_i)_{i=1}^{\infty} \in \ell^{\infty} \rightarrow \parallel x \parallel_{\infty} = \sup\limits_{i \geq 1}\lvert x_i \rvert \text{ , if }  p = \infty.$$
{% endraw %}
is a norm on $\ell^p$.

With the above foundation, we now attempt to reasonably define the length of a function. Let $\Omega$ be an open (thus measurable) subset of $\mathbb{R}^n$. The corresponding space $L^1(\Omega)$ thus consist all real Lebesgue integrable functions, i.e., those measurable functions $f: \Omega \rightarrow (-\infty, \infty)$ that satisfy $\int_{\Omega} \lvert f(x) \rvert dx < \infty$.

We now extend this definition. Given any $1<p<\infty$ , we let $L^p(\Omega)$ denote the set formed by all measurable functions $f: \Omega \rightarrow (-\infty, \infty)$ such that $\lvert f \rvert^p \in L^1(\Omega)$, or equivalently, that  satisfy 
{% raw %}
$$\int_{\Omega} \lvert f(x) \rvert^p dx < \infty \quad \text{for some } 1 < p < \infty.$$ 
{% endraw %}
We now define the real normed vector space 
{% raw %}
$$(L^p(\Omega), \parallel \cdot\parallel_{L^p(\Omega)}), \quad 1\leq p \leq \infty,$$ 
{% endraw %}
which are called the Lebesgue spaces.
<blockquote> 
<h3>Theorem 1</h3>

Let $\Omega$ be an open subset of $\mathbb{R}^n$. For each extended real number $1\leq p \leq \infty$, let $L^p(\Omega)$ denote the set of all measurable functions $f: \Omega \rightarrow (-\infty, \infty)$ that satisfy 
{% raw %}
$$\int_{\Omega} \lvert f(x) \rvert^p dx < \infty \quad \text{if } 1\leq p < \infty,$$
{% endraw %}
{% raw %}
$$\inf\{C \geq 0; |f| \leq C \ \ a.e. \text{ in } \Omega\} < \infty \quad \text{if } p=\infty.$$
{% endraw %}
Then, for each $1\leq p \leq \infty$, the set $L^p(\Omega)$ is a vector space, and the mapping $\parallel\cdot\parallel_{L^p(\Omega)}$ defined by 
{% raw %}
$$f \in L^p(\Omega) \rightarrow \parallel f\parallel_{L^p(\Omega)} := (\int_{\Omega} \lvert f(x) \rvert^p dx)^{1/p} \quad \text{if } 1 \leq p < \infty,$$
{% endraw %}
{% raw %}
$$f \in L^{\infty}(\Omega) \rightarrow \parallel f\parallel_{L^{\infty}(\Omega)} := \inf\{C \geq 0; \lvert f \rvert \leq C \ \ a.e. \text{ in } \Omega\},$$
{% endraw %}
is norm on $L^p(\Omega)$.
</blockquote>

Similarly, the only nontrivial triangle property can be proofed by [Minkowski inequality](https://en.wikipedia.org/wiki/Minkowski_inequality).

Then, we can use the norm to describe length of the function in a vector space. And we can also use $\parallel f-g\parallel_{L^p}$ to define the distance between two functions $f$ and $g$. 

You may notice that there is some connection betweeen $\ell^2$ and $L^2$.  Indeed such a relationship exists. [Riesz (1907)](https://en.wikipedia.org/wiki/Riesz%E2%80%93Fischer_theorem#CITEREFFischer1907) proved that
 
<blockquote> 

<h3>Notes from Riesz and Fischer (1907)</h3>

Let $\{\varphi_n\}$ be an orthonormal system in $L^2[a,b]$ and $\{a_n\}$ a sequence of reals. The convergence of the series $\sum a_n^2$ is a necessary and sufficient condition for the existence of a function $f$ such that 
{% raw %}
$$\int_a^b f(x) \varphi_n(x) dx = a_n, \quad \text{for every } n.$$ 
{% endraw %}

</blockquote>
 
 A special case of this result is the Fourier series expansion in $L^2(0,2\pi;\mathbb{C})$.

More generally, there exists a Hilbert space isomorphism between any separable Hilbert space $X$ and the $\ell^2$ space. This means that there exists a linear bijective mapping between $X$ and $\ell^2$ that preserves the inner product, hence the Hilbert space structures of the two spaces are identical.

We will continue to discuss the above conclusion in subsequent articles. We need to know some results in functional analysis, such as the fact that the  $L^2$ is a Hilbert space (a complete inner product space); and maximal orthonormal families in an inner-product space, etc. 

<!--(Furthermore, once we have the definition of an inner product space, we can describe the angle between functions.)-->

<!--
Note that the theorem provide two other ways of defining each Lebesgue space $L^p(\Omega), 1\leq p \leq \infty$, either as the completion of the space $\mathcal{C}(\Omega)$ with the respect to the norm 
$\parallel \cdot \parallel_{L^p(\Omega)}$
or as the completion with respect to the norm $\parallel\cdot\parallel_{L^p(\Omega)}$ of the space formed by all measurable simple function 
$s: \Omega \rightarrow \mathbb{R}$ 
that satisfy $\int_{\Omega} \lvert s \rvert^p ds < \infty$. 
-->
