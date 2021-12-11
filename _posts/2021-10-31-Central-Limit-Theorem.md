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
where $$ y \in \mathcal{X} $$ is in the sample set (all possible outcome of n toss), or notice the fact that

$$ n * Var (X) 
= \sum_{i=0}^{n} (x_i-\mu)^2 = \sum_{i=0}^{n} (x_i)^2 - 2\mu \sum_{i=0}^{n} x_i + \sum_{i=0}^{n} (\mu)^2
= \sum_{i=0}^{n} (x_i)^2 - 2n(\mu)^2 + n(\mu)^2
= \sum_{i=0}^{n} (x_i)^2 - n(\mu)^2 $$. 

Therefore, $$ Var (X) = \frac{\sum_{i=0}^{n} (x_i)^2}{n} - \frac{\mu^{2}}{n} = \mathbb{E} (X^2) - \left( \mathbb{E} (X) \right)^{2} $$,
this reduces to find the expected value of $$ \mathbb{E} (X^2) $$. **AN IMPORTANT THING TO NOTE HERE IS THAT**, Given $$X = \sum_{i=0}^{n} x_i$$ ,
$$ \mathbb{E} (X^2) = \frac{\sum_{i=0}^{n} x_i^2}{n} $$, while $$ \mathbb{E} (X^2) \neq \frac {\left( \sum_{i=0}^{n} x_i \right)^2}{n} $$. Indeed the reason is $$x_{i}$$ are independent, i.e. given the same sample pool, no matter how many times you choose or test, the state of the next one is still unknown except for the mean and standard derivation: you never know what the next chocolate tastes, as long as it's purely random pool, for example, the pool from [Charlie's Chocolate Factory](https://en.wikipedia.org/wiki/Charlie_and_the_Chocolate_Factory_(film)), which is impossible in reality anyway ;) 

By direct definition, 
$$ Var (X) = \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} (k-\mu)^{2}
= \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} k^2 - \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} 2npk + \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} n^2 p^2 
= np \sum_{k=1}^{n} \binom{n-1}{k-1} p^{k-1} q^{(n-1)-(k-1)} ((k-1)+1) - 2 n^2 p^2 \sum_{k=1}^{n} \binom{n-1}{k-1} p^{k-1} q^{(n-1)-(k-1)} + \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} n^2 p^2
= n(n-1)p^2 \sum_{k=2}^{n} \binom{n-2}{k-2} p^{k-2} q^{(n-2)-(k-2)} + np \sum_{k=1}^{n} \binom{n-1}{k-1} p^{k-1} q^{(n-1)-(k-1)} - 2 n^2 p^2 \sum_{k=1}^{n} \binom{n-1}{k-1} p^{k-1} q^{(n-1)-(k-1)} + \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} n^2 p^2
= n(n-1)p^2 \sum_{t=0}^{n-2} \binom{n-2}{t} p^{t} q^{(n-2)-t} + np \sum_{t=0}^{n-1} \binom{n-1}{t} p^{t} q^{(n-1)-t} - 2 n^2 p^2 \sum_{t=0}^{n-1} \binom{n-1}{t} p^{t} q^{(n-1)-t} + \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} n^2 p^2
= n(n-1)p^2 (p+q)^{n-2} + np(p+q)^{n-1} - 2 n^2 p^2 (p+q)^{n-1} + n^2 p^2 (p+q)^{n}
= n(n-1)p^2 + np - 2n^2 p^2 + n^2 p^2
= np - np^2 = np(1-p) = npq \blacksquare$$

Alternatively,
$$ Var (X) = \sum_{k=0}^{n} \binom{n}{k} p^{k} q^{n-k} k^2 - \left( \sum_{k=0}^{n} \binom{n}{k} p^k q^{n-k} * k \right)^2
= np \sum_{k=0}^{n} \binom{n-1}{k-1} p^{k-1} q^{(n-1)-(k-1)} ((k-1)+1) - (np)^2
= np \sum_{k=1}^{n} \binom{n-1}{k-1} p^{k-1} q^{(n-1)-(k-1)} (k-1) + np \sum_{k=1}^{n} \binom{n-1}{k-1} p^{k-1} q^{(n-1)-(k-1)} - (np)^2
= n(n-1)p \sum_{k=2}^{n} \binom{n-2}{k-2} p^{k-1} q^{(n-1)-(k-1)} + np \sum_{k=1}^{n} \binom{n-1}{k-1} p^{k-1} q^{(n-1)-(k-1)} - (np)^2
= n(n-1)p^2 \sum_{k=2}^{n} \binom{n-2}{k-2} p^{k-2} q^{(n-2)-(k-2)} + np \sum_{t=0}^{n-1} \binom{n-1}{t} p^{t} q^{(n-1)-t} - (np)^2
= n(n-1)p^2 \sum_{t=0}^{n-2} \binom{n-2}{t} p^{t} q^{(n-2)-t)} + np (p+q)^{n-1} - (np)^2
= n(n-1)p^2 (p+q)^{n-2} + np (p+q)^{n-1} - (np)^2
= np(1-p) = npq \blacksquare $$



For the Gaussian distribution example, we have the classical white noise graph, or ![bean machine]({{ site.baseurl }}/images/normal.jpg "an image title")
There was saying that normal distribution was invented from study of coefficients of binomial expansion, check stirling's approximation for more info.

Suppose we start with the random variable X with $$ \mathbb{E} (X) = \mu $$ and
$$ Var (X) = \sigma $$, and let $$ Z = \frac{X-\mu}{\sigma} $$ be the new random variable, since $$ E (Z) = E(\frac{X}{\sigma}) - \frac{\mu}{\sigma} 
= 0 $$, but how to calculate $$ Var(Z) $$ or $$ \mathbb{E} (X^2) $$ then?

We introduce the idea of probability density function here, $$\frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-\frac{(x-\mu)^2}{2 \sigma^2}) \, dx$$ 
This is the density function which defined at any real point, that is, the result of the integral is 1. The trick to prove is first consider this integral,
$$ I = \int\limits_{-\infty}^{\infty} exp(-x^2) \, dx $$, if we start with integration by parts, we would have 
$$ I = \int\limits_{-\infty}^{\infty} exp(-x^2) \, dx = x exp^{-x^2} |_{-\infty}^{\infty} - \int\limits_{-\infty}^{\infty} -2x^2 exp(-x^2) \, dx
= \frac 23 \int\limits_{-\infty}^{\infty} exp(-x^2) \, dx^3 
= \frac 23 x^3 exp^{-x^2} |_{-\infty}^{\infty} - \frac 23 \int\limits_{-\infty}^{\infty} -2x^4 exp(-x^2) \, dx  
= \frac{4}{15} \int\limits_{-\infty}^{\infty} exp(-x^2) \, dx^5 
= \frac{4}{15} x^5 exp^{-x^2} |_{-\infty}^{\infty} - \frac{4}{15} \int\limits_{-\infty}^{\infty} -2x^4 exp(-x^2) \, dx 
= \frac{8}{105} \int\limits_{-\infty}^{\infty} exp(-x^2) \, dx^7
= \frac{8}{105} x^7 exp^{-x^2} |_{-\infty}^{\infty} + \frac{16}{945} \int\limits_{-\infty}^{\infty}  exp(-x^2) \, dx^9
= \dots
$$  

This would continues forever and seems not wise to do the partial sum anymore, and the trick is to consider the square of $$ I $$, notice there's
an injective isomorphism $$ (x, \, y) \longmapsto (r, \, \theta) $$, where $$ -\infty < x < \infty$$, $$ -\infty < y < \infty$$, and $$ 0 \leq r < \infty $$, 
$$ 0 \leq \theta \leq 2\pi$$. i.e. This map is 1-1 and onto, to make it simpler, every point in the real plane can be parameterized by radius and angle, besides 
this representation is unique. 
$$ I^2 = \left( \int\limits_{-\infty}^{\infty} exp(-x^2) \, dx \right) * \left( \int\limits_{-\infty}^{\infty} exp(-y^2) \, dy \right)  
= \int\limits_{-\infty}^{\infty} \int\limits_{-\infty}^{\infty} exp(-(x^2+y^2)) \, dx \, dy 
= \int\limits_{0}^{\infty} \int\limits_{0}^{2\pi} exp(-r^2) \, r \, dr \, d\theta
= \int\limits_{0}^{2\pi} \frac{-1}{2} e{-x^2} |_{0}^{\infty}
= \pi
$$ 

Note the geometric meaning of this integral is the volume of the enclosed object with height of $$exp(-x^2)$$, and this volume is bounded (not infinity),  
hence, we have the small division of area (this's how we are dividing the whole plane) $$r \, dr \, d\theta $$ and take a loop of $$ 2\pi $$; The other 
explanation is via determinant of jacobian matrix.

So the integral of density function on the real line is 1, which is the total probability: 
$$ \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-\frac{(x-\mu)^2}{2 \sigma^2}) \, dx
= \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-(\frac{x-\mu}{\sqrt{2} \sigma})^2) \, dx
= \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-t^2) \, \sqrt{2} \sigma \, du
= \frac{1}{\sqrt{\pi}} I
= 1
$$

And for mean, we are integrating the density function at some point multiply with value at this point, i.e. the distribution of x. 
$$ \mathbb{E} (X) = \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-\frac{(x-\mu)^2}{2 \sigma^2}) \, x dx
= \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-(\frac{x-\mu}{\sqrt{2} \sigma})^2) \, x dx
= \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-t^2) \, (\sqrt{2} \sigma t+\mu) \sqrt{2} \sigma \, du
= \frac{\sqrt{2} \sigma}{\sqrt{\pi}} \int_{-\infty}^{\infty} e^{-t^2} \, t \, dt + \frac{1}{\sqrt{\pi}} \int_{-\infty}^{\infty} exp(-t^2) \mu \, dt
= \frac{-\sigma}{\sqrt{2\pi}} e^{-t^2}|_{-\infty}^{\infty} + \frac{1}{\sqrt{\pi}} \int_{-\infty}^{\infty} exp(-t^2) \mu \, dt
= 0 + frac{\sqrt{\pi} \mu}{\sqrt{\pi}} = \mu
$$

For variance we're integrating density function times difference between local value and the mean, so
$$ Var (X) = \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-\frac{(x-\mu)^2}{2 \sigma^2}) \, (x-\mu)^2 \, dx
= \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-(\frac{(x-\mu)}{\sqrt{2} \sigma})^2) \, x^2 dx - \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-(\frac{(x-\mu)}{\sqrt{2} \sigma})^2) \, x^2 dx + \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-(\frac{(x-\mu)}{\sqrt{2} \sigma})^2) \, \mu^2 dx
= \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-t^2) \, \sqrt{2} \sigma du
= \frac{1}{\sqrt{\pi}} I
= 1
$$

The Poisson Distribution is an application of taylor's series, since we have to ensure the distribution is 1, the probability density function of poisson 
distribution is $$ Pr(X=k) = e^{-\lambda} \frac{\lambda^k}{k!}$$, where the occurence of k is confined to non-negative integer, since
$$ e^{-\lambda} = 1 - x + \frac{1}{2!} \lambda^2 + .. + \frac{1}{n!} (-\lambda)^n + ...$$, so the cumulative density function equal to 1 is well defined. 

The mean of gaussian distribution is $$\mathbb{E}(X) = \sum_{k=0}^{\infty} e^{-\lambda} \frac{\lambda^k}{k!} * k = \lambda \sum_{k=1}^{\infty} e^{-\lambda} \frac{\lambda^(k-1)}{(k-1)!} = \lambda$$. 

The variance of poisson distribution is $$Var(X) = \sum_{k=0}^{\infty} e^{-\lambda} \frac{\lambda^k}{k!} * (k-\lambda)^2
= \sum_{k=0}^{\infty} e^{-\lambda} \frac{\lambda^k}{k!} * k^2 - \sum_{k=0}^{\infty} e^{-\lambda} \frac{\lambda^k}{k!} *2k \lambda +\lambda^2
= \sum_{k=1}^{\infty} e^{-\lambda} \frac{\lambda^k}{(k-1)!} * ((k-1)+1) - 2\lambda^2 \sum_{k=1}^{\infty} e^{-\lambda} \frac{\lambda^(k-1)}{(k-1)!} + \lambda^2   
= \lambda^2 \sum_{k=2}^{\infty} e^{-\lambda} \frac{\lambda^(k-2)}{(k-2)!} + \lambda \sum_{k=1}^{\infty} e^{-\lambda} \frac{\lambda^(k-1)}{(k-1)!} - 2\lambda^2 \sum_{k=1}^{\infty} e^{-\lambda} \frac{\lambda^(k-1)}{(k-1)!} + \lambda^2
= \lambda^2+\lambda-2\lambda^2+\lambda^2 = \lambda
$$. 

## Central Limit Theorem and Sample Variance
The following statement about central limit theorem in statistics:

Given one kind of random variable X, with mean $$\mu$$ and standard deviation $$\sigma$$, then if we pick n such samples, 
the mean of these sample would be $$\mu$$ and the variance of these samples should be $$\frac{\mu}{\sqrt{n}}.$$

Although not explicitly stated, we are assuming the paobability density function of X obeys Gaussian distribution, and the reason is the density function is symmetric with respect to the mean value. The mean is intuitively direct to understand: consider a simple example, soccer balls produced by the same pipline (thus identical) with same expected weight m, and expected variance $$\sigma^2$$, then as we choose to test more and more soccer balls, the average weight converges to m by [Large Number Theorem](https://en.wikipedia.org/wiki/Law_of_large_numbers). The variance  

The probability density function is \[ \frac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^{\infty} exp(-(\frac{(x-\mu)^2}{2 \sigma^2})) \, dx = 1. \]
Note if we denote the integral $$\int_{-\infty}^{\infty} exp() \, dx $$



{% comment %} 
\\[ x_{1,2} = \frac{-b \pm \sqrt{b^2-4ac}}{2b} \\].


\\[ a_1 = x \\]
\\[ &= x+y \\]
\\[ &= \mu \\]
\\[ &= \frac{z^2}{c} \\]

    These commments will not include inside the source.
## MaxWell Equation

equation | description
----------|------------
$$\nabla \cdot \vec{\mathbf{B}}  = 0.$$ | divergence of $$\vec{\mathbf{B}}.$$ is zero
$\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t}  = \vec{\mathbf{0}}$ |  curl of $\vec{\mathbf{E}}$ is proportional to the rate of change of $\vec{\mathbf{B}}$
$\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} = \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} = 4 \pi \rho$ | _wha?_
{% endcomment %}
