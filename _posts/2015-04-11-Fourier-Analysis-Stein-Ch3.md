---
title: Chapter3 Convergence of Fourier Series 
layout: post
category : [books, Fourier Analysis by Stein]
tagline: "Supporting tagline"
tags : [Analysis, Fourier Analysis]
---
This chapter concerns about "global" and "local" convergence of Fourier series of $$f$$.

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
1 & if \, n=m \\
0 & if \, n\ne m
\end{array} \right.\\
(f, e_n) = \hat{f_n} = a_n \\
$$  
$$
(f-\sum_{|n| \le N}a_n e_n) \perp \sum_{|n| \le N}a_n e_n \stackrel{Pathagorea}{\Longrightarrow}\\ \begin{array}{lll}
\|f\|^2 & = & \|f-\sum_{|n| \le N}a_n e_n)\|^2 + \|\sum_{|n| \le N}a_n e_n\|^2 \\
& = & \|f-S_N(f)\|^2 + \int_{|n|\le N} |a_n|^2
\end{array}
$$

**Lemma1.2 (Best approximatino)**  If $$f$$ is integrable on the circle with Fourier coefficients $$a_n$$, then  
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
**Theorem 1.3** Let f be an integrable function on the circle with $$f\sim\sum_{n = -\infty}^{+\infty} a_n e^{in\theta}$$. Then we have  
1. Mean-square convergence of Fourier Series  
\\[
\frac{1}{2\pi}\int_0^{2\pi} |f(\theta)-S_N(f)(\theta)|^2 d\theta \to 0 
\\]
2. Parseval's indentity
\\[ \sum_{n = -\infty}^{n = +\infty} |a_n|^2 = \lVert f\rVert ^2\\]

* **Remark 1** If $${e_n}$$ is any orthonormal family of functions on the circle with  $$a_n = (f, e_n)$$   
$$\Rightarrow$$ Bessel's inequality: $$\sum_{n=-\infty}^{+\infty}|a_n|^2 \le \|f\|^2 $$, "=" holds when $$\{e_n\}$$ is a "basis". 
* **Remark 2** $$\exists f: \mathcal{R} \rightarrow l^2(\mathbb{Z})$$, $$\mathcal{R}$$ is not complete, but $$l^2(\mathbb{Z})$$ is Hilbert space,
which means $$\exists {a_n} \in l^2(\mathbb{Z})$$, yet no function in $$\mathcal{R}$$ has nth Fourier coefficient wqual to $$a_n$$ for all n.  

Apply Parseval's identity or Bessel's inequality, we get  
**Theorem 1.4 (Riemann-Lebesgue lemma)** If f is integrable on the circle then $$ \hat{f}(n) \rightarrow 0 \,as\, |n|\rightarrow \infty\,$$
and $$\int_0^{2\pi} f(\theta)cos(N\theta) d\theta \rightarrow 0\,as\, N\rightarrow \infty$$  

A more general version of Parseval's identity:  
**Lemma 1.5** Suppose F and G are integrable on the circle with $$F\sim\sum a_n e^{un\theta} \, and \, G\sim\sum b_n e^{un\theta}$$  
Then  \\[\frac{1}{2\pi}\int_0^{2\pi} F(\theta)\overline{G(\theta)}d\theta = \sum_{n = -\infty} ^ {+\infty}a_n\overline{b_n}\\]  
Proof. Actually, $$(F, G) = \frac{1}{4}[\|F+G\|^2-\|F-G\|^2+ i(\|F+iG\|^2 - \|F-iG\|^2)]$$  

### 2. Return to pointwise convergence  

####  2.1 A local result  
**Theorem 2.1** Let $$f$$ be an integrable function on the circle which is differentiable at a point $${\theta}_0$$. Then $$S_N(f)(\theta_0) \rightarrow f(\theta_0) \,as\, N \rightarrow \infty. $$   

* Proof.  
$$
F(t) = \left\{\begin{array}{ll} 
\frac{f(\theta_0-t) - f(\theta_0)}{t} & if \, t \neq 0 \,and\, |t| < \pi \\ 
-f'(\theta_0) & if \, t = 0
\end{array} \right.
$$    
Since $$f$$ is differentiable at $$\theta_0$$, so $$F$$ is bounded and integrable.  
$$
S_N(f)(\theta_0) - f(\theta_0) = \frac{1}{2\pi} \int_{-\pi}^{\pi} F(t)tD_N(t)dt\\
F(t)tD_N(t) = \frac{F(t)t\sin(N+1)t }{sin(\frac{t}{2})} = \underline{F(t)t\frac{\cos(\frac{t}{2})}{\sin(\frac{t}{2})}}_{{1}} \sin(Nt) + \underline{F(t)t}_{{2}} \cos(Nt)
$$  
both $${1, 2}$$ are integrable, according to Riemann-Lebesgue lemma, we have $$|S_N(f)(\theta_0) - f(\theta_0)| \rightarrow 0 \, as\, N \rightarrow \infty $$

**Theorem 2.2** Suppose $$f$$ and $$g$$ are two integrable functions defined on the circle, and for some $$\theta_0$$ there exists an open interval $$I$$ containing $$\theta_0$$ such that  
\\[
f(\theta) = g(\theta) \quad \forall \theta \in I
\\]
Then, $$S_N(f)(\theta_0)-S_N(g)(\theta_0)) \rightarrow 0$$ as N tends to infinity    

### 2.2 A continuous function with diverging Fourier series

