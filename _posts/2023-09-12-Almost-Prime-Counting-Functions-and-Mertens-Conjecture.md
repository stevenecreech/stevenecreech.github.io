---
layout: post
title: "Almost Prime Counting Functions and Merten's Conjecture"
date: 2023-09-12
---

$$\textbf{Abstract:}$$ The goal of this blog post is to discuss and derive a formula for the number of $$k$$-almost primes less than a given value $$x$$. We shall do this for both in the general and square-free case, and we will relate the square-free case to Merten's conjecture.

<h1>Introduction</h1>

Given a positive integer $$n>1$$, we have that $$n$$ has a prime factorization given by 

$$
n=\prod_{i=1}^rp_i^{a_i}
$$

We recall that the function $$\Omega(n):=\sum_{i=1}^r a_i$$ counts the number of prime factors of $$n$$ (with multiplicity). We define a $$k$$-almost prime to be a number $$n$$ such that $$\Omega(n)=k$$. We note that a $$1$$-almost prime is just a prime number while a $$2$$-almost prime is known as a semiprime. We remark that Conway also referred to these as primes, biprimes, triprimes, quadprimes, and so on. Now we wish to have a generalization of the prime counting function, $$\pi(x)=\#\{n\leq x: n \text{ is prime}\}$$, so we define the $$k$$-almost prime counting function to be 

$$
\pi_k(x)=\#\{n\leq x:\Omega(n)=k\}.
$$

Thus, we have that $$\pi_k(x)$$ just counts the number of $$k$$-almost primes less than $$x$$. We will also define the related square-free $$k$$-almost prime counting function as

$$
\pi_k^*(x)=\#\{n\leq x:\Omega(n)=k, n\text{ is square-free}\}.
$$

We remark the subtle difference between $$\pi_k$$ and $$\pi_k^*$$ by observing that $$\pi_2(6)=2$$ while $$\pi_2^*(6)=1$$. Since we have that $$4,6$$ are the two semiprimes less than or equal to $$6$$, but $$6$$ is the only square-free semiprime less than $$6$$ as we don't count $$4$$. Thus, another way of viewing $$\pi_k^*(x)$$ is to count the number of positive integers $$n$$ less than $$x$$ with prime factorization $$n=\prod_{i=1}^kp_i$$ where $$p_i\neq p_j$$ for $$i\neq j$$. 

Now the goal will be to give a recursive formula for $$\pi_k(x)$$ and $$\pi_k^*(x)$$. We shall first state the formula for semiprimes as the following theorems. We note that the formula for $$\pi_2(x)$$ was given by R.G. Wilson in 2006 and E. Noel and G. Panos in 2005 <a href = "https://mathworld.wolfram.com/Semiprime.html">(see this note)</a>; however, neither result was published and was only given in a correspondence. Furthermore, I was unable to find a proof of the formula written down anywhere, so we will provide one here. 

$$\textbf{Theorem 1:}$$Let us denote $$p_k$$ to be the $$k$$-th prime number, then the number of semiprimes less than a given value $$x$$ whose smallest prime factor is $$p_j$$ is given by the formula:

$$
\sum_{k=i}^{\pi(\sqrt{x})}\left(\pi\left(\frac{x}{p_k}\right)-k+1\right)
$$

Similarly, the number of square-free semiprimes less than a given value $$x$$ whose smallest possible prime factor is $$p_j$$ is given by the formula:

$$
\sum_{k=j}^{\pi(\sqrt{x})}\left(\pi\left(\frac{x}{p_k}\right)-k\right)
$$

In particular, setting $$j=1$$, we get the following formulas for the number of semiprimes and square-free semiprimes less than a given value $$x$$:

$$
\pi_2(x)=\sum_{k=1}^{\pi(\sqrt{x})}\left(\pi\left(\frac{x}{p_k}\right)-k+1\right)
$$

$$
\pi_2^*(x)=\sum_{k=1}^{\pi(\sqrt{x})}\left(\pi\left(\frac{x}{p_k}\right)-k\right)
$$

We shall then prove the more general form of these statements for $$k$$-almost primes. I will note that the statement for the $$3$$-almost prime case I found a solution in the following <a href = "https://math.stackexchange.com/questions/1129118/counting-squarefree-3-almost-primes-solved">StackExchange post</a>, and one should remark that square-free $$3$$-almost primes are known as sphenic numbers, and the StackExchange post gives a formula to count them. The hard part in this tends to be the jump from $$2$$ to $$3$$, so our below theorem just continues the ideas encapsulated in the $$3$$-almost prime formula into the $$k$$-almost prime case. Furthermore, I will note that although the proofs aren't too difficult, I again was unable to find them written out anywhere, so we shall provide the proof. 

$$\textbf{Theorem 2:}$$ With the same notation as above, we have the following formulas for the $$k$$-almost primes less than a given value $$x$$ whose smallest prime factor is $$p_j$$:

$$
\begin{equation}
\pi_k(x)=\sum_{i_1=j}^{\sqrt[k]{x}}\sum_{i_2=i_1}^{\pi\left(\sqrt[k-1]{\frac{x}{p_{i_1}}}\right)}...\sum_{i_{k-1}=i_{k-2}}^{\pi\left(\sqrt{\frac{x}{p_{i_1}p_{i_2}...p_{i_{k-2}}}}\right)}\left(\pi\left(\frac{x}{p_1p_2...p_{k-1}}\right)-i_{k-1}+1\right)
\end{equation}
$$

Similarly, we have that the formula for the number of square-free $$k$$-almost primes less than a given value $$x$$ whose smallest prime factor is $$p_j$$ is given by:

$$
\begin{equation}
\pi_k^*(x)=\sum_{i_1=j}^{\sqrt[k]{x}}\sum_{i_2=i_1+1}^{\pi\left(\sqrt[k-1]{\frac{x}{p_{i_1}}}\right)}...\sum_{i_{k-1}=i_{k-2}+1}^{\pi\left(\sqrt{\frac{x}{p_{i_1}p_{i_2}...p_{i_{k-2}}}}\right)}\left(\pi\left(\frac{x}{p_1p_2...p_{k-1}}\right)-i_{k-1}\right)
\end{equation}
$$

In particular, setting $$j=1$$ gives us the formula for the number of $$k$$-almost primes and square-free $$k$$-almost primes less than a given value $$x$$:

$$
\begin{equation}
\pi_k(x)=\sum_{i_1=1}^{\sqrt[k]{x}}\sum_{i_2=i_1}^{\pi\left(\sqrt[k-1]{\frac{x}{p_{i_1}}}\right)}...\sum_{i_{k-1}=i_{k-2}}^{\pi\left(\sqrt{\frac{x}{p_{i_1}p_{i_2}...p_{i_{k-2}}}}\right)}\left(\pi\left(\frac{x}{p_1p_2...p_{k-1}}\right)-i_{k-1}+1\right)
\end{equation}
$$

$$
\begin{equation}
\pi_k^*(x)=\sum_{i_1=1}^{\sqrt[k]{x}}\sum_{i_2=i_1+1}^{\pi\left(\sqrt[k-1]{\frac{x}{p_{i_1}}}\right)}...\sum_{i_{k-1}=i_{k-2}+1}^{\pi\left(\sqrt{\frac{x}{p_{i_1}p_{i_2}...p_{i_{k-2}}}}\right)}\left(\pi\left(\frac{x}{p_1p_2...p_{k-1}}\right)-i_{k-1}\right)
\end{equation}
$$

After proving these formulas, we shall relate these ideas to Merten's conjecture by giving a formula for Merten's function in terms of the square-free $$k$$-almost prime counting functions. 

<h1>The Semiprime Case</h1>

Now we shall give a proof of Theorem 1 for the formula for (square-free) semiprimes. Then we shall remark how we can then see the formula for the number of (square-free) semiprimes whose smallest possible prime factor is $$p_i$$.

We shall do this by simply counting the number of semiprimes less than $$x$$. To do this we begin by remarking that the largest possible prime factor of a semiprime less than $$x$$ can be $$\sqrt{x}$$. Thus, we will have $$\pi(\sqrt{x})$$ different possible prime factors. Now for each prime $$p_k\in\{p_1,...,p_{\pi(\sqrt{x})}\}$$, we claim that there are $$\pi\left(\frac{x}{p_k}\right)-k+1$$ semiprimes less than $$x$$ whose smallest prime factor is $$p_k$$. To see this we remark that $$\pi\left(\frac{x}{p_k}\right)$$ counts the number of primes less than or equal to $$\frac{x}{p_k}$$, and for such a prime $$q$$ we will have that $$qp_k$$ is a semiprime less than or equal to $$x$$. However, we want to only count those whose smallest prime factor is $$p_k$$, as there are $$k-1$$ primes less than $$p_k$$, we conclude that there are exactly $$\pi\left(\frac{x}{p_k}\right)-k+1$$ semiprimes less than or equal to $$x$$ having $$p_k$$ as the smallest prime factor. Thus, we conclude the first formula of theorem $$1$$ by observing that we are just summing over all possible prime factors which can divide a semiprime less than or equal to $$x$$. Similarly, we conclude the second formula of theorem $$1$$ by seeing that $$\pi\left(\frac{x}{p_k}\right)-k$$ will count the number of square-free semiprimes less than or equal to $$x$$ having $$p_k$$ as the smallest prime factor. This gives us theorem $$1$$.

Now we remark that the formula for the number of (square-free) semiprimes whose smallest prime factor is $$p_i$$ follows by the exact same counting method as above, but since the smallest prime factor is $$p_i$$ we then must start our sum at the value $$i$$ rather than $$1$$. 


<h1>The General k-almost Prime Case</h1>

We shall now give a proof of the general $$k$$-almost prime case. Let us begin with the $$k$$-almost prime case. We shall do this via induction on $$k$$ together with the observation that 

Now for the square-free case, we 

<h1>Connection to Merten's Conjecture and Riemann Hypothesis</h1>

Now in this last section, we will relate the square-free $$k$$-almost prime counting function to Merten's conjecture (and hence the Riemann hypothesis). We begin by recalling some basic definitions. We have that the Möbius function, $$\mu(n)$$, is defined to be 

$$
\mu(n)=\begin{cases}
1 & n=1\\
(-1)^{\Omega(n)} & n\text{ is square-free}\\
0 & \text{otherwise}
\end{cases}
$$
Then we have that Merten's function, $$M(x)$$, is the running sum over the Möbius function that is 
$$
M(x)=\sum_{n\leq x}\mu(n)
$$
Merten originally conjectured that $$\vert M(x)\vert\leq \sqrt{x}$$. However, it was disproven by Odlyzko and Riele in 1984 <a href="https://www-users.cse.umn.edu/~odlyzko/doc/arch/mertens.disproof.pdf">(see this paper)</a>. Although, the weaker statement of $$M(x)=O(x^{\frac{1}{2}+\epsilon})$$ for any $$\epsilon>0$$ is still an open problem (which is equivalent to the Riemann hypothesis). Now we have the following relationship between Merten's conjecture and the square-free $$k$$-almost prime counting functions we state it as the following theorem. 

$$\textbf{Theorem 3:}$$ We let $$\delta_{x\geq 1}$$ to be the function that is $$1$$ if the input is greater than or equal to $$1$$ and $$0$$ otherwise, then we have the following 

$$
M(x)=\delta_{x\geq 1}(x)+\sum_{k=1}^\infty(-1)^{k+1}\pi_k^*(x)
$$
Furthermore, we remark that the sum is actually a finite sum since we will have that $$\pi_k^*(x)=0$$ for all $$k\geq \log_2(x)$$ since the first $$k$$-almost prime is $$2^k$$. We note that as we are counting square-free $$k$$-almost primes there is a better bound for the upper index of the sum; however, such a bound is a bit harder to describe in concise mathematical notation. In particular, the sum can end at the number $$\ell$$ which is the smallest integer such that $$p_1\cdot...\cdot p_{\ell}>x$$, we shall denote this number by $$\nu(x):=\ell$$, so we have the finite sum version of this sum is given by:

$$
M(x)=\delta_{x\geq 1}(x)+\sum_{k=1}^{\nu(x)}(-1)^{k+1}\pi_k^*(x)
$$

Now to prove this theorem, we remark that Merten's function will have that the $$\mu(1)$$ term is accounted for in the $$\delta_{x\geq 1}$$ term. Then we have that $$\mu(n)$$ will be $$-1$$ for all the primes less than $$x$$ which gives us the contribution of $$-\pi_1^*(x)$$, then continuing we will have that $$\mu(n)$$ will be $$1$$ for all the square-free semiprimes less than $$x$$ giving the contribution of $$\pi_2^*(x)$$, and continuing on with the square-free $$k$$-almost primes there will be $$\pi_k^*(x)$$ of them less than $$x$$ and for each of these the Möbius function will have the value of $$(-1)^{k+1}$$ which is how we deduce our formula for Merten's function. 

Now I shall remark that I had hoped that such a formula for Merten's function in terms of the square-free $$k$$-almost prime counting functions could help in proving the pseudo-Riemann hypothesis which asserts that there is some $$\epsilon>0$$ such that $$\zeta(s)$$ has no zeros for $$\text{Re}(s)>1-\epsilon$$. The equivalent formulation in terms of Merten's function will be that there is some $$\epsilon>0$$ such that $$M(x)=O(x^{1-\epsilon})$$. However, I am not clever enough to come up with such a proof (as one would expect it to be extremely difficult). However, I might note that we do have the following asymptotic expression for the $$k$$-almost primes (see chapter II.6 of Tenenbaum's book "Introduction to Analytic and Probabilistic Number Theory")

$$\textbf{Theorem 4:}$$ We have the following estimate for the number of $$k$$-almost primes as $$x\rightarrow \infty$$

$$
\pi_k(x)\sim \frac{x}{\log x}\frac{(\log\log x)^{k-1}}{(k-1)!}
$$

We note that the book does not give a proof for the square-free case, but one should expect that such an asymptotic to still hold in that case. This seems like a good place to finish off as it isn't entirely clear how to proceed, but I shall finish off by stating several questions that I don't know whether or not they are easy to prove or not but might be interesting food for thought for the engaged reader.

$$\textbf{Question 1:}$$ It is known that Merten's function changes signs infinitely often is it possible to give a proof of this fact by combining Theorems 3 and 4?

$$\textbf{Question 2:}$$ The asymptotic in Theorem 4 suggests that for $$x$$ large enough one might expect there to be more $$k$$-almost primes than $$\ell$$-almost primes for $$k>\ell$$, is it possible to prove this by combining Theorem 3 with the fact that Merten's function changes signs infinitely often?


