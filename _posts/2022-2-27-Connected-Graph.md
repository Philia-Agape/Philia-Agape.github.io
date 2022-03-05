---
title: "Connected Graph"
---

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.css" integrity="sha384-R4558gYOUz8mP9YWpZJjofhk+zx0AS11p36HnD2ZKj/6JR5z27gSSULCNHIRReVs" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.js" integrity="sha384-z1fJDqw8ZApjGO3/unPWUPsIymfsJmyrDVWC8Tv/a1HeOtGmkwNd/7xUS0Xcnvsx" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/contrib/auto-render.min.js" integrity="sha384-+XBljXPPiv+OzfbB3cVmLHf4hdUFHlWNZN5spNQ7rmHTXpd7WvJum6fIACpNNfIR" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
 
Q: If there're N nodes, What is the minimum number of edges to make all Nodes connected? 

A: We need at least N-1 edges, and at most $$\binom{N}{2}$$ edges.

Q: Still N nodes, with E edges, but what is the minimum number of edges to add to connect all Nodes?

A: Idea is to find the number of connected parts, i.e. a locally connected newtowk with $$n_{i}$$ Nodes, and $$e_{i}$$ Edges.  

Explore Thinking: How to find exactly all pairs of edges to reconnect to make graph connected?
A: We need to check paid of Nodes in connected parts where they have two or more edges, such that we can destroy this pair and connect them to other connected parts (including isolated Nodes, they are self-connected!)

Back to the Problem [Number of Operations to Make Network Connected](https://leetcode.com/problems/number-of-operations-to-make-network-connected/)

The main idea of union find is to classify the locally connected components: given one pair of connected link, we can always update the starting node, since each pair is ordered (actually not even necessary condition for label update!), if we label each node with the node with least value among those connected with it (i.e. there exists a path between two nodes, and we label each node with the node in the path with least value, call it starting node). Thus, whenever we check one pair, we check the starting node label of two and label them with the smaller one, if we go through the whole pairs and no update, then we're finished!   

```cpp
class Solution {
public:
int makeConnected(int n, vector<vector<int>>& connections) {

int num = connections.size(); //number of connections
if(n-1 > num) return -1;
int iso = 0;
 vector<vector<int>> web (n);
vector<int> flag (n);
for(int i=0; i<n; ++i){
   flag[i] = i; 
}
bool change = true;
while(change){
   change = false; 
   for(int i=0; i<num; ++i){
      int a = connections[i][0], b = connections[i][1];
      if(flag[b] > flag[a]){
        flag[b] = flag[a];
        change = true;
      }    
else if(flag[b] < flag[a]){
    flag[a] = flag[b];
    change = true;
}    
}
}

//Orderness of connections is necessary: a>b so if flag[a] == -1, 
//no Node value less than a is connected with a
//nodes connected with a is greater than a from web
//For the loop, make sure
 set<int> ans;  
for(int i=0; i<n; ++i){
  ans.insert(flag[i]); 
}
return ans.size()-1;
}
    
};

```

Explore Thinking: How to find the distance between any pairs of nodes?

A: Follow Dijkstra Approach: if there's any middle node to recalculate the distance between any two nodes, add it! If we finish one-time search and no pair of distance update, then jump out of the loop!

```cpp
vector<int> count (n,0);
vector<vector<int>> web (n, vector<int>(n,1e5));
for(int i=0; i<n; ++i){
  web[i][i] = 0; 
}
        
for(int i=0; i<num; ++i){
   int a = connections[i][0], b = connections[i][1]; 
   web[a][b] = 1;
   web[b][a] = 1;
   count[a]++;
   count[b]++;   
   //web[connections[i][1]].push_back(connections[i][0]);  
}

//Dijkstra
 
bool change = true;
int time = 0;
        
while(change){
   ++time; 
   change = false; 
   for(int i=0; i<n; ++i){
      for(int j=i+1; j<n; ++j){
         if(web[i][j] < 1e5){
            for(int k=0; k<n; ++k){
               if(web[i][j] + web[j][k] < web[i][k]){
                   web[i][k] = web[i][j] + web[j][k]; 
                   web[k][i] = web[i][k];
                   change = true;
               }    
             } 
           }   
        }
     }  
}
       
//cout << "time = " << time << "\n";

for(int i=0; i<n; ++i){
   for(int j=0; j<n; ++j){
     cout << web[i][j] << " "; 
   }
   cout << "\n";
}
        
 //check connected local pattern and edge
vector<bool> vis (n,false);
 int iso = 0;
for(int i=0; i<n; ++i){
   if(vis[i]) continue;
    else if(count[i] == 0){
       ++iso;
       continue;
    } 
 int v = 1;
 int e = count[i]; 
 for(int j=i+1; j<n; ++j){
    if(!vis[j] && web[i][j] < 1e5){
        ++v;
        e += count[j];
        vis[j] = true;
     }  
}
    e /= 2; 
    ++iso;
}
```

Explore Thinking: **IF all nodes were to be placed in $$\mathbb{R}^{2}$$, can we set up any coordinate system to verify the location of each node?**
A: Dijkstra would provide all possible pairs of distance, and we could set up locally coordinates for the $$N = 3$$, three Nodes case: pick one as origin, the trajectory of the second one is the circle centered at the origin, and the third one is the intersection of two circles centered at the first and second node, with radius equal to distance between pairs, respectively.

Actually, for the three Nodes case, we we can rotate the formed "triangle" any degree freely: this would always work!

Explore Thinking: **What if there exists negative distance between nodes?**
A: Just a temporary thought, then it's a Gain-Loss Expectation problem instead of geometric metrology one: there's no negative distance~~



