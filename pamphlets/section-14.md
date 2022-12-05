# Section 14:14 - Algorithms Searching + BFS + DFS

## 180-001 Searching + Traversal Introduction

## 181-002 Linear Search
In CS, linear search(sequential search) is a method of finding a target value within a list, like looping through array to find the items. It sequentially checks
each element of the list for the target value until a match is found or until all the elements have been searched.

In js, `array.indexOf()` uses linear search to try and find the item. Another way is to write:
```js
array.findIndex(function (item) {
    return item === 'Godzilla';
});
// or
array.find(function (item) {
    return item === 'Godzilla';
});

array.includes('Godzilla');
```
All of the above searches are linear searches. That is, for the worst case, we're gonna go through the entire list(O(n) - linear time).

We can't use linear search to index websites like google or search for friends in facebook, because it's gonna cost us a lot of time.

Is there a better way?

What if the list of our data was sorted? We'll answer this in next vid.

## 182-003 Binary Search
Binary search: Since we know the list is sorted, we can discard half the items instead of one at a time. We can start in the middle of the list and check
if the current item is higher or lower than the one we're looking for? If it's lower, discard everything at the left of the current element. Then go to the
middle index of the remaining items. If there is no middle index, you can choose the left of the imaginary middle index and do the comparison and ... .

If our data is sorted, we can do better than O(n) or linear time. Because a sorted list reminds us of a BST.

Storing data in a DS like a tree instead of a linear DS like an array, is actually more efficient. As we insert items, if we sort them, it gives us a better
performance than adding it to an unsorted list that we have to search through it one day.

O(log (n)) comes from the fact that we're not visiting all nodes. Each step down the tree, we're eliminating half of the nodes.

If the items are not sorted, we have to go through one by one. But if they're sorted, then you can use divide and conquer approach(merge sort and quick sort
are doing the same thing).

Linear search -> O(n)
Binary search -> O(log (n))

Traversal means going from node to node, either finding a specific thing or making sure that we touch(visit) every single node(for example to do sth to each node).

## 183-004 Graph + Tree Traversals
The names traversal and search is often used interchangeably, sometimes meaning the same thing, sometimes not.

In order to validate a tree is BST which means the left item is always lower than the right item(the rules of a BST), we have to **touch(visit) every single node**,
but how we do this?

You can think of traversal as visiting every node and because we're visiting **every** node, that's an O(n) operation(linear time). Up until now we did
loops to visit all of the items in other data structures like arrays, linked lists, hash tables, queues, stacks. How we do this in a DS like a tree or
a graph? There's 2 ways.

Do we have to do a tree traversal or a graph traversal?

Both options are the exact same. We have BFS and DFS(sometimes the search word in these two are called traversal).

Q: Why we don't store everything in lists which are simpler to understand (like arrays)? What about hash tables?

The main benefit of why we don't put complex data into lists like arrays that are sorted(why he said sorted here???), is that we get the O(log (n)) instead of O(n) .
About hash tables: Those are not ordered. 

Trees and graphs work great for when we search for things, we have better performance than array, but also when inserting or deleting, we have better performance
than sth like an array. But we also maintain the order that we wouldn't have otherwise with hash tables. Trees and graphs are used a lot when we want to
search nodes or visit every node.

## 184-005 BFS Introduction
## 185-006 DFS Introduction
## 186-007 BFS vs DFS
## 187-008 Resources BFS vs DFS
File attached
## 188-009 Exercise BFS vs DFS
## 189-010 Solution BFS vs DFS
## 190-011 breadthFirstSearch()
## 191-012 breadthFirstSearchRecursive()
## 192-013 PreOrder, InOrder, PostOrder
## 193-014 depthFirstSearch()
## 194-015 Optional Exercise Validate A BST
File
## 195-016 Graph Traversals
## 196-017 BFS in Graphs
## 197-018 DFS in Graphs
## 198-019 Dijkstra + Bellman-Ford Algorithms
## 199-020 Searching + Traversal Review

---


002 Search-Repl
https://repl.it/@aneagoie/searching

004 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview-click-here-for-course-link

005 Code-Repl
https://repl.it/@aneagoie/Data-Structures-Trees

006 Code-Repl
https://repl.it/@aneagoie/Data-Structures-Trees

009 Exercise-Repl
https://repl.it/@aneagoie/Traversal-Quiz-1

010 Solution-Repl
https://repl.it/@aneagoie/Traversal-Quiz

011 Starting-Code-
https://repl.it/@aneagoie/Data-Structures-Trees

011 Finished-Code
https://repl.it/@aneagoie/Data-Structures-Trees-traversals-bfs

012 Starting-Code
https://repl.it/@aneagoie/Data-Structures-Trees-traversals-bfs

012 Finished-Code
https://repl.it/@aneagoie/Data-Structures-Trees-traversals-bfs-recursive

014 Starting-Code
https://repl.it/@aneagoie/Data-Structures-Trees-traversals-bfs-recursive

014 Finished-Code
https://repl.it/@aneagoie/Data-Structures-Trees-traversals

014 BFS-vs-DFS
https://stackoverflow.com/questions/9844193/what-is-the-time-and-space-complexity-of-a-breadth-first-and-depth-first-tree-tr

016 VisuAlgo-Traversal
https://visualgo.net/en/dfsbfs

019 How-Dijkstras-Algorithm-Works
https://medium.com/basecs/finding-the-shortest-path-with-a-little-help-from-dijkstra-613149fbdc8e

020 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview-click-here-for-course-link
