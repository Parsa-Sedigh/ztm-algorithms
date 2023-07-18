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
is gonna be `log n`.

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
There are some algorithms. For example, we have AVL trees and red black trees allow us to make sure that our BST is gonna be balanced.

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
In js, you can use **arboreal** library for tree traversal and ... .

## 132-009 Solution lookup() 
It's up to us put the node that has a equal value to the currentNode(left or right doesn't matter in case of equal value).

To verify the result, you can use `JSON.stringify(traverse(tree.root))` and then paste the JSON into the browser's console which would give you a nicer
format. Just note that you shouldn't copy the `stringify()` result with it's quotes around(don't copy the string).

So we understood why we have bigO of O(log n): Although we have loops like while loops, we're not actually iterating through every single node, we're only
iterating using divide and conquer which means we're dividing up so that we don't visit all the nodes. Each node that we visit, we make a decision to go left
or right(in this case).

## 133-010 Extra Exercise remove()

## 134-011 Solution remove() **(TODO)**

## 135-012 AVL Trees + Red Black Trees
Usually in production, you wanna have a balanced tree. There are 2 types of trees that are popular when it comes to this. Although we built our 
BST, you'd most likely in production use sth like an AVL tree or a red black tree that automatically re-balances itself, so that we don't have those edge
cases where our balanced tree turns into a linear unbalanced tree and we get O(n) on all the operations.

Usually you use a library that implements these trees.

So these two trees are usually the most popular for balancing BSTs. Just explain why they are useful(because if we have an unbalanced tree, it will become
like a linked list and gets O(n) on all operations).

## 136-013 Resources AVL Trees + Red Black Trees
See the attached file.

## 137-014 Binary Heaps
A heap can be used in any algorithm where ordering is important and it's commonly used when it comes to priority queues. With arrays, we had random access, it allowed
us to randomly access any element within them using an index. In a linked list, we can change things dynamically like an array, but finding sth within them is
`O(n)` (linear time), because we had to go through the linked list. Heaps are a bit different. You can't do O(1) random access like we did with arrays or hash tables,
as we know about trees, we have to do some sort of traversal(heap is a type of tree!). Now compared to a BST, in heaps, lookup is O(n) and not O(log n), because
it's less ordered than a BST. A BST had a meaning between left and right child, the left was always less than the right. In a binary heap, that doesn't matter.
Left and right can be any value as long as it's less than the top value(in max heap). So if the value we're looking for is for example less than the currentNode in
a binary heap, we have to check **both** nodes underneath the `currentNode` and ... and looking up becomes O(n) . 

So binary heaps pretty much turned into a searching through a linked list or iterating through an array.

Q: So why would we ever want to use a binary heap?

A: Binary heaps are really great at doing comparative operations, just like saying: I want people that have a value over 33 . Because in that case, we can just
grab the top nodes in a max binary heap. Instead of going all the way down through the nodes. This example would be O(n) with a BST.

Binary heaps are used a lot in data storage, priority queues, sorting algorithms.

Insert operation in binary heaps: **Worst case: O(log n) - Best choice: O(1)**

In order to truly understand why we need binary heap, why they're useful, how they're different from BST, we need to talk about priority queues.

## 138-015 Quick Note on Heaps
### Gotcha about heaps:
When you hear memory heaps, that's not the same as the heap DS. The naming is just coincidental and heap has no real relationship with the DS that is named
heap.

Memory heap is a heap of memory if you're talking about a language runtime for example. VS a heap DS, they're different.

## 130-016 Priority Queue
The beauty of binary heaps is that they take up the least amount of space possible because it's always left to right insertion. So there's no concept of
an unbalanced binary heap. We don't have to re-balance it like a BST, because of this(because they do left to right insertion), they preserve this order of 
insertion, which is great and you can implement binary heaps using arrays vs what we did before with BSTs where we used nodes.

Left to right insertion: In binary heaps, always start from left when inserting nodes and then go to right(in the same level).

So the only guarantee that binary heap gives us, is the parent is always greater than the children(in case of max heap). Now besides being memory efficient and 
compact(because it's always a complete binary tree), binary heaps are useful for things such as priority queues.

Although searching through a binary heap is a lot slower than a BST, you have an idea of priority, because insertion is done in order(left to right) and
although we might have to bubble up the inserts every once in a while(bubbling means for example in a max heap, after inserting a value which is big, you need
to bring it upper in the tree till it's less than it's parent, why? because it has more value(higher priority!)), most of the time you get really fast inserts
with binary heaps.

**Note:** So in binary heaps, lookups are slow but you wanna use binary heaps when you're just interested in finding the max or min it it's a min heap and
a lot of times in binary heaps or in priority queues, you have methods like findMax or findMin that is O(1), because you know right away that the top root node
is the max or min(in min heaps).

## 140-017 Trie
A trie is a specialized tree, used in searching(most often with text) and in most cases, it can outperform search trees, hash tables and most other DSs depending
on the type of search you're doing.

Tries allow you to know if a word or part of a word exists in a body of a text. A trie usually has an empty root node which is the starting point.

Trie is not a binary tree because a node can have more than 2 children.

The power of trie is when we search for sth such as `N`. We will know that there's 2 words associated with the word N(look at the slide).

Another name of trie is prefix tree.

You can think of trie as auto-completion. It's used for searching words in a dictionary, providing other suggestions on search engines or even IP routing.

The benefit of this DS is speed and space, The bigO of finding a word in DS is:
Because we're not gonna go through every single node. Instead, all we need to do is to find the length of the word, so the bigO of a trie in searching is
O(length of the word we're searching for). In space complexity, tries also have a major advantage. Because we use prefixes such as N in the slide which is used
in multiple words, we don't have to store it multiple times, it's stored in one location and we have children linking to it. Because of those prefixes,
you save a lot of space, because we avoid storing the prefix letters.

## 141-018 Tree Review

---

```js
class Node {
    constructor(value){
        this.left = null;
        this.right = null;
        this.value = value;
    }
}

class BinarySearchTree {
    constructor(){
        this.root = null;
    }
    insert(value){
        const newNode = new Node(value);
        if (this.root === null) {
            this.root = newNode;
        } else {
            let currentNode = this.root;
            while(true){
                if(value < currentNode.value){
                    //Left
                    if(!currentNode.left){
                        currentNode.left = newNode;
                        return this;
                    }
                    currentNode = currentNode.left;
                } else {
                    //Right
                    if(!currentNode.right){
                        currentNode.right = newNode;
                        return this;
                    }
                    currentNode = currentNode.right;
                }
            }
        }
    }
    lookup(value){
        if (!this.root) {
            return false;
        }
        let currentNode = this.root;
        while(currentNode){
            if(value < currentNode.value){
                currentNode = currentNode.left;
            } else if(value > currentNode.value){
                currentNode = currentNode.right;
            } else if (currentNode.value === value) {
                return currentNode;
            }
        }
        return null
    }
    remove(value) {
        if (!this.root) {
            return false;
        }
        let currentNode = this.root;
        let parentNode = null;
        while(currentNode){
            if(value < currentNode.value){
                parentNode = currentNode;
                currentNode = currentNode.left;
            } else if(value > currentNode.value){
                parentNode = currentNode;
                currentNode = currentNode.right;
            } else if (currentNode.value === value) {
                //We have a match, get to work!

                //Option 1: No right child: 
                if (currentNode.right === null) {
                    if (parentNode === null) {
                        this.root = currentNode.left;
                    } else {

                        //if parent > current value, make current left child a child of parent
                        if(currentNode.value < parentNode.value) {
                            parentNode.left = currentNode.left;

                            //if parent < current value, make left child a right child of parent
                        } else if(currentNode.value > parentNode.value) {
                            parentNode.right = currentNode.left;
                        }
                    }

                    //Option 2: Right child which doesnt have a left child
                } else if (currentNode.right.left === null) {
                    currentNode.right.left = currentNode.left;
                    if(parentNode === null) {
                        this.root = currentNode.right;
                    } else {

                        //if parent > current, make right child of the left the parent
                        if(currentNode.value < parentNode.value) {
                            parentNode.left = currentNode.right;

                            //if parent < current, make right child a right child of the parent
                        } else if (currentNode.value > parentNode.value) {
                            parentNode.right = currentNode.right;
                        }
                    }

                    //Option 3: Right child that has a left child
                } else {

                    //find the Right child's left most child
                    let leftmost = currentNode.right.left;
                    let leftmostParent = currentNode.right;
                    while(leftmost.left !== null) {
                        leftmostParent = leftmost;
                        leftmost = leftmost.left;
                    }

                    //Parent's left subtree is now leftmost's right subtree
                    leftmostParent.left = leftmost.right;
                    leftmost.left = currentNode.left;
                    leftmost.right = currentNode.right;

                    if(parentNode === null) {
                        this.root = leftmost;
                    } else {
                        if(currentNode.value < parentNode.value) {
                            parentNode.left = leftmost;
                        } else if(currentNode.value > parentNode.value) {
                            parentNode.right = leftmost;
                        }
                    }
                }
                return true;
            }
        }
    }
}

const tree = new BinarySearchTree();
tree.insert(9)
tree.insert(4)
tree.insert(6)
tree.insert(20)
tree.insert(170)
tree.insert(15)
tree.insert(1)
tree.remove(170)
JSON.stringify(traverse(tree.root))

//     9
//  4     20
//1  6  15  170

function traverse(node) {
    const tree = { value: node.value };
    tree.left = node.left === null ? null : traverse(node.left);
    tree.right = node.right === null ? null : traverse(node.right);
    return tree;
}
```

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
