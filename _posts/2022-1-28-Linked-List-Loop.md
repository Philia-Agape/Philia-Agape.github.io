---
layout: post
comments: true
title: "Linked List Loop"
---

LLL! Not [LL](https://www.lovelive-anime.jp/worldwide/)!

To search for the loop inside the linked list, and given the condition that we must come up with an method having O(1) space complexity.

Since recording the list is not allowed, we must use two pointers to implement our idea, just like [rabbit chasing turtle.](https://en.wikipedia.org/wiki/The_Tortoise_and_the_Hare)

Now, we assume rabbit's speed is two and turtle's is one, and later will be explained why it's convenient. They represent two pointers pointing to the beginning of the linked list, say the non-loop part, is of length x, and the loop is of length y, then we assume at the time rabbit first meets turtle, turtle has moved $$n_{1}$$ step, and rabbit has moved $$2* n_{1}$$ steps, if we assume the meeting location is $$\lambda$$ away from the starting node of the loop, and turtle has travelled $$k_{1}$$ round while rabbit has travelled $$k_{2}$$ round, i.e. $$n_{1} = x + \lambda + k_{1} * y$$ and $$2 * n_{1} = x + \lambda + k_{2} * y$$, as a result, $$x = (k_{2}-2k_{1}) * y - \lambda$$. 

What Could we derive from this equation? If the pointer has entered the loop and moves y steps, it would remain in the same position, so if the turtle starts at the location they first meet, and let the rabbit starts from the beginning, with same speed of the turtle, then the location they first meet is the starting node of the loop!

```cpp
typedef struct node{
   int val;
   struct* next;
};

```









