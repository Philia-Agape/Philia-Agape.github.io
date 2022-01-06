---
layout: post
title: Catch-Up the Power Series!
---

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.css" integrity="sha384-R4558gYOUz8mP9YWpZJjofhk+zx0AS11p36HnD2ZKj/6JR5z27gSSULCNHIRReVs" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.js" integrity="sha384-z1fJDqw8ZApjGO3/unPWUPsIymfsJmyrDVWC8Tv/a1HeOtGmkwNd/7xUS0Xcnvsx" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/contrib/auto-render.min.js" integrity="sha384-+XBljXPPiv+OzfbB3cVmLHf4hdUFHlWNZN5spNQ7rmHTXpd7WvJum6fIACpNNfIR" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
        
In case you've never heard of the classical dog chasing power series problem: Alice and Bob were seated on both ends of a line with distance $$L$$, and they 
started to run towards with velocity $$v_{a}$$, $$v_{b}$$ respectively, and a dog started from Alice's position was running bouncing forward and back between 
them with velocity $$v_{c} \geq v_{a} \, , \, v_{b}$$. How long the distance will the dog travel until Alice and Bob meet? 

If we think of the event as a whole, the total time it takes for Alice and Bob to meet will be $$ T_{tot} = \frac{L}{v_{a}+v_{b}}$$ and the distance the dog
travelled will be $$ S_{tot} = T_{tot} * v_{c} = \frac{L v_{c}}{v_{a}+v_{b}}$$.

If we do it by parts, calculate the distance for next meet-up when every time, the dog reverse its velocity, we need to do a power series addition. Think of 
the first meeting, say the distance between Bob and the dog $$ L_{0} = L$$, and the time it takes for them to meet will be 
$$t_{0} = \frac{L_{0}}{v_{b}+v_{c}} = \frac{L}{v_{b}+v_{c}}$$, and then the dog reverse its velocity to meet Alice, but now the distance between between Alice 
and the dog will be $$ L_{1} = L_{0} - (v_{a}+v_{b}) * t_{0} = L - \frac{L(v_{a}+v_{b})}{v_{b}+v_{c}} = L \frac{v_{c}-v_{a})}{v_{c}+v_{b}}$$, and the time it 
takes for Alice and dog to meet will be $$t_{1} = \frac{L_{1}}{v_{a}+v_{c}} =  $$, 

In fact, we may realize that the total distance the dog travelled $$ S = \[ \sum_{i=0}^{\infty} t_{i} \] * v_{c}$$, and the time for the dog to travel for each meeting will be $$ t_{2i} = \frac{L_{2i}}{v_{c}+v_{b}}$$ and $$ t_{2i+1} = \frac{L_{2i+1}}{v_{c}+v_{a}}$$, for even and odd cases respectively. Note if we change 
the dos's starting position it would be the converse case! Based on the formula for meeting time, we can derive the distance for each meeting, say 
$$L_{i+1} = L_{i} - (v_{a}+v_{b}) * t_{i} = L{i-1} - (v_{a}+v_{b}) * (t_{i-1}+t_{i}) = \dots = L - (v_{a}+v_{b}) * \[ \sum_{i=0}^{\infty} t_{i}]\$$. 
By induction, $$ L_{0} = L$$, $$L_{1} = L_{0} - (v_{a}+v_{b}) * t_{0} = L - L \frac{v_{a}+v_{b}}{v_{c}+v_{b}} = L \frac{v_{c}-v_{a}}{v_{b}+v_{c}}$$,
$$ L_{2} = L_{1} - t_{1} * (v_{a}+v_{b}) =  L_{1} - \frac{L_{1}(v_{a}+v_{b})}{v_{c}+v_{a}}= L_{1} \frac{(v_{c}-v_{a})(v_{c}-v_{b})}{(v_{b}+v_{c})(v_{a}+v_{c})} $$
and $$ L_{3} = L_{2} - t_{2}(v_{a}+v_{b}) = L_{2} - \frac{L_{2}(v_{a}+v_{b})}{v_{c}+v_{b}} = L \frac{(v_{c}-v_{a})^2(v_{c}-v_{b})}{(v_{b}+v_{c})^2(v_{a}+v_{c})}$$, so 
$$ t_{3} = \frac{L_{3}}{v_{c}+v_{a}} = L \frac{(v_{c}-v_{a})^2(v_{c}-v_{b})}{(v_{b}+v_{c})^2(v_{a}+v_{c})^2}$$.

By Adding this power series, we may conclude that this partial sum is approaching to the limit $$ S = \frac{v_{c}L}{v_{a}+v_{b}}$$.




