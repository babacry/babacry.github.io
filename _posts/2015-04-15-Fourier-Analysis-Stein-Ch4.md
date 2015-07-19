---
title: Chapter4 Some Applications of Fourier Series 
layout: post
category : [books, Fourier Analysis by Stein]
tagline: "Supporting tagline"
tags : [Analysis, Fourier Analysis]
---
This chapter concerns 4 specfic problems:

+ Among all simple closed curves of length $$l$$ in the plane $$\mathbb{R}^2$$, which one encloses the largest area?
+ Given an irrational number $$\gamma$$, what can be said about the distribution of the fractional parts of the sequence of numbers $$n\gamma$$, for $$n = 1, 2, 3, . . .$$?
+ Does there exist a continuous function that is nowhere differentiable?
+ Time-dependent heat equation on the circle.  

### 1. The isoperimetric inequality  

+ $$\Gamma$$: closed curves, do not intersect itself. 
+ $$\mathcal{A}$$: area enclosed by $$\Gamma$$
+ $$l$$: length of $$\Gamma$$

Intuitively to increase $$\mathcal{A}$$:

+ if not convex, we can deform $$\Gamma$$ to increase $$\mathcal{A}$$ 
+ "flatter" the curve

#### Curves, length and area
+ A parametrized curve $$\gamma$$ is a mapping: $$\gamma: [a, b] \rightarrow \mathbb{R}^2$$, the image if $$\gamma$$ if a set of poiunts in the plane, which we call a **curve** and denoted by $$\Gamma$$  
+ **Simple**: if does not intersect itself.
+ **Closed**: if two end-points coincide.
+ If s: [c, d] -> [a, b] is $$C^1$$ bijective, then it gives rise to another parametrization of $$\Gamma$$: 
        \\[ \eta (t) = \gamma(s(t)) \\]
+ Closed and simple property are independent of the chosen parametrization.  
+ We say $$\gamma, \eta $$ are **equivalent** if $$s'(t) > 0$$, since it guarantee the same orientation. If $$s'(t) <  0 \,\, \forall t$$, since it guarantee the same orientation. If $$s'(t) < 0$$, then $$\eta$$ reverses the orientation.
+ If $$\gamma (s) = (x(s), y(s))$$, then $$l = \int_a^b ((x'(s))^2 + (y'(s))^2)^{\frac{1}{2}}ds$$.
+ The **length** of $$\Gamma$$ is a notion intrinsic to the curve, and does not depends on the parametrization.
    Actually, by chain's rule $$l = \int_a^b \lvert \gamma '(s)\rvert ds = \int_c^d \lvert\gamma '(s(t)) \rvert\lvert s'(t) \rvert dt = \int_c^d \lvert \eta '(t)dt \rvert $$.
+ A special type of parametrization for $$\Gamma$$   
    **Parametrization by arc-length**: if $$\lvert \gamma '(s) \rvert = 1 \,\, \forall s $$
+ **Area** $$\mathcal{A} = \frac{1}{2} \lvert \int_\Gamma (xdy - ydx)\rvert = \frac{1}{2} \lvert \int_a^b x(s)y'(s) - y(s)x'(s)ds\rvert  $$.

#### Statement and proof of the isoperimetric inequality.  

**Theorem 1.1** Suppose that $$\Gamma$$ is a simple closed curve in $$\mathbb{R}^2$$ of length $$l$$, and let $$ \mathcal{A} $$ denote the area of the region enclosed by this curve. Then  \\[ \mathcal{A} \le \frac{l^2}{4\pi} \\]  
with equality if and only if $$\Gamma$$ is a circle.

* **Proof** 

    + Let $$\gamma : [0, 2\pi] \rightarrow \mathbb{R}^2$$ with $$\gamma (s) = (x(s), y(s))$$ be a parametrization of arc-length of the curve $$\Gamma$$, that is $$x'(s)^2 + y'(s)^2 = 1 \,\, \forall s$$.  
