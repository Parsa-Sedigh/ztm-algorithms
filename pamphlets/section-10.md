# Section 10: 10 - Data Structures Trees

## 124-001 Trees Introduction
Trees are a DS that have a hierarchical structure as opposed to sth like linked lists or arrays which are linear, trees can have a zero or more child nodes.

A tree usually starts with a single root node or a parent node and every child of the tree descends from this root node. So it's kinda like an inversed tree, really **and
every child of a node, descends from only one parent.** So you have a parent-child relationship and it's directional(go in one way).

In trees we can have subtrees, the red area in slide.

Our web pages are created by DOM(document object model) and it's a tree DS. The children are connected hierarchically to one another.

Abstract syntax tree is how code is usually being run. Usually we write code and then it gets broken down by the machine into abstract syntax tree so that it understands
what we wrote down and it uses a tree DS.

The beauty of trees is that we use the same principles as we did in linked lists, that is we have nodes and these nodes can contain any type of info.

Linked lists is technically a type of tree, but with just one single path and therefore it's linear, there's only one way to go from top to bottom vs in a tree.

The thing that is different from a linked list, is that a node in tree can only point to a child(all the arrows in tree are pointing down). There's always one entry point(the root)
but nodes don't really have to reference their parent.

## 125-002 Binary Trees
Linked lists are a **type** of a tree.

Rules in binary trees:
- each node can only have either 0, 1 or 2 nodes and each child can only have 1 parent

Perfect binary tree: In there, a node either has 0 children or 2 children and also the bottom layer of the tree is completely filled, nothing's missing.
This type of binary tree is really efficient and is sth that is desirable. When binary trees are perfect, they have two interesting properties:
1) the number of total nodes on each level, doubles as we move down the tree: first level: 1 node, second level: 2 and then 4 and ... .
2) the number of nodes on the last level is equal to the sum of the number of nodes on all the other levels + 1 . Which means **about half** of our nodes are on the last level and this
brings an interesting point: By organizing our data in this way, we have half of this data in the bottom level. If somehow we can avoid visiting every node, even if the node
we're looking for is at the very bottom, perhaps there's some efficiencies that we can have. Because of this type of structure, you're gonna see a new notation of BigO: O(log n)

Full binary tree: a node has either 0 or 2 children, but never 1 child.


## 126-003 O(log n)
Because of the way binary trees are structured, there's a certain way for us to calculate the number of nodes that they have.

Total number of nodes in a binary tree: 2^h - 1

`log nodes = steps`(we dropped -1 from the above formula because it's insignificant)

log n means that based on the height, the maximum number of decisions(let's say we're looking for a specific node) that we're gonna take,
is gonna be log n.

Note:
for example: log 100 = 2 because 10^2 = 100

When you see the notation of O(log n), all it's saying is that the choice of the next element on which to perform some sort of actions, is one of
several possibilities and only **one** needs to be chosen, We don't have to check both.

A good way to think about `log n` is when you're looking through a phone book. You don't actually check every single person in a phone book. Instead,
you can simply do what's called **divide and conquer** by looking based on where their names alphabetically begin. You keep dividing and conquering until
you get to that person. You only need to explore a subset of each section before eventually finding the person.

So O(log n) is like looking through a phonebook.

O(log n) is fast. O(log n) is better than O(n) (linear time). Because we don't need to check every single element or operate on.

## 127-004 Binary Search Trees
Binary search tree allows us to search really efficiently. A place like google search would find this extremely useful. They use a tree DS so that our
searches could be a lot faster with sth like `O(log n)`.

Most common tree DS which is binary search tree which is a subset of binary tree.

A binary search tree is really good at searching. They are great for comparing things. Now, why would this be better than for example a hash table where
we can just give it a key and get the item right away?
Well, the binary search tree DS preserves relationship. Just like you wouldn't want your folders on your computer to be in a hash table DS because there is no sort of
relationship, instead, you want your folders to have relationships, to have a parent folder and sub folder and ... . Binary search tree allows us to
preserve these relationships.

Binary search tree rules:
1) All child nodes in the tree to the right of the root node, must be greater than the current node. That means if we keep going to the right,
the value of the node constantly increases. If we go to left, it decreases from the current node.
2) **a node can only have up to 2 children because it's a binary tree.**