Theorem 2.1 fails when replace differentiable with weaker assumption continuous.  
We construct the counter-example with principle "symmetry-breaking".  
Split the Fourier series $$\sum_{n = -\infty}^{\infty} a_n e^{in\theta}$$ to $$\sum_{n \ge 0} a_n e^{in\theta}$$ and $$\sum_{n < 0} a_n e^{in\theta}$$ 

**Sawtooth function $$f$$**

1. odd  
2. $$f(\theta) = i(\pi -\theta) \quad$$ when $$\,\theta \in (0,\pi)$$

![Sawtooth Function]({{ site.url }}/assets/mathPic/sawtoothFunction.png)
$$f(\theta) \sim \sum_{n\neq 0} \frac{e^{in\theta}}{n}$$ 
while if breaking symmetry ,
$$\sum_{n=-\infty}^{-1}\frac{e^{in\theta}}{n}$$ is not the Fourier series of a Riemann integrable function(see appendix).  

Define two functions on $$[-\pi, \pi]$$:  
$$f_N(\theta) = \sum_{1 \le n \le N}\frac{e^{in\theta}}{n}\quad and \quad \widetilde{f}_N({\theta}) = \sum_{-N\le n\le -1}\frac{e^{in\theta}}{n}$$.  

1. $$ \lvert \widetilde{f}_N(0) \rvert \ge c\log N $$.   
2. $$f_N(\theta)$$ is uniformly bounded in $$N$$ and $$\theta$$.     

1 is easily proved, 2 can be proved like Tauber's Theorem:  

**Lemma 2.3** Suppose that the Abel means $$A_r=\sum_{n=1}^{\infty} r^n c_n$$ of the series $$\sum_{n=1}^{\infty} c_n$$ are bounded as $$r$$ tends to 1 (with $$r$$ < 1). If $$c_n = O(1/n)$$, then the partial sums $$S_N = \sum_{n=1}^{N} c_n$$ are bounded.(The proof is tricky, we need to let $$r=1-1/N$$)   

And apply lemma 2.3 to $$f_N(\theta)$$, $$c_n = \frac{e^{in\theta}}{n} -  \frac{e^{-in\theta}}{n} = O(1/n)$$  
$$Ar(f)(\theta) = f\ast Pr(\theta) $$  
Since $$f$$ is bounded and $$Pr$$ is a good kernel.  
So $$S_N(f)(\theta)$$ is uniformly bounded in $$N$$ and $$\theta$$.  

**Next, we construct a countinuous function with diverging Fourier series.**    

$$f_N(\theta) = \sum_{1 \le n \le N}\frac{e^{in\theta}}{n}\quad and \quad \widetilde{f}_N({\theta}) = \sum_{-N\le n\le -1}\frac{e^{in\theta}}{n}$$.  
Let
$$P_N(\theta) = e^{i(2N)\theta}f_N(\theta) \quad and \quad \widetilde{P}_N({\theta}) = e^{i(2N)\theta}\widetilde{f}_N(\theta)$$.  
Then, we have   
$$
S_M = \left\{\begin{array}{ll}
P_N & if \, M \ge 3N \\
 \widetilde{P}_N & if \, M = 2N \\
0 & if \, M < 2N 
\end{array}\right.
$$  

Construct a convergent series of positive terms $$\sum \alpha_k$$ and a sequence $$N_k$$, s.t.  
1. $$N_k > 3N_{k-1}$$   
2. $$ \alpha_k \log N_k \rightarrow \infty$$ as $$k \rightarrow \infty $$

Let **$$f(\theta) = \sum_{k=1}^{\infty} \alpha_kP_{N_k}(\theta)$$**   
since $$|p_{N_k}(\theta)|$$ is bounded, then the seires above converges uniformly to a continuous periodic function.  

Then, we have $$\lvert S_{2N_m}(f)(0)\rvert = \lvert\sum_{k=1}^{\infty} \alpha_kS_{2N_m}(P_{N_k})(0)\rvert$$  

|if $$k < m \quad$$,| $$3N_k < N_m < 2N_m \quad $$ | $$S_{2N_m}(P_{N_k}) = P_{N_k}$$
|if $$k = m \quad$$,| $$N_k = N_m \quad$$|$$ S_{2N_m}(P_{N_k}) = \widetilde{P}_{N_k}$$
|if $$k > m \quad$$,| $$N_k > 3N_m > N_m \quad$$|$$ S_{2N_m}(P_{N_k}) = 0$$

So,  $$\lvert S_{2N_m}(f)(0)\rvert = \lvert \alpha_m \widetilde{P}_{N_m}(0) + \sum_{k=m+1}^{\infty} \alpha_k P_{N_k}(0) \rvert \ge c\alpha_m \log N_m + O(1) \rightarrow \infty$$ as $$m \rightarrow \infty$$ 

### Appendix  
**$$\sum_{n=-\infty}^{-1}\frac{e^{in\theta}}{n}$$ is not the Fourier series of a Riemann integrable function.**

* Proof.   
Suppose it were the Fourier series of integrable function $$\tilde{f}$$.  
Then $$lim_{r\rightarrow 1}\lvert Ar(\tilde{f})(\theta)\rvert = lim_{r \rightarrow 1} \sum_{n=1}^{\infty} \frac{r^n}{n} = \infty$$  
While $$\lvert Ar(\tilde{f})(\theta)\rvert \le \frac{1}{2\pi} \int_{-\pi}^{\pi} \lvert \tilde{f}(\theta) \rvert Pr(\theta) d\theta \le sup\lvert\tilde{f}(\theta) \rvert$$  
but $$f$$ is bounded, gives the contraction.  
