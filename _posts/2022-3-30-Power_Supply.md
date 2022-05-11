---
Title: Three_Phase_Power_Supply
---

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.css" integrity="sha384-R4558gYOUz8mP9YWpZJjofhk+zx0AS11p36HnD2ZKj/6JR5z27gSSULCNHIRReVs" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.js" integrity="sha384-z1fJDqw8ZApjGO3/unPWUPsIymfsJmyrDVWC8Tv/a1HeOtGmkwNd/7xUS0Xcnvsx" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/contrib/auto-render.min.js" integrity="sha384-+XBljXPPiv+OzfbB3cVmLHf4hdUFHlWNZN5spNQ7rmHTXpd7WvJum6fIACpNNfIR" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>

Think of the power supply nowadays in modern society almost everywhere, one of the greatest inventions from last century: No Wonder Tesla is the GOAT, the GOD of EE!

For Three-Phase Alternating Current, We would have three alternating power supply line, each with $$\frac{2\pi}{3}$$ difference to the other two supply.
Namely, $$U_{1} = U \times sin(2\pi ft)$$, $$U_{2} = U \times sin(2\pi ft + \frac{2\pi}{3})$$, and $$U_{3} = U \times sin(2\pi ft - \frac{2\pi}{3})$$, and by calculating the difference between two voltage supply, we could derive the power supply through the machine: **Instead of addition, which is the combination of wavelets, but not the power supply thorough the machine!**

Addition is confusing, since we have the fact that 
$$U_{1}+U_{2}+U_{3} = Usin(2\pi ft) - \frac{U}{2}sin(2\pi ft) + \frac{\sqrt{3}U}{2} cos(2\pi ft) - \frac{U}{2}sin(2\pi ft) - \frac{\sqrt{3}U}{2} cos(2\pi ft) 
= 0$$, 
which says at any time the voltage of three power supply sum up to zero.

Calculate the difference between two L(Live) lines, 

$$U_{1}-U_{2} 
=Usin(2\pi ft) + \frac{U}{2} sin(2\pi ft) - \frac{\sqrt{3}U}{2} cos(2\pi ft) 
=\frac{3U}{2} sin(2\pi ft) - \frac{\sqrt{3}U}{2} cos(2\pi ft) 
=\sqrt{3}U sin(2\pi ft-\frac{\pi}{6})$$; 

$$U_{2}-U_{3} 
=\frac{-U}{2} sin(2\pi ft) + \frac{\sqrt{3}U}{2} cos(2\pi ft) + \frac{U}{2} sin(2\pi ft) + \frac{\sqrt{3}U}{2} cos(2\pi ft) 
=\sqrt{3}U cos(2\pi ft) 
=\sqrt{3}U sin(2\pi ft + \frac{\pi}{2})$$; 

$$U_{3}-U_{1} 
=\frac{-U}{2} sin(2\pi ft) - \frac{\sqrt{3}U}{2} cos(2\pi ft) - U sin(2\pi ft) 
=\frac{3U}{2} sin(2\pi ft) - \frac{\sqrt{3}U}{2} cos(2\pi ft) 
=-\sqrt{3}U sin(2\pi ft+\frac{\pi}{6}) 
=\sqrt{3} U sin(2\pi ft-\frac{5\pi}{6})$$

Thus, the voltage between any two pairs of L line is theoretically, $$\sqrt{3}$$ Times the EMF of L line.

 ![3-Phase Power Supply](https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/3_Phase_Power_Connected_to_Wye_Load.svg/2560px-3_Phase_Power_Connected_to_Wye_Load.svg.png)

Explorative Thinking: What is the voltage for the center of circle in a loop circuit? Ideally each line burdens the same resistance. 
