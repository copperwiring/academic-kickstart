---
layout: post
title: "KL-Divergence"
date: 2020-01-15 12:38:00 -0700
comments: true
tags: technical
# draft: true
---

**What is KL-Divergence**
KL Divergence is a measure of how one probabilty distributon is different from another. Some people also call it the distance between two distributions, however, strictly speaking it is not the distance. Distance is commutative while KL-Divergence is not.

**Mathematically**:

$$ D\_{KL}(P||Q) = \sum_x P(X= x) log\frac{P(X=x)}{Q(X=x)} $$

$$ D\_{KL}(P||Q) = \sum_x P(X= x) log\frac{P(X=x)}{Q(X=x)} $$

where $\sum_x P(X= x)$ is the summation of all the values that random variable $X$ will take and $P(X= x)$ is the probabilty of that random variable. In short we can also write:

$$ D\_{KL}(P||Q) = \sum_x P(x) log\frac{P(x)}{Q(x)} $$

----
**How can we generalize it to two different distributions?**

Suppose we have two multivariate normal distributions defined as

$$ p(x) = N(x;p\_1, \Sigma\_1 ) $$
$$ q(x) = N(x;p\_2, \Sigma\_2 ) $$

where $N$ is the normal distribution, $p_1$ & $p\_2$ are are the means and $\Sigma\_1$ and $\Sigma\_2$ are the covariance matrix.

The multivariate normal distribution is defined as:

$$ N(x;p;\Sigma\_1) = \frac{1}{\sqrt{(2\pi)^{k} |\Sigma_1|}} * exp(- \frac{1}{2} (x-p)^{T} \Sigma^{-1}(x-p)) $$ 

if the two distributions have the same distributions. Here $x$ is the vector of length $k$ x $1$ i.e. the elements are $x= [x\_1, x\_2...x\_n]^{T}$

Now, if we have two distributions as mutivariate normal density, then KL Divergence between the two normal distributions is defined as:

$$ D\_{KL}(p(x) || q(x)) = \frac{1}{2} {  \bigg[log \frac{|\Sigma_{2}|}{|\Sigma_{1}|} - d + tr(\Sigma_2^{-1}\Sigma_1) + (p_2 - p_1)^{T} \Sigma_2^{-1}(p_2 - p_1)} \bigg] $$

**Proof**:

We know that KL Divergence between two PDFs can be expressed as:
$$ D\_{KL}(p(x) || q(x)) = \sum_x P(x) log\frac{P(x)}{Q(x)} \tag{1}  $$

and multi-variate normal distribution is defined like:
$$ N(x;p;\Sigma\_1) = \frac{1}{\sqrt{(2\pi)^{k} |\Sigma_1|}} * exp\Big[- \frac{1}{2} (x-p_1)^{T} \Sigma^{-1}(x-p_1)\Big] \tag{2}  $$

<!-- See \ref{1} for a how-to.  -->

*Note: $|\Sigma|$ is the determinant and is not the absolute value*

Taking log of Eq.$2$, we can write as:

$$ log P(x) = - \frac{k}{2}log(2\pi) - \frac{1}{2}log(|\Sigma_1|) - \frac{1}{2} \Big[(x-p_1)^{T} \Sigma^{-1}(x-p_1)\Big]  \tag{3} $$

Similarly for second probabilty distribution $Q$,
$$ log Q(x) = - \frac{k}{2}log(2\pi) - \frac{1}{2}log(|\Sigma_2|) - \frac{1}{2} \Big[(x-p_2)^{T} \Sigma^{-1}(x-p_2)\Big]  \tag{4} $$

Now, Eq.$\tag{1}$ can be re-written as:
$$ D\_{KL}(p(x) || q(x)) = \sum_x P(x) * [logP(x) - logQ(x)] \tag{5}  $$

Substituting Eq. $3$ and Eq. $4$ in Eq. $5$, we get:

<div>
$$ 
\begin{multline} 
 D_{KL}(p(x) || q(x)) = 
\sum_x P(x) *  \\
\hspace{25mm}- \Big[\frac{k}{2}log(2\pi) - \frac{1}{2}log(|\Sigma_1|) - \frac{1}{2} \Big[(x-p_1)^{T} \Sigma^{-1}(x-p_1)\Big] \Big] \\
\hspace{-20mm} \Big[- \Big[- \frac{k}{2}log(2\pi) - \frac{1}{2}log(|\Sigma_2|) - \frac{1}{2} \Big[(x-p_2)^{T} \Sigma^{-1}(x-p_2)\Big]\Big]\Big]
\end{multline} 
$$
</div>

$$ $$

<div>
$$ 
\begin{multline} 
 D_{KL}(p(x) || q(x)) = 
\sum_x P(x) *  \\
\hspace{25mm} \xcancel{-\frac{k}{2}log(2\pi)}  \boxed{- \frac{1}{2}log(|\Sigma_1|)} - \frac{1}{2} \Big[(x-p_1)^{T} \Sigma^{-1}(x-p_1) \\
\xcancel{+\frac{k}{2}log(2\pi)} \boxed{+ \frac{1}{2}log(|\Sigma_2|)} + \frac{1}{2} \Big[(x-p_2)^{T} \Sigma^{-1}(x-p_2)\Big]
\end{multline} 
$$
</div>

We can cancel out the parts that give 0, club the boxed item in one and remaining terms in one. Hence,

<div>
$$ 
\begin{multline} 
 D_{KL}(p(x) || q(x)) = 
\sum_x P(x) *  \\
\hspace{25mm}  \Bigg[ \hspace{5mm} \boxed{+ \frac{1}{2}log(\frac{|\Sigma_2|}{|\Sigma_1|})} - \frac{1}{2} \Big[(x-p_1)^{T} \Sigma^{-1}(x-p_1) \Big] + \frac{1}{2} \Big[(x-p_2)^{T} \Sigma^{-1}(x-p_2)\Big]\Bigg]\tag{6}
\end{multline} 
$$
</div>

$P(x)$ can be split for each of the terms and hence can be written as:
<div>
$$ 
\begin{multline} 
 D_{KL}(p(x) || q(x)) = 
\sum_x P(x) * \Bigg[ \hspace{5mm} \frac{1}{2}log(\frac{|\Sigma_2|}{|\Sigma_1|})\Bigg] \\
\sum_x P(x) * \Bigg[- \frac{1}{2} \Big[(x-p_1)^{T} \Sigma^{-1}(x-p_1) \Big] \Bigg] + 
\sum_x P(x) * \Bigg[ \frac{1}{2} \Big[(x-p_2)^{T} \Sigma^{-1}(x-p_2)\Big]\Bigg] \tag{7}
\end{multline} 
$$
</div>

Now let us solve the remaining terms one by one. We will start with 

$$
\sum_x P(x) * \Bigg[ \frac{1}{2} \Big[(x-p_2)^{T} \Sigma_2^{-1}(x-p_2)\Big]\Bigg] \equiv E_p\Bigg[ \frac{1}{2} \Big[(x-p_2)^{T} \Sigma_2^{-1}(x-p_2)\Big]\Bigg]
$$

Using properties of trace and expectation (Appendix -1), we can re-write:

$$
E_p\Bigg[ \frac{1}{2} \Big[(x-p_2)^{T} \Sigma_2^{-1}(x-p_2)\Big]\Bigg]
$$ as


$$
= \frac{1}{2}E_p\Bigg[ tr\Big[(x-p_2)^{T} \Sigma_2^{-1}(x-p_2)\Big]\Bigg]
= E_p\Bigg[ tr\Big[\frac{1}{2} (x-p_2)^{T} \Sigma_2^{-1}(x-p_2)\Big]\Bigg]
= E_p\Bigg[ tr\Big[\frac{1}{2}(x-p_2)(x-p_2)^{T} \Sigma_2^{-1}\Big]\Bigg] 
$$

Using propery __, we have

$$
= tr \Bigg[\hspace{3mm}\boxed{E_p \Bigg( \Bigg[(x-p_2)(x-p_2)^{T} \Bigg]} \frac{1}{2} \Sigma_2^{-1} \Bigg) \Bigg]
$$

The boxed element is nothing but a covaiance matrix $\Sigma_2$, therefore
$$
D_{KL}\Big(p(x) || q(x)\Big) =  tr \Bigg[ \Sigma_2 \frac{1}{2} \Sigma_2^{-1}] \Bigg] = tr \Bigg[ I_k \Bigg] \equiv k
$$

To be continued ...








