---
title: Chapter3 Convergence of Fourier Series 
layout: post
category : [books, Fourier Analysis by Stein]
tagline: "Supporting tagline"
tags : [Analysis, Fourier Analysis]
---
This chapter concerns about "global" and "local" convergence of f.

* "global": Orthogonal is used to prove mean-square convergence. So vector space, inner product and Hilber space are introduced.  
* "local": Fourier series convergences at $$\theta$$ whenever f is differentiable at $$\theta$$.
   * But Fourier series may fail to converge when f is just continuous (an example shown).

### 1. Mean-Square convergence of Fourier Series  

**Theorem 1.1** Suppose f is integrable on the circle. Then
\\[
\frac{1}{2\pi}\int_0^{2\pi} |f(\theta)-S_N(f)(\theta)|^2 d\theta \to 0 
\\]

#### 1.1 Vector spaces and inner product  
**Vector space**  
: (a). '+' between elements:  $$X+Y=Y+X\\(X+Y)+Z=X+(Y+Z)$$  
: (b). \\(\lambda X \in V\\)   

**Inner Product**  

* on a vector space over $$\mathbb{R}$$   
   1. symmetric: $$(X,Y)=(Y,X)$$  
   2. linear: $$(aX+bY, Z) = a(X,Z)+b(Y,Z)$$  
   3. positive-definite: $$(X,X)\ge 0$$    
* on a vector space over $$\mathbb{C}$$   
   1. Hermitian: $$(X,Y)=\overline{(Y,X)}$$  
   2. linear && conjugate-linear:  $$ (aX+bY, Z) = a(X,Z)+b(Y,Z)  \\  (X, aY+bZ) = \bar{a}(X,Y)+\bar{b}(X,Z)  $$  
   3. positive-definite: $$(X,X)\ge 0$$    

**Three important results about orthogonal**  

1. Pathagorean Theorem: if $$X\perp Y$$ then $$\|X+Y\|^2=\|X\|^2+\|Y\|^2$$ 
2. Cauchy-Schwarz inequality: $$(X,Y) \le \|X\|\|Y\|$$  
3. The Triangle inequality: $$\|X+Y\| \le \|X\|+\|Y\|$$   

Hilbert Space
: (a). positive-definite: $$\|X\|=0 \Rightarrow X=0$$  
: (b). complete  

pre-Hilbert Space  
: either of above conditions fails

$$\mathbb{R}^d, \mathbb{C}^d, l^2(\mathbb{Z})$$ are all Hilbert space.  

**pre-Hilber space $$\mathcal{R}$$ with (a) (b) both fail**  
$$\mathcal{R}$$: Set of complex-valued Riemann integrable functions on $$[0,2\pi]$$.  

