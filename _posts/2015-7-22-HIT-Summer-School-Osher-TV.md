---
title: Total Variation - Part II
layout: post
category : [HIT Summer School, Image Processing, TV]
tagline: "Supporting tagline"
tags : [HIT Summer School, Image Processing]
---

* This is the reading notes of an introduction paper (An introduction to Total Variation for Image Analysis) writen by A. Chambolle, et. al.
* It is about Total Variation-based image reconstruction

1. Some theoretical results on functions which minimize the total variation
2. Algorithms to minimize the total variation

#  Some theoretical facts: definitions, properties

## Definition

**Definition 1.1.** The total variation of an image is defined by duality: for $$u \in L_{loc}^1(\Omega)$$ it is given by  
    
$$
    J(u) = sup\{-\int_{\Omega} u div \phi dx : \phi \in C_c^{\infty}(\Omega, \mathbb{R}^N), \lvert \phi(x) \rvert \le 1 \forall x \in \Omega\}
$$  

A function is said to have Bounded Variation whenever $$ J(u) < +\infty$$. 

Typical examples:

* A smooth function $$ u \in C^1(\Omega) $$ (or in fact a function $$ u \in W^{1, 1}(\Omega)$$): in this case,  

$$
    -\int_{\Omega} u div \phi dx = \int_{\Omega} \phi \cdot \nabla u dx
$$

## An equivalent definition

## Main properties of the total variation

## Functions with bounded variation
