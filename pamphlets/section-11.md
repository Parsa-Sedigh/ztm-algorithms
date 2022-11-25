# Section 11: 11 - Data Structures Graphs

## 142-001 Graphs Introduction
Graphs encompass trees and linked lists. Linked lists are a type of tree, tree is a type of graph. 

Facebook has an undirected graph and not a directed one. Because when you're connected to a friend, that friend is also connected to me.
It's not 1-way.

Twitter is more directed because if I have my profile, people can follow me and I can follow people, but if somebody follows me, I don't automatically
follow them. So twitter is more directed.

Cyclic graphs are common in weighted graphs such as google maps, because most of the time, there is a way to get back.

## 143-002 Types Of Graphs
## 144-003 Exercise Guess The Graph
## 145-004 Graph Data
Graphs are built on top of other DSs.

We can create a graph in 3 ways:

edge list:
```js
const graph = [[0, 2], [2, 3], [2, 1], [1, 3]]; // the arrays state the connections
```

adjacent list(adjacency list):
With this we can create a graph where the index is the node and the value is the node's neighbors. We can use objects, arrays or linked lists to represent them.

Note: The index of the array is the value of the actual graph node. If a node value is sth other than a number, you can use object. So if you have sequential numbers
for the value of graph, using arrays in this approach is good, but if not, you can use objects in this approach.
```js
/* index 0 is connected to 2. Index 1 is connected to 2 and 3. Index of 2 is connected to 0, 1 and 3. */
const graph = [[2], [2, 3], [0, 1, 3], [1, 2]];

const graphWithObj = {
    0: [2],
    1: [2, 3],
    2: [0, 1, 3],
    3: [1, 2]
};
```

Adjacent(adjacency) matrix: This matrix is gonna have 0s and 1s indicating whether the node x has a connection to node y, 0 means no, 1 means yes and if you have a weighted
graph, you can write weights. You can use objects here too.
```js
const graph = [
    [0, 0, 1, 0],
    [0, 0, 1, 1], // node 1 is connected to node 2 and node 3
    [1, 1, 0, 1], // node 2 is connected to 0, 1 and 3
    [0, 1, 1, 0],
];

// or:
const graphObj = {
    0: [0, 0, 1, 0],
    1: [0, 0, 1, 1], 
    2: [1, 1, 0, 1], 
    3: [0, 1, 1, 0]
};
```

## 146-005 Exercise Graph Implementation
We're gonna create a graph using adjacency list using a hash table.

Why we're using an object instead of graph an array?
Because if we start removing things from the graph or placing things in the graph that's out of order, it's gonna cost us a lot. Remember, arrays unshifting and
shifting is expensive.



## 147-006 Solution Graph Implementation
BFS and DFS can be applied both to graphs and trees.

## 148-007 Graphs Review

## 149-008 Data Structures Review
## 150-009 What Else Is Coming Up

- In Sorting, we use arrays and trees.
- in dynamic progrraming, we use hash tables
- BFS and DFS -> they're used in graphs and trees
- recursion -> trees

---

001 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview

002 The-Internet-Map
https://internet-map.net/

003 VisuAlgo-Graphs
https://visualgo.net/en/graphds

005 Exercise-Repl
https://repl.it/@aneagoie/Data-Structures-Graphs-1

006 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Graphs

007 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview
