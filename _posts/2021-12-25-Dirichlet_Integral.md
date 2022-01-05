---
Title: Leibniz integral rule
Layout: Post
---

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.css" integrity="sha384-R4558gYOUz8mP9YWpZJjofhk+zx0AS11p36HnD2ZKj/6JR5z27gSSULCNHIRReVs" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.js" integrity="sha384-z1fJDqw8ZApjGO3/unPWUPsIymfsJmyrDVWC8Tv/a1HeOtGmkwNd/7xUS0Xcnvsx" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/contrib/auto-render.min.js" integrity="sha384-+XBljXPPiv+OzfbB3cVmLHf4hdUFHlWNZN5spNQ7rmHTXpd7WvJum6fIACpNNfIR" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
 
##Dirichlet Integral

Consider the integral $$ \int_{0}^{\infty} \frac{sinx}{x} dx$$, first we need to check it's bounded, i.e. the value exist as the result of an improper integral. 
As x approaches to zero, $$\lim_{x\to 0} \frac{sinx}{x} = \lim_{x\to 0} \frac{cosx}{1} = 1$$, $$ \[ \lim_{x\to\infty} f(x) \] $$ by L'hospital rule, and As x approaches to $$\infty$$, 
$$\lim_{x\to \infty} \frac{sinx}{x} < \lim_{x\to \infty} \frac{|sinx|}{x} < \lim_{x\to \infty} \frac{1}{x} = 0$$, so the function beheaves well at both sides,
but it's not sufficient to ensure it's converging though, we need to think of the partial sum.  

The trick here is to multiply the function with $$ e^{-bx}$$ then do the integral, say $$ I(b,x) = \int_{0}^{\infty} e^{-bx} \frac{sinx}{x} \, dx$$, which is 
actually called [Laplace Transform](https://en.wikipedia.org/wiki/Laplace_transform), anyway, if we take partial derivative of $$I(b,x)$$ with respect to b, say 
$$ \frac{\partial I(b,x)}{\partial b} = \int_{0}^{\infty} \frac{\partial e^{-bx}}{\partial b} \frac{sinx}{x} \, dx 
= \int_{0}^{\infty} \frac{\partial e^{-bx}}{\partial b} \frac{sinx}{x} \, dx
= \int_{0}^{\infty} e^{-bx} \, (-sinx) \, dx$$
When $$ b = 0$$, $$ \frac{\partial I(b,x)}{\partial b} |_{b=0} = I'(0,x) = \int_{0}^{\infty} e^{-bx} \, (-sinx) \, dx $$

Solving for $$ I'(b,x) = \int_{0}^{\infty} e^{-bx} \, (-sinx) \, dx = \int_{0}^{\infty} e^{-bx} \, d(cosx) 
= cosx * e^{-bx} |_{0}^{\infty} - \int_{0}^{\infty} cosx de^{-bx} 
= -1 
$$

Consider the $$ $$


https://en.wikipedia.org/wiki/Dirichlet_integral
https://en.wikipedia.org/wiki/Poisson_kernel
https://en.wikipedia.org/wiki/Littlewood%E2%80%93Paley_theory
