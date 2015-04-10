---
title: Chapter3 Convergence of Fourier Series 
layout: post
category : [books, Fourier Analysis by Stein]
tagline: "Supporting tagline"
tags : [Analysis, Fourier Analysis]
---
### 1. Mean-Square convergence of Fourier Series  

**Theorem 1.1** Suppose f is integrable on the circle. Then
\\[
\frac{1}{2\pi}\int_0^{2\pi} |f(\theta)-S_N(f)(\theta)|^2 d\theta \to 0 
\\]

#### 1.1 Vector spaces and inner product  
**Vector space**  
1. '+' between elements:  $$X+Y=Y+X\\(X+Y)+Z=X+(Y+Z)...$$  
2. $$\lambda X \in V$$  

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
1.
