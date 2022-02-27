---
title: "Connected Graph"
---

Q: If there're N nodes, What is the minimum number of edges to make all Nodes connected? 

A: We need at least N-1 edges, and at most $$\bio(N,2)$$ edges.

Q: Still N nodes, with K edges, but what is the minimum number of edges to add to connect all Nodes?

A: We need to find

Explore Thinking: How to find exactly all pairs of edges to reconnect to make graph connected?

A: Idea is to find the connected parts where 



```cpp

```



Explore Thinking: How to find the distance between any pairs of nodes?

Dijkstra Approach, if there's any middle node to recalculate the distance between any two nodes, add it!

```cpp

```

[Number of Operations to Make Network Connected](https://leetcode.com/problems/number-of-operations-to-make-network-connected/)