So, $$ \frac{1}{2\pi} \int_0^{2\pi} (x'(s)^2 + y'(s)^2) ds = 1 $$.  
    + $$x(s)$$ and $$y(s)$$ are $$2\pi-periodic$$, so  
    $$x(s)\sim\sum_{-\infty}^{+\infty} a_n e^{ins} \quad y(s)\sim\sum_{-\infty}^{+\infty} b_n e^{ins} \quad $$  
    $$x'(s)\sim\sum_{-\infty}^{+\infty} ina_n e^{ins} \quad y'(s)\sim\sum_{-\infty}^{+\infty} inb_n e^{ins} \quad $$   
    According to Parseval's identity  
    \\[ \sum_{n=-\infty}^{+\infty} n^2(\lvert a_n \rvert^2 + \lvert b_n \rvert^2) =  \frac{1}{2\pi} \int_0^{2\pi} (x'(s)^2 + y'(s)^2) ds = 1 \\]  
    Apply bilinear form of Parseval's identity(Lemma 1.5 of Chapter 3)  
    $$
    \begin{array}{lll}
    \mathcal{A} & = & \frac{1}{2} \lvert \int_0^{2\pi} x(s)y'(s) - y(s)x'(s) ds \rvert \\
    & = & \pi \lvert \sum_{-\infty}^{+\infty} n(a_n \overline{b_n} - \overline{a_n}b_n) \rvert \\
    & \le & \pi \sum_{-\infty}^{\infty} n^2(a_n^2 + b_n^2) \\
    & = & \pi
    \end{array}
    $$  
    The inequality include two parts:  
        - $$ \lvert n \rvert \le n^2 $$.
        - $$ \pi \lvert a_n \overline{b_n} - \overline{a_n}b_n \rvert \le 2 \lvert a_n \rvert \lvert b_n \rvert \lvert \le a_n \rvert^2 + \lvert b_n \rvert^2 $$.
    + So, if "=" holds, we must have two "=" holds simultaneously  
    For the first inequality, "=" holds if and only if $$n \le 1$$, so we have  
    $$ x(s) = a_{-1}e^{-is} + a_0 + a_1e^{is} \quad y(s) = b_{-1}e^{-is} + b_0 + b_1e^{is} $$  
    Since x(s), y(s) are real-valued, and 
    \\[ \sum_{n=-\infty}^{+\infty} n^2 (\lvert a_n \rvert^2 + \lvert b_n \rvert^2) = 1 \\]  
    So we have $$ 2(\lvert a_1 \rvert^2 + \lvert b_1 \rvert^2) = 1 $$  
    For the second inequality, we have $$ \lvert a_1 \rvert = \lvert b_1 \rvert = 1/2$$
    + So $$a_1 = \frac{1}{2} e^{i\alpha} \,\, b_1 = \frac{1}{2} e^{i\beta} $$ and $$2\lvert a_1\overline{b_1} - \overline{a_1}b_1 \rvert = 1 $$  
    Implies that $$ sin(\alpha - \beta) = 1$$, so $$\alpha - \beta = \frac{k\pi}{2}$$  
    Finally, we have $$ x(s) = a_0 + cos(\alpha + s) $$, $$ y(s) = b_0 \pm sin(\alpha + s) $$ which is a circle.

### 2. Weyl’s equidistribution theorem  

+ **Symbols** : $$<x> = x - [x]$$
+ Observation: $$<\gamma>, <2\gamma>, <3\gamma>, \dots$$  
    - If $$\gamma$$ is rational, finite $$ <n \gamma > $$ are distinctive
    - If $$\gamma$$ is irrational, all $$ <n \gamma > $$ are distinctive
