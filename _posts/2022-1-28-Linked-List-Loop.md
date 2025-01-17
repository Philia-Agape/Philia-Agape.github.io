---
layout: post
title: "Linked List Loop"
---

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.css" integrity="sha384-R4558gYOUz8mP9YWpZJjofhk+zx0AS11p36HnD2ZKj/6JR5z27gSSULCNHIRReVs" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.js" integrity="sha384-z1fJDqw8ZApjGO3/unPWUPsIymfsJmyrDVWC8Tv/a1HeOtGmkwNd/7xUS0Xcnvsx" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/contrib/auto-render.min.js" integrity="sha384-+XBljXPPiv+OzfbB3cVmLHf4hdUFHlWNZN5spNQ7rmHTXpd7WvJum6fIACpNNfIR" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>

[LLL](https://leetcode.com/problems/linked-list-cycle/)! Not [LL](https://www.lovelive-anime.jp/worldwide/)!

To search for the loop inside the linked list, and given the condition that we must come up with an method having O(1) space complexity.

Since recording the list is not allowed, we must use two pointers to implement our idea, just like [rabbit chasing turtle.](https://en.wikipedia.org/wiki/The_Tortoise_and_the_Hare)

Now, we assume rabbit's speed is two and turtle's is one, and later will be explained why it's convenient. They represent two pointers pointing to the beginning of the linked list, say the non-loop part, is of length x, and the loop is of length y, then we assume at the time rabbit first meets turtle, turtle has moved $$n_{1}$$ step, and rabbit has moved $$S * n_{1}$$ steps, if we assume the meeting location is $$\lambda$$ away from the starting node of the loop, and turtle has travelled $$k_{1}$$ round while rabbit has travelled $$k_{2}$$ round, i.e. $$n_{1} = x + \lambda + k_{1} * y$$ and $$n_{2} = S * n_{1} = x + \lambda + k_{2} * y$$, multiply $$n_{1}$$ by $$S$$ we obtain $$Sn_{1} = Sx + S\lambda + Sk_{1}y$$, $$(S-1)\lambda = (1-S)x + (k_{2}-Sk_{1}) * y$$, then $$\lambda = -x + \frac{k_{2}-Sk_{1}}{S-1} y$$, thus $$x = \frac{k_{2}-Sk_{1}}{S-1} y - \lambda $$ the position we want to seek, espcially when $$x = 0$$, which means the loop starts at beginning. 

What Could we derive from this equation? If the pointer has entered the loop and moves y steps, it would remain in the same position, so if the turtle starts at the location they first meet, and let the rabbit starts from the beginning, with same speed of the turtle, then the location they first meet is the starting node of the loop!

```cpp
typedef struct node{
   int val;
   struct* next;
};

class Solution {
public:
    bool hasCycle(ListNode *head) {
       if(!head || !head->next || !head->next->next) return false; 
       ListNode* rabbit = head->next->next, *turtle = head->next;
       while(rabbit != turtle){
          if(rabbit->next && rabbit->next->next) rabbit = rabbit->next->next;
          else return false; 
          turtle = turtle->next; 
       }
       turtle = head;
       while(turtle != rabbit){
          turtle = turtle->next;
          rabbit = rabbit->next; 
       } 
       printf("the node starts at %d", rabbit->val); 
       return true; 
    }
};

```









