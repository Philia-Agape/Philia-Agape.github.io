---
Title: Magic Cube
---
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.css" integrity="sha384-R4558gYOUz8mP9YWpZJjofhk+zx0AS11p36HnD2ZKj/6JR5z27gSSULCNHIRReVs" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.js" integrity="sha384-z1fJDqw8ZApjGO3/unPWUPsIymfsJmyrDVWC8Tv/a1HeOtGmkwNd/7xUS0Xcnvsx" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/contrib/auto-render.min.js" integrity="sha384-+XBljXPPiv+OzfbB3cVmLHf4hdUFHlWNZN5spNQ7rmHTXpd7WvJum6fIACpNNfIR" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
    
## Classical Cube Operations as a Group 
Magic Cube or Rubik's cube was first invented by Ernő Rubik in 1970s, and it has enjoy high popularity over the past decades. It also varies a lot: from the 
most classical 3 by 3 by 3 cube to $$ n*n*n $$ cube, and many other polyhedron variations...

Back to classical Magic Cube, how to solve it then? First let's consider what types of operations can we apply? Basically, the cube allows three operations at one 
trial (90 degree): from Left to Right, from Up to Down, from Front to Back, and with inverse operation respectively. All these operations can be represented by John Ambrose Fleming's [right hand rules](https://en.wikipedia.org/wiki/John_Ambrose_Fleming) uniquely as well.

Let's label each operation, say U the rotate the first layer (negative Z axis orientation by right hand rule) of cube by 90 degree clockwise (i.e. from right to left), what elements on the surface of cube has changed? It's the firse layer of cube: one surface (the top surface), and four edges directly connecting it. OK!
Follow this logic, we can produce three similar operations with orientation preserved: the U rotation of three layers of the cube, and by convention we call the 
clockwise 90 degree rotation of the bottom layer D: U means Up and D means Down. For the second layer, middle layer, if we apply a 90 degree negative Z axis rotation on it, it's equivalent to apply UD or DU, so we don't consider this operation. So far we've created U&D, one pair of operations. If we'd like to reverse the orientation, say counterclockwise ratation, by convention we denote it by U' and D' respectively, which is isomorphic to UUU and DDD, namely clockwise rotation by 90 degree is equivalent ot counterclockwise 270 degree; Also, by convention, we denote rotation in Z-axis by 180 degree by $$ U^2 $$ and $$ D^2 $$.

Remember there're three orientations, and by convention, we say R is the rotation of right side by 90 degree clockwise with positive Y-axis orientation, while L is the rotation of left side by 90 degree with negative Y-axis orientation, and F is the rotation of front side by 90 degree clockwise with positive X-axis orientation, while B is the rotation of left side by 90 degree with negative Y-axis orientation

Therefore, we say $$\mathbb{G} = \{U, \, D, \, L, \, R, \, F, \, B \} $$ is the generating group of all possible scrambled configuration of the cube from origin state (home). For example, U^2DL is the configuration of applying U twice and D and then L. Note so far it's a free group, just like a dictionary in which you can add words freely to create a new word, the only principle here is trivial and obvious, for example, firstly, the order of any single operation is four, namely $$ UUUU = LLLL = DDDD = RRRR = FFFF = BBBB = e$$ and $$  

[Group Theory of Rubik](http://web.mit.edu/sp.268/www/2010/rubikSlides.pdf).
[Rubik Solve](http://www.geometer.org/rubik/group.pdf).

## Solveing the cube: Thistlethwaite, Iterative_deepening_A*

The origin method contributes from [Thistlethwaite's algorithm](https://www.jaapsch.net/puzzles/thistle.htm). The algebraic structure was explained in detail by the chain of subgroup. Followed Thistlethwaite's blueprint, he consructed a chain of subgroup of the generating group $$\mathbb{G}$$, as follows:

\\[ \{L, \, R, \, F, \, B, \, U, \, D \} \trianglelefteq \{L, \, R, \, F, \, B, \, U^2, \, D^2 \} \trianglelefteq 
\{L, \, R, \, F^2, \, B^2, \, U^2, \, D^2 \} \trianglelefteq \{L^2, \, R^2, \, F^2, \, B^2, \, U^2, \, D^2 \} \trianglelefteq 
\{I\} \\]

Where $$\{I\}$$ is the identity group which means no operation, or preserve itself operation (already home!) ;)





.

It's said that there's more advanced algorithm to solve rubik, check [Iterative_deepening_A*](https://www.diva-portal.org/smash/get/diva2:816583/FULLTEXT01.pdf).
