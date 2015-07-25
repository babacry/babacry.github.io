---
title: Generalized Stoke's Theorem
layout: post
category: [Analysis]
tagline: "Supporting tagline"
tags : [Analysis]
---

Green's Theorem, Kelvin-Stokes Theorem... must be the worst part of my calculus learning. 

So, in order to understand better, I want to give a conclusion and recall some Theorems which are very useful.

## Generalized Stoke's Theorem

**Generalized Stokes's Theorem** Let $$X$$ be a compact piece-with-boundary of a $$(k-1)$$-dimensional oriented manifold $$M \subset \mathbb{R}^n$$. Give the boundary $$\partial X$$ of $$X$$ the boundary orientation, and let $$\phi$$ be a $$k$$-form defined on an open set containing $$X$$. Then     

$$
    \int_{X} d\omega = \int_{\partial X} \omega
$$

($$d$$ is the exterior derivative)

### Some special cases of Stoke's Theorem:  

* Fundamental theorem of calculus $$\int_a^b dF = F(b) - F(a)$$: $$n = k = 1$$.
* Green's Theorem : $$ n = k = 2 $$.
* Divergence Theorem of Gauss: $$ n = k = 3 $$. 
* Kelvin–Stokes theorem: $$ n = 3\,\,\, k = 2$$.

### Exterior derivative

#### Axioms for the exterior derivative
+ $$df$$ is the differential of $$f$$ for smooth functions f.
+ $$d(df)$$ = 0 for any smooth function $$f$$.
+ $$d(\alpha \wedge \beta) = d \alpha \wedge \beta + (-1)^p (\alpha \wedge d\beta)$$ where $$\alpha$$ is a $$p$$-form.

#### Definition of exterior derivative of $$k$$-form over $$\mathbb{R}^n$$
The exterior derivative of a $$k$$-form  

$$
    \omega = f_I dx^I = f_{i_1, i_2, ..., i_k} dx^{i_1} \wedge dx^{i_2} \wedge \cdots \wedge x^{i_k}
$$

over $$\mathbb{R}^n$$ is defined as

$$
    d\omega = \sum_{i = 1}^n \frac{\partial f_I}{\partial x^i} dx^i \wedge dx^I
$$


## Green's Theorem

**Green's Theorem** Let $$C$$ be a positively oriented, piecewise smooth, simple closed curve in a plane, and let $$D$$ be the region bounded by $$C$$. If L and M are functions of $$(x, y)$$ defined on an open region containing $$D$$ and have continuous partial derivative there, then  

$$
    \oint_{C} (Ldx + Mdy) = \int\!\!\int_D(\frac{\partial M}{\partial x} - \frac{\partial L}{\partial y}) dxdy    
$$

#### Actually

$$  
\begin{array}{lll}
    d(Ldx + Mdy) & = & \frac{\partial L}{\partial x} dx \wedge dx + \frac{\partial L}{\partial y} dy \wedge dx + \frac{\partial M}{\partial x} dx \wedge dy + \frac{\partial L}{\partial y} dy \wedge dy \\
    & = & (\frac{\partial M}{\partial x} - \frac{\partial L}{\partial y}) dx \wedge dy    
\end{array}
$$

## Divergence Theorem of Gauss

Suppose $$V$$ is a subset of $$\mathbb{R}^n$$ (in the case of $$n=3$$, $$V$$ represents a volume in $$3D$$ space) which is compact and has a piecewise smooth boundary $$S$$ (also indicated with $$ \partial{V} = S $$ ). If $$F$$ is a continuous differentiable vector field defined on a neighborhood of $$V$$, then we have:  

$$
    \iiint_V (\nabla \cdot F) dV = \iint_S F \cdot n dS
$$

#### Actually for $$ n = 3 $$  

$$
\begin{array}{lll}
d(A dy \wedge dz + B dz \wedge dx + C dx \wedge dy) & = & \frac{\partial A}{\partial x} dx \wedge dy \wedge dz + \frac{\partial B}{\partial y} dy \wedge dz \wedge dx + \frac{\partial C}{\partial z} dz \wedge dx \wedge dy \\
& = & (\frac{\partial A}{\partial x} + \frac{\partial B}{\partial y} + \frac{\partial C}{\partial x}) dx \wedge dy \wedge dz
\end{array}
$$

## Kelvin-Stokes Theorem

Let $$\gamma: [a, b] \rightarrow R^2$$ be a piecewise smooth Jordan plane curve. The Jordan curve theorem implies that $$\gamma$$ diveide $$R^2$$ into two components, a compact one and another that is non-compact. Let $$D$$ denote the compact part that is bounded by $$\gamma$$ and suppose $$\psi: D \rightarrow R^3$$ is smooth, with $$S: \psi (D)$$. If $$\Gamma$$ is the space curve defined by $$\Gamma (t) = \psi(\gamma(t))$$ and $$F$$ is a smooth vector field on $$R^3$$. Then:  

$$
\oint_\Gamma F d\Gamma = \iint_S \nabla \times F dS
$$

#### Actually  

$$
\begin{array}{lll}
    d(Pdx + Qdy + Rdz) & = & \frac{\partial P}{\partial y} dy \wedge dx + \frac{\partial P}{\partial z} dz \wedge dx + \frac{\partial Q}{\partial x} dx \wedge dy + \frac{\partial Q}{\partial z} dz \wedge dy + \frac{\partial R}{\partial z} dx \wedge dz + \frac{\partial R}{\partial y} dy \wedge dz \\
                       & = & (\frac{\partial R}{\partial y} - \frac{\partial Q}{\partial z})dy \wedge dz + (\frac{\partial P}{\partial z} - \frac{\partial R}{\partial x}) dz \wedge dx + (\frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y}) dx \wedge dy
\end{array}
$$


### Thanks

Thanks for Weina Wang and Alan Zhu. They explain things like vector field, exterior derivative... for me, which helped me a lot in understanding Generalized Stoke Theorem.





