* fails (a): $$\|f\|=0 \Rightarrow f$$ vanishes except on a set of measure 0  
* fails (b): $$\mathcal{R}$$ is not complete  
$$
f(\theta) = \left\{ \begin{array}{ll}
                    0 & for \, \theta = 0 \\ 
log(\frac{1}{\theta}) & for \, 0 < \theta \le 2\pi 
\end{array} \right. \quad
$$
$$
f_n(\theta) = \left\{ \begin{array}{ll}
                    0 & for \, 0 \le \theta \le \frac{1}{n} \\ 
log(\frac{1}{\theta}) & for \, \frac{1}{n} < \theta \le 2\pi 
\end{array} \right.
$$  
$$\{f_n\}$$ forms a Chuchy sequence in $$\mathcal{R}$$
but can not converge to an element in $$\mathcal{R}$$.   
Since if $$f_n \rightarrow g \in \mathcal{R}$$, it must be $$f$$, but $$f$$ is not integrable.

#### 1.2 Proof of mean-Square convergence  
Consider pre-Hilbert space $$R$$ with
: inner product: $$(f,g) = \frac{1}{2\pi} \int_0^{2\pi} f(\theta) \overline{g(\theta)} d\theta$$  
: norm:          $$\|f\|^2 = (f,f) =  \frac{1}{2\pi} \int_0^{2\pi} f(\theta) \overline{f(\theta)} d\theta$$  

Theorem 1.1 becomes $$\|f-S_N(f)\| \rightarrow 0$$ as $$N \rightarrow \infty$$  

Let $$e_n(\theta) = e^{in\theta}$$  
then $$\{e_n\}_{n \in \mathbb{Z} } $$ is orthonormal  
$$
(e_n, e_m) = \left\{ \begin{array}{ll}
1 & if \, n=m \.\
0 & if \, n\ne m
\end{array} \right.\\
(f, e_n) = \hat{f_n} = a_n \\
$$  
$$
(f-\sum_{|n| \le N}a_n e_n) \perp \sum_{|n| \le N}a_n e_n {}_{\Longrightarrow}^{Pathagorea}\\
\begin{array}{lll}
\|f\|^2 & = & \|f-\sum_{|n| \le N}a_n e_n)\|^2 + \|\sum_{|n| \le N}a_n e_n\|^2 \\
& = & \|f-S_N(f)\|^2 + \int_{|n|\le N} |a_n|^2
\end{array}
$$

**lemma1.2 (Best approximatino)**  If $$f$$ is integrable on the circle with Fourier coefficients $$a_n$$, then  
\\[ \lVert f\rVert ^2 = \lVert f-S_N(f) \rVert^2 + \sum_{|n| \le N} |a_n|^2 \\]
for any complex numbers $$c_n$$. Moreover, equality holds precisely when $$c_n=a_n$$ for all $$|n| \le N$$.

**Proof of theorem 1.1**  

* If $$f$$ is continuous  
Trigonometric polynimials are dense in the space of continuous functions on the circle, say $$C_f$$.  
So, $$\forall \epsilon > 0, \exists P \in C_f \, s.t. \|f-P\| < \epsilon $$   
Assume deg(P) = M, according to "Best approximation theorem",   
then, $$\forall N \le M \|f-S_N(f)\| \le \|f-P\| < \epsilon $$   
* If $$f$$ is merely integrable  
Apply Theorem3.2 in Chapter2, choose a continuous function g s.t.  $${sup}_{\theta \in [0,s\pi]}|g(\theta)| \le {sup}_{\theta \in [0,s\pi]}|f(\theta)| < \epsilon \quad$$  and  $$\quad \int_0^{2\pi}|f(\theta) - g(\theta)|d\theta < \epsilon ^2$$  
We have $$\|f-g\| \le C\epsilon ^2$$, since $$g$$ is continuous, proof return to part 1.  

**Parseval's identity**  
\\[ \sum_{n = -\infty}^{n = +\infty} |a_n|^2 = \lVert f\rVert ^2\\]

**Summarize**  
**Theorem 1.3** Let f be an integrable function on the circle with $$f~\sum_{n = -\infty}^{+\infty} a_n e^{in\theta}$$. Then we have  
1. Mean-square convergence of Fourier Series  
\\[
\frac{1}{2\pi}\int_0^{2\pi} |f(\theta)-S_N(f)(\theta)|^2 d\theta \to 0 
\\]
2. Parseval's indentity
\\[ \sum_{n = -\infty}^{n = +\infty} |a_n|^2 = \lVert f\rVert ^2\\]

Apply Parseval's identity or Bessel's inequality, we get  
**Theorem 1.4 (Riemann-Lebesgue lemma)** If f is integrable on the circle then $$ \hat{f}(n) \rightarrow 0 \,as\, |n|\rightarrow \infty\quad$$
and $$\int_0^{2\pi} f(\theta)cos(N\theta) d\theta \rightarrow 0\,as\, N\rightarrow \infty$$  

A more general version of Parseval's identity:  
**Lemma 1.5** Suppose F and G are intefrable on the circle with $$F~\sum a_n e^{un\theta} \, and \, G~\sum b_n e^{un\theta}$$  
Then  \\[\frac{1}{2\pi}\int_0^{2\pi} F(\theta)\overline{G(\theta)}d\theta = \sum_{n = -\infty} ^ {+\infty}a_n\overline{b_n}\\]  
Proof. Actually, $$(F, G) = \frac{1}{4}[\|F+G\|^2-\|F-G\|^2+ i(\|F+iG\|^2 - \|F-iG\|^2)]$$  

### 2. Return to pointwise convergence  

