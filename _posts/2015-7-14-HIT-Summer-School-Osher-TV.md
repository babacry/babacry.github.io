---
title: Total Variation - Part I 
layout: post
category : [HIT Summer School, Image Processing, TV]
tagline: "Supporting tagline"
tags : [HIT Summer School, Image Processing]
---

* This is the reading notes of an introduction paper (An introduction to Total Variation for Image Analysis) writen by A. Chambolle, et. al.
* It is about Total Variation-based image reconstruction

1. Some theoretical results on functions which minimize the total variation
2. Algorithms to minimize the total variation


## Why is total variation useful for images?

Total variation was firstly introduced in 1992 by Rudin, Osher and Fatemi.  

### The Bayesian approach to image reconstruction

* **$$g = Au+n$$**
* **$$g = (g_{i, j})_{1 \le i, j \le N}$$**: Image of discrete, bounded 2D-signals.  
* **$$u\in \mathbb{R}^{N\times N}$$**: The initial signal
* **$$A$$**: some transformation(blurring, sampling...).
* **$$n = (n_{i,j})$$**: The noise (e.g. Gaussian norm with avg = 0 and standard-deviation = $$\sigma$$).
* **a priori probability density**: $$P(u) \sim e^{-p(u)}$$

Use Bayes' Rule $$P(u\lvert g)P(g) = P(g\lvert u)P(u)$$, and $$n \sim e^{-\frac{1}{2{\sigma}^2 \sum_{i, j} \lvert g_{i, j} - (Au)_{i, j} \rvert^2}}$$, $$P(u) \sim e^{-p(u)}$$,  
we have
\\[
    p(u\lvert g) \sim \frac{1}{Z(g)} e^{ - p(u) - \frac{1}{2\sigma^2} \sum_{i, j} \lvert g_{i, j} - (Au)_{i, j}\rvert^2}
\\]

($$Z(g)$$ is the normalization factor)

It give the "maximun a posterior"(MAP) problem: find the maximum of $$p(u\lvert g)$$  
an equivalent version is the minmum problem:
\\[
    \min_u p(u) + \frac{1}{2\sigma^2} \sum_{i, j} \lvert g_{i, j} - (Au)_{i, j}\rvert^2
\\]

### Variational models in the continuous setting

Idea: minimizing an energy. 
Use A = Id in MAP problem in the following discussion.  
MAP problem:
\\[
    \min_{u\in L^2(\Omega)} \lambda F(u) + \frac{1}{2}\int_{\Omega} \lvert u(x) - g(x) \rvert^2 dx_{}
\\]

**explaination**:  

* $$F$$: Functional which corresponding a prioro probability density $$p(u)$$
* $$\lambda > 0$$: weight balancing factor

Example of F:  

1. $$F(u) = \frac{1}{2} \int_{\Omega} u^2 dx$$.
2. $$F(u) = \frac{1}{2} \int_{\Omega} \lvert \nabla u \rvert^2 dx$$.

The Euler-Lagrange equations of above chosen F are  

1. $$\lambda u + u - g = 0$$. 
2. $$\lambda \triangle u + u - g = 0$$. 

(Symbols: $$\nabla$$(gradient) $$\Delta $$(Laplacian))

From the example  

1. no regularization has been occured (since $$F(u) = \frac{1}{2} \int u^2$$ enforces no spatial regularization)
2. too much spatial regularization

Contradiction:

* The image $$u$$ must belong to $$H^1(\Omega)$$ (whose derivative is square-integrable)
* Functions in $$H^1(\Omega)$$ cannot present discontinuities across hypersurfaces

* A quick argument which justify above
    + Assume $$u: [0, 1] \rightarrow \mathbb{R} \quad u \in H^1(0, 1)$$
    + Then for each $$0 < s < t < 1$$
\\[
    u(t) - u(s) = \int_s^t u'(r) dr \le \sqrt{t-s} \sqrt{\int_s^t \lvert u'(r) \rvert^2 dr} \le \sqrt{t-s} \lVert H \rVert_{H^1}^2
\\]
$$ \Rightarrow u $$ must be $$\frac{1}{2}\textrm{-}H\ddot{o}lder$$ 

* If $$u \in H^1((0, 1) \times (0, 1))$$
* Then for a.e. $$ y \in (0, 1) \quad x \mapsto u(x, y) \in H^1(0, 1) $$  (since $$\int_0^1(\int_0^1 \lvert \frac{\partial{u}}{\partial{x}}(x, y) dx \rvert)dy$$)  
$$ \Rightarrow $$ For a.e. $$ y \in (0, 1) \quad x \mapsto u(x, y)$$ will be $$\frac{1}{2}\textrm{-}H\ddot{o}lder$$   
$$ \Rightarrow $$ It certainly can not jump across the square boundaries in figure


Good $$F$$ should be like  

* ensure some spatial regularity
* preserve the edges

Two ideas considering $$F$$ 

* Idea by D.Geman. and S.Geman. (Bayesian)  
    + variable $$l = (l_{i+\frac{1}{2}, j}, l_{i, j+\frac{1}{2}})_{i, j}$$ can only take values from $$\{0, 1\}$$ 
    + Meaning if $$l$$:  
$$
    l_{i+\frac{1}{2}, j} = \left\{\begin{array}{ll}
        1 & \textrm{there is an edge between} (i, j) \textrm{and} (i+1, j) \\
        0 & \textrm{there is no edge between} (i, j) \textrm{and} (i+1, j)
    \end{array} \right.
$$
    + $$ p(u) \rightarrow p(u, l) $$  
$$
    p(u, l) = \lambda \sum_{i, j} ((1 - l_{i+\frac{1}{2}, j})(\mu_{i+1, j} - \mu_{i, j})^2 + (1 - l_{i, j+\frac{1}{2}})(\mu_{i, j+1} - \mu_{i, j})^2 ) + \mu \sum_{i, j} (l_{i+\frac{1}{2}, j} + l_{i, j+\frac{1}{2}})
$$
    + So, the MAP problem will now look like  
$$
    \min_{u, l} p(u, l) + \frac{1}{2\sigma^2} \sum_{i, j} \lvert g_{i, j} - \mu_{i, j} \rvert^2
$$

* Idea by D.Mumford and J.Shah  
discrete $$ \rightarrow$$ continuous
    + Actually, the set $$\{l = 1\}$$ is just a curve $$K \subset \Omega$$, so that the problem will look like  
    $$
        min_{u, K} \lambda \int_{\Omega\backslash K} \lvert \nabla u \rvert dx + \mu length(K) + \int_{\Omega} \lvert u-g \rvert^2 dx
    $$

Here, we conclude the disadvantages of above ideas

* Very difficult to analyse mathematically
* Numerically complicated (non-convex)
* Only 1-dim problem can be solved in polynomial times by DP

### A convex, yet edge-preserving approach

In the context of image reconstruction, it was proposed first by Rudin, Osher and Fatemi to consider the "Total Variation" as a regularizer $$F(u)$$ for (MAPc)

* It can be seen as extension of energt $$F(u) = \int_\Omega \lvert \nabla u(x) \rvert dx$$
* It is well-defined for $$C^1(W^{1, 1})$$ functions
* Convex

But, how to deal with the problem raised earlier($$W^{1, 1}$$ functions cannot present discontinuity across a line)?  
Consider the problem:
\\[
    \min_u \lambda \int_0^1\lvert u'(t) \rvert dt + \int_0^1 \lvert u(t) - g(t) \rvert^2 dt
\\]
with $$ g = \chi_{(\frac{1}{2}, 1)} $$

Denote $$ \varepsilon = \lambda \int_0^1\lvert u'(t) \rvert dt + \int_0^1 \lvert u(t) - g(t) \rvert^2 dt $$
and assume the minimizer is $$u$$ if it exists.  

* For $$v = \{u, 1\}$$, $$\varepsilon(v) \le \varepsilon(u) \Rightarrow u \le 1 $$
* By the same argument above, we have $$ u \ge 0 $$
* By symmetry, $$ t \mapsto 1 - u(1-t) $$ has the same energy as $$u$$
* By convexity  
$$
    \varepsilon (\frac{1-u(1-\cdot) + u}{2}) \le \frac{1}{2} \varepsilon(1-u(1-\cdot)) + \frac{1}{2} \varepsilon(u) = \varepsilon(u)
$$  
Also, $$\varepsilon(\frac{v_1+v_2}{2}) \le \frac{1}{2}(\varepsilon(v_1) + \varepsilon(v_2))$$, "=" holds iff $$v_1 = v_2$$  
Combine above two conditions, we know that $$\frac{1-u(1-\cdot) + u}{2}$$ has a lower energy if $$u \neq 1-u(1-\cdot)$$  
And $$u$$ is the minimizer, so $$u$$ must be centrosymmetric of $$(\frac{1}{2}, \frac{1}{2})$$, like shown in the picture.

![]({{site.url}}/assets/mathPic/TV-pic1.png)

Assume $$ m = min(u), M = max(u)$$, then we have $$ m = 1 - M$$  
So
\\[
    \varepsilon (u) \ge \lambda(M-m) + m^2 = \lambda(1-2m) + m^2    
\\]
Which means,

* If $$\lambda \ge \frac{1}{2}$$, then $$u \equiv \frac{1}{2}$$ ("=" holds of above equition)
* If $$\lambda < \frac{1}{2}$$, then $$\varepsilon (u) \ge \lambda(M-m) + m^2 = \lambda(1-2m) + m^2 \ge \lambda(1-\lambda)$$    

* Construct $$\{ u_n \}_{n=2}^\infty$$  
    $$
    u_n = \left\{ \begin{array}{ll}
            \lambda & t\in [0, \frac{1}{2} - \frac{1}{n}] \\
            \frac{1}{2} + n(t-\frac{1}{2})(\frac{1}{2} - \lambda) & t \in (\frac{1}{2} - \frac{1}{n}, \frac{1}{2} + \frac{1}{n}) \\
            1-\lambda & t \in [\frac{1}{2} - \frac{1}{n}, 1]
        \end{array} \right.
    $$

Here is the picture of $$u_n$$
![]({{site.url}}/assets/mathPic/TV-pic2.png)

* So, $$ \varepsilon (u_n) \le \lambda (1- 2\lambda) + (1 - \frac{2}{n}) \lambda^2 + \frac{2}{n} \rightarrow \lambda(1-\lambda)$$ as $$ n \rightarrow \infty$$ 
* Hence, $$\inf_{u\in\{u_n\}} \varepsilon(u) = \lambda(1 - \lambda)$$

But $$\lim_{n\rightarrow \infty} u_n$$ is not differentiable.  
So, we have to extend in an appropriate way the notion of derivative to give a solution to this problem, which leads to "total variation".





