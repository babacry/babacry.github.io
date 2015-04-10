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

#### 1.2 Proof of mean-Square convergence  

**lemma1.2 (Best approximatino)**  If $$f$$ is integrable on the circle with Fourier coefficients $$a_n$$, then  
\\[ \lVert f\rVert ^2 = \lVert f-S_N(f) \rVert^2 + \sum_{|n| \le N} |a_n|^2 \\]
for any complex numbers $$c_n$$ Moreover, equality holds precisely when $$c_n=a_n$$ for all $$|n| \le N$$.

### 2. Return to pointwise convergence  