+ Definition[Equidistribution]. A sequence of numbers $$\xi_1, \xi_2, \dots, \xi_n, \dots$$ in $$[0,1)$$ is said to be equidistributed if for every interval $$(a, b) \in [0, 1)$$  
\\[
    \lim_{n \rightarrow \infty} \frac{ \\# \\{ 1 \le n \le N : \xi_n \in (a, b) \\} }{N} = b - a
\\]

**Theorem2.1** If $$\gamma$$ is irrational, then the sequence of fractional parts $$<\gamma>, <2\gamma>, <3\gamma>, \dots$$ is equidistributed in $$[0, 1)$$   

Of course, $$<\gamma>, <2\gamma>, <3\gamma>, \dots$$ is dense in $$[0, 1)$$. 

**Lemma 2.2** If $$f$$ is continuous and periodic of period 1 and $$\gamma$$ is irrational, then  
$$\frac{1}{N} \sum_{n=1}^N f(n\gamma) \rightarrow \int_0^1 f(x)dx$$ as $$N \rightarrow \infty$$   

**Proof**  

1. Assuse $$f = 1$$, $$e^{2\pi ix}, e^{4\pi ix}, \dots, e^{2k\pi ix}$$  
    - $$f = 1$$ holds obviously
    - Otherwise, $$left \rightarrow 0 = right$$
2. All trignometric polynomials holds.
3. $$\forall$$ continuous $$f$$  
    $$\exists P$$ s.t. $$sup_{x\in \mathbb{R}} \lvert f(x)-P(x) \rvert < \frac{\epsilon}{3} $$  
    for large N we have $$\lvert \frac{1}{N} \sum_{n=1}^N P(n\gamma) - \int_0^1 P(x) dx \rvert < \frac{\epsilon}{3}$$
4. So, totally, for large $$N$$, we have  
$$
\begin{array}{lll}
    \lvert \frac{1}{N} \sum_{n=1}^N f(n\gamma) - \int_0^1 f(x)dx \rvert & < &  \lvert \frac{1}{N} \sum_{n=1}^N ( f(n\gamma) - P(n\gamma) ) \rvert \\ & & + \lvert \int_0^1 f(x) - P(x)dx \rvert \\ & & + \lvert \frac{1}{N} \sum_{n=1}^N f(n\gamma) - \int_0^1 P(x)dx  \rvert \\ & < & \epsilon
\end{array}
$$ 

* Now, return to **Theorem 2.1**
    
Approximate $$\chi_{(a, b)} (x)$$  by $$f^{+}_{\epsilon}$$ and $$f^{-}_{\epsilon}$$ of period 1, and $$f^{-}_{\epsilon}  \chi_{(a, b)} (x) < f^{+}_{\epsilon}$$.  
![Approximation]({{ site.url }}/assets/mathPic/FourierAnalysis-pic2.png)
So, we have  
$$
    \frac{1}{N} \sum_{n=1}^N f^{-}_{\epsilon} (n\gamma) \le S_N \le \frac{1}{N} \sum_{n=1}^N f^{+}_{\epsilon} (n\gamma) 
$$  
which means  
$$
    b-a-2\epsilon \le {\lim\inf}_{N \rightarrow \infty} S_N \le {\lim\sup}_{N \rightarrow \infty} S_N \le b-a+2\epsilon 
$$.  
So, $$\lim_{N \rightarrow \infty} S_N$$ exists, and $$\lim_{N \rightarrow \infty} S_N = b-a$$, which finish the proof of Theorem 2.1.

**Corollary 2.3** The conclusion of Lemma2.2 holds for every function $$f$$ which is Riemann integrable in $$[0, 1]$$ and periodic of period 1.  

* The proof is about the definition of Riemann integrable. 

Next is an interesting interpretation of the Lemma 2.2 and Corollary 2.3 in terms of a simple dynamical system.

* **action $$\rho$$**: $$\theta \rightarrow \theta + 2\pi \gamma$$
* **$$\rho^n$$**: $$\theta \rightarrow \theta + 2\pi n\gamma$$

Then, if $$f$$ is Riemann integrable and $$\gamma$$ is irrational, we have  
\\[
    \lim_{N\rightarrow \infty} \sum_{n=1}^N f(\rho^n(\theta)) = \frac{1}{2\pi} \int_0^{2\pi} f(\theta) d\theta
\\]
Left side is "Time average", right side is "Space average". "Time avg" = "Space avg" is the ergodicity of this system.

According to **Theorem 2.1**, we have the **Weyl's criterion**

* **Weyl's creterion** A sequence of real numbers $$\xi_1, \xi_2, \xi_3, \dots, \xi_n, \dots$$ in $$[0, 1)$$ is equidistributed if and only if for all integers $$k\neq 0$$ one has
\\[
    \frac{1}{N} \sum_{n=1}^N e^{2\pi i k \xi_n} \rightarrow 0, \quad as N \rightarrow \infty
\\]

* **An interesting example**  
Suppose that the sides of a square are reflecting mirrors and that a ray of light leaves a point inside the square. What kind of path will the light trace out?

![Reflections]({{ site.url }}/assets/mathPic/FourierAnalysis-pic3.png)

Consider line $$P_{+} (t, \gamma t)$$ reflecting in the plane, it will  

* Closed and periodic if $$\gamma$$ is rational
* Dense in square if $$\gamma$$ is irrational

### 3. A continuous but nowhere differentiable function

+ **History** 
    - 1861, *Riemann* guessed the function $$R(x) = \sum_{n=1}^{\infty} \frac{\sin (n^2 x)}{n^2}$$ was nowhere differentiable.  
    - 1872, *Weierstrass* try to proof Riemann's guess, and found the first example of nowhere differentiable function: 
\\[ W(x) = \sum_{n=1}^{\infty} b^n \cos (a^n x) \\]
is nowhere differentiable when $$ab > 1+\frac{3\pi}{2} , 0 < b < 1, a\in \{2, 3, 4, \dots\}$$.  
    - 1916, *Hardy* show $$R$$ is not differentiable at all irrational multiples $$\pi$$, and also at certain rational multiples $$\pi$$.
    - 1969, *Gerver* completely settled the problem:    
        $$R$$ is differentiable at $$\frac{p\pi}{q}$$ with $$p,q$$ both odd integers.  
        $$R$$ is not differentiable otherwise.
This section give another example of nowhere differentiable function.  
**Theorem 3.1** If $$0 < \alpha < 1$$, then the function
\\[f_{\alpha}(x) = f(x) = \sum_{n=0}^{\infty} 2^{-n\alpha} e^{i2^n x}\\]
is continuous but nowhere differentiable.

+ **Lacunary Fourier series**: A Fourier series that skips many terms.  
  (like f, wihch only appear in 1, 2, 4, 8, 16...)

Countinuity is easy to prove,  and the proof of nowhere differentiable is really the story of three methods of summing a Fourier series.  

+ **partial sums**: $$S_N(g) = g \ast D_N$$ 
+ **$$Ces\grave{a}ro$$ summability**: $$\sigma(g) = g \ast F_N$$.
+ **Delayed means**: $$\Delta_N(g) = 2\sigma_{2N}(g) - \sigma_N(g)$$.

**Lemma 3.2** Let g be any continuous function that is differentiable at $$x_0$$. Then, the $$Ces\grave{a}ro$$ means satisfy $$\sigma_N(g)'(x_0) = O(\log N)$$. Therefore
\\[\Delta_N(g)'(x_0) = O(\log N).\\]

* **Proof**  
    - $$\sigma_N(g)'(x_0) = \int_{-\pi}^{\pi} F_N'(x_0 - t)g(t)dt = \int_{-\pi}^{\pi} F_N'(t)g(x_0-t)dt$$.  
    Use the property of periodic, we have $$\sigma_N(g)'(x) = \int_{-\pi}^{\pi} F_N'(t)[g(x_0 - t) - g(x_0)]dt$$.  
    Since g is differentiable at $$x_0$$, we have $$\lvert \sigma_N(g)'(x_0)\rvert \le C\int_{-\pi}^{\pi} \lvert F_N'(t) \rvert \lvert t \rvert dt $$.
    - $$\lvert F_N'(t)\rvert \le AN^2$$ a.n.d. $$\lvert F_N'(t)\rvert \le \frac{A}{\lvert t \rvert^2}$$  
    The first inequality use the property of $$ F_N(t)'s $$ trignominal form.   
    The second inequality use the form of $$F_N(t) = \frac{1}{N} \frac{sin^2(tN/2)}{sin^2(t/2)} \$$.
    - Combine above, we have  
    $$
    \begin{array}{lll}
    \lvert \sigma_N(g)'(x_0)\rvert & \le & \lvert \int_{\lvert t \rvert \le 1/N} \lvert F_N'(t)\rvert \lvert t \rvert dt \rvert + \lvert \int_{\lvert t \rvert \ge 1/N} \lvert F_N'(t) \rvert \lvert t \rvert dt \rvert \\
    & \le & A_1 \frac{2}{N} N^2 \frac{1}{N} + A_2 log N \\
    & = & O(1) + O(log N) \\
    & = & O(log N)
    \end{array}
    $$

**Lemma 3.3** If $$2N = 2^n$$, then by **Lacunary** property \\[\Delta_{2N}(f) - \Delta_N(f) = 2^{-n\alpha}e^{i2^nx}.\\]

Now, by the *Lemma 3.2* we have
\\[\Delta_{2N}(f)'(x_0) - \Delta_N(f)'(x_0) = O(\log N)\\]
and the *Lemma 3.3* also implies
\\[\lvert \Delta_{2N}(f)'(x_0) - \Delta_N(f)'(x_0) \rvert = 2^{n(1-\alpha)} \ge cN^{1-\alpha}.\\]
which makes the **contradiction**.

### 4. The heat equation on the circle

In this section, we return to the original problem of heat diffusion considered by Fourier.  

There is a ring, like shown in the picture, we use the notation $$u(x, t)$$ to represent the temperature at time $$t$$ in point $$x$$ of the ring. And $$x = 2\pi\theta$$, $$x \in [ 0, 1 ) $$. 
![]({{site.url}}/assets/mathPic/FourierAnalysis-pic4.png)

We have 2 equations:  

* $$u(x, 0) = f(x)$$.
* $$\frac{\partial u}{\partial t} = c \frac{\partial^2 u}{\partial x^2} \quad$$.

$$u(x, 0) = f(x)$$ is the initial condition, $$f(x)$$ is Riemann integrable.   
$$c$$ is a constant related to the material of the ring.  
We assume $$c = 1$$.

**Solve the problem**:  

1. Assume $$u(x, t) = A(x)B(t)$$, then we have 
\\[
    \frac{B'(t)}{B(t)} = \frac{A\{'}\{'}(x)}{A(x)} = \lambda
\\]
2. Since A(x) must be 1-periodic, so $$\lambda$$ can only take $$\lambda_n = -4\pi^2 n^2$$.  
     For $$\lambda_n$$, we have $$A_n = e^{2\pi i nx} \quad B_n = e^{-4\pi^2 n^2t}$$.
3. Then $$u(x, t) = \sum_{n=-\infty}^{+\infty} a_n e^{-4\pi^2 n^2 t} e^{2\pi inx}$$
4. $$u(x, t) = (f \ast H_t)(x)$$, $$H_t$$ is the heat kernel
\\[
    H_t = \sum_{n=-\infty}^{+\infty} e^{-4\pi^2 n^2 t} e^{2\pi inx}
\\]

+ The convergence of $$u$$ can be easily proved when considering the Riemann integrability of $$f$$.
+ $$H_t$$ is positive everywhere, it can be argued by assuming $$f \le 0$$ and $$H_t(x_0) < 0 $$, which leads to a contradiction.

