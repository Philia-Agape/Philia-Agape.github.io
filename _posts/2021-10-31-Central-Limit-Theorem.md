---
Title: Central Limit Theorem
---

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.css" integrity="sha384-R4558gYOUz8mP9YWpZJjofhk+zx0AS11p36HnD2ZKj/6JR5z27gSSULCNHIRReVs" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.js" integrity="sha384-z1fJDqw8ZApjGO3/unPWUPsIymfsJmyrDVWC8Tv/a1HeOtGmkwNd/7xUS0Xcnvsx" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/contrib/auto-render.min.js" integrity="sha384-+XBljXPPiv+OzfbB3cVmLHf4hdUFHlWNZN5spNQ7rmHTXpd7WvJum6fIACpNNfIR" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
 
## Binomial, Gaussian, Poisson distribution
These are three most-frequent statistical distribution, let's briefly discuss each one.
For Binomial distribution, it originates from the flip coin example: once you flip the coin, the possible outcome would
be either head or tail, and a uniform coin would have fifty-fifty chance, namely 
\\[\ p = P(head,\ one \ toss) = 0.5 \ and \ q = P(tail, \ one \ toss) = 0.5 = 1-p \\]. 

In general, Given n trial of one Binomial random variable, say $$ X = \sum_{i=1}^{n} x_i $$ 

where $$ E (x_i) = 1 * p + 0 * q = p $$, $$ Var (x_i) = p * (1-\mu)^{2} + q*(0-\mu)^{2} = p * (1-p)^2 + (1-p) * p^2 = p-p^2 = p(1-p) = pq $$

The expected value (mean) of X is $$ E (X) = \sum_{k=0}^{n} \binom{n}{k} p^k q^{n-k} * k =  
\sum_{k=1}^{n} n * \binom{n-1}{k-1} p * p^{k-1} q^{(n-1)-(k-1)} = np \sum_{t=0}^{n-1} \binom{n-1}{t} p^{t} q^{(n-1)-t} 
= np (p+q)^{n-1} = np $$, 

The variance of X can be calculated in two ways: directly from definition $$ Var(X) = \sum_{y} P(y)(\mathbb{E}(y)-\mu)^2 $$
where $$ y \in \mathcal{X} $$ is in the sample set (all possible outcome of n toss),

or notice the fact that $$ n * Var (X) 
= \sum_{i=0}^{n} (x_i-\mu)^2 = \sum_{i=0}^{n} (x_i)^2 - 2\mu \sum_{i=0}^{n} x_i + \sum_{i=0}^{n} (\mu)^2
= \sum_{i=0}^{n} (x_i)^2 - 2n(\mu)^2 + n(\mu)^2
= \sum_{i=0}^{n} (x_i)^2 - n(\mu)^2 $$, 

Therefore, $$ Var (X) = \frac{\sum_{i=0}^{n} (x_i)^2}{n} - \frac{\mu^{2}}{n} = \mathbb{E} (X^2) - \left( \mathbb{E} (X) \right)^{2} $$,
this reduces to find the expected value of $$ \mathbb{E} (X^2) $$.

By direct definition, $$ Var (X) = \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} (k * (1-\mu)^{2} + (n-k) * (0-\mu)^2)
= \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} (kn^2 p^2 - 2knp + k + n^3 p^2 - kn^2 p^2) 
= \sum_{k=0}^{n} \binom{n}{k} k * p^{k} q^{n-k} (1-2np) + \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} n^3 p^2
= np(1-2np) \sum_{k=1}^{n} \binom{n-1}{k-1} p^{k-1} q^{(n-1)-(k-1)} + n^3 p^2 \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} 
= np(1-2np) \sum_{t=0}^{n-1} \binom{n-1}{t} p^{t} q^{(n-1)-t)} + n^3 p^2 \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k}
= np(1-2np)(p+q)^{n-1} + n^3 p^2 (p+1)^n
= np - 2n^2 p^2 + n^3 p^2
= np(1-2np+n^2 p)
= npq $$

Alternatively, $$ Var (X) = \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} k^2 - \left( \sum_{k=0}^{n} \binom{n}{k} p^k q^{n-k} * k \right)^2
= n \sum_{k=0}^{n} \binom{n-1}{k-1} p^{k} q^{n-k} () + (np)^2
$$

Then, 
$$
(x+z)+t & = x+(z+t)

& = x+0_V 

& = x \ 
$$

For the Gaussian distribution, we have the classical white noise graph, and we start with the random variable $$ \mathbb{E} (X) = \mu $$ and
$$ Var (X) = \sigma $$, and let $$ Z = \frac{X-\mu}{\sigma} $$ be the new random variable, since $$ E (Z) = E(\frac{X}{\sigma}) - \frac{\mu}{\sigma} 
=  $$

## Central Limit Theorem and Sample Variance
The following statement about central limit theorem in statistics:

Given one kind of random variable X, with mean $$\mu$$ and standard deviation $$\sigma$$, then if we pick n such samples, 
the mean of these sample would be $$\mu$$ and the variance of these samples should be $$\frac{\mu}{\sqrt{n}}.$$

Note at this moment the CNT

The mean is intuitively direct to understand, let's recall first the derivation of mean and variance of gaussian distribution.
The probability density function is \[ \frac{1}{\sigam \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-(\frac{x-\mu}{\sqrt{2}\sigma})) \, dx = 1. \]
Note if we denote the integral $$\int_{-\infty}^{\infty} exp() \, dx

\\[ x_{1,2} = \frac{-b \pm \sqrt{b^2-4ac}}{2b} \\].


## MaxWell Equation

equation | description
----------|------------
$$\nabla \cdot \vec{\mathbf{B}}  = 0.$$ | divergence of $$\vec{\mathbf{B}}.$$ is zero
$\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t}  = \vec{\mathbf{0}}$ |  curl of $\vec{\mathbf{E}}$ is proportional to the rate of change of $\vec{\mathbf{B}}$
$\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} = \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} = 4 \pi \rho$ | _wha?_