The advantage of binary search tree is searching and lookup is fast. We just compare the value of current node with the node we're searching and if the value
of current node is smaller, we go to the right, otherwise go to left. We don't have to iterate in a linear fashion through each node and that is what lookup means,
it means we can search for an item a lot faster than for example an array where we have to iterate and loop through every single item.

What about insert and delete?

In a hash table, we can do insert and delete really fast with O(1) or constant time, but in binary search tree: O(log n) because in order for us to
insert or delete sth in a BST, we need to first figure out where to insert or delete the item(we need to first find it) from the root node and then
we have to decide which node is gonna take it's place(in case of delete)? So as you can imagine, if we had a lot of children which means a lot of nested 
nodes in the case of BST, a lot of reordering needs to happen.

## 128-005 Balanced VS Unbalanced BST
There's a problem with BSTs:
If we have a unbalanced BST like for example all of the nodes keep adding to the right side of the tree, it all of a sudden turns into a linked list where
in the side with most nodes, we're just looping through every single node. This is a big problem that comes with BST that is you can have balanced search trees
which all of their operations are O(log n) but the unbalanced ones have O(n) for their operations(sorta turned into a long linked list). Why O(n) for unbalanced BSTs?
Because we have to loop through every node.

This is why an unbalanced BST is bad.

How do you balance a BST?
There are some algorithms. For example we have AVL trees and red black trees allow us to make sure that our BST is gonna be balanced.

## 129-006 BST Pros and Cons
**Assuming the BST is balanced**, look at the BST pros & cons slide.

Since we can place the node in BST anywhere in memory, we can have flexible size which means we can keep growing our tree.

We usually have to do some sort of traversal through the tree for any **sort** of operation, so it doesn't have `O(1)` operation.

BST comparison to arrays:

Assuming the BST is balanced:

So compared to an array(if the array is unsorted, we have to iterate through the entire array so O(n)), a lookup in BST will be a lot faster, 
because it's O(log n). Inserts and deletes are also faster than an array unless the array is adding to the end, otherwise, arrays have to shift all the indexes
vs a BST is O(log n) for this operation.

BST comparison to hash tables:
Although hash tables allow us to insert and search at constant time(O(1)), with BSTs we have sorted data and we also have this structure of
parent-child relationship that you won't be able to get too much with hash tables. 

BSTs aren't the fastest for anything, O(log n) for balanced and O(n) for unbalanced , but there are certain conditions where they do outperform objects
and arrays(we will learn these).

## 130-007 Exercise Binary Search Tree
To verify that your BST implementation is working, write:
```js
JSON.stringify(traverse(tree.root)); // give it the root node of our tree
```

## 131-008 Solution insert()


## 132-009 Solution lookup()
## 133-010 Extra Exercise remove()
## 134-011 Solution remove()
## 135-012 AVL Trees + Red Black Trees
## 136-013 Resources AVL Trees + Red Black Trees
## 137-014 Binary Heaps
## 138-015 Quick Note on Heaps
## 130-016 Priority Queue
## 140-017 Trie
## 141-018 Tree Review

---

001 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview

004 Binary-Search-Tree-VisuAlgo
https://visualgo.net/bn/bst

005 Big-O-Cheat-Sheet
http://bigocheatsheet.com

007 Exercise-Repl
https://repl.it/@aneagoie/Data-Structures-Trees-exercise

008 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Trees-exercise-2

009 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Trees-exercise-3

010 Exercise-Repl
https://repl.it/@aneagoie/Data-Structures-Trees-exercise-3

010 Binary-Search-Tree-VisuAlgo
https://visualgo.net/en/bst

011 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Trees

014 VisuAlgo-Binary-Heap
https://visualgo.net/en/heap

015 A-great-explanation-of-why
https://stackoverflow.com/questions/1699057/why-are-two-different-concepts-both-called-heap

016 Priority-Queue-Javascript-Code
https://www.geeksforgeeks.org/implementation-priority-queue-javascript/

018 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview
