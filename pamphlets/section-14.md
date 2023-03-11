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

**O(log (n)) comes from the fact that we're not visiting all nodes. Each step down the tree, we're eliminating half of the nodes.**

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

There are 2 types of searching or traversing a tree or a graph: BFS and DFS

## 184-005 BFS Introduction
BFS uses additional memory because it is necessary to track the child nodes of all the nodes on a given level while searching that level. This means that
we need to track every node and it's children in order.

## 185-006 DFS Introduction
The search follows one branch of the tree down as many levels as possible until target node is found or the end is reached. If the target
was not found (which means When the search can go on further), it can continues at the nearest ancestor with an unexplored child.

DFS has a lower memory requirement than BFS because it's not necessary to store all the child pointers at each level.

The idea with DFS is that we want to go as deep as possible into a graph or tree, usually starting from the left side and then start going to the right
until the traversal of the tree is done.

There are different variations of DFS.

**Q:** Why do we have these two ways of exploring a tree or a graph? What's the pros and cons?

## 186-007 BFS vs DFS
### Main pros and cons
The time complexity for BFS and DFS is the same, because they all visit the nodes at least once. So it's O(n) .

BFS:

With BFS, it's very good for finding the shortest path between a starting point and any other reachable node. Because we always start off with the root
node and then search the closest nodes first and then the nodes further and then further and ... .

Downside of BFS: It requires more memory than DFS.

Rule of thumb: If you have additional info on the location of the target node and you know that the node is likely in the upper level of a tree, then BFS
is better because it will search through the closest nodes first.

DFS:

If you know that the node is likely at the lower level of a tree, perhaps DFS is better in that case.

DFS is good at asking the question: **Does the path to a certain node exist, from a source node to a target node?**

The big advantage with DFS is that it uses less memory than BFS.

Downside: It can get slow especially if the tree of graph is really deep and it's not necessarily good at finding the shortest path.

Now you know when to use which one!

## 187-008 Resources BFS vs DFS
File attached
## 188-009 Exercise BFS vs DFS

## 189-010 Solution BFS vs DFS
Q1:

BFS. Because it starts searching the closest nodes to the parent, first.

Q2:

BFS. Because DFS will take a long time with a deep tree, since it's gonna go one by one, going really really down below and because solotuions are rare,
it's most likely going to just repeat that step over and over and with DFS, we use recursive functions and with DFS, that can take a really long time, although
with VFS we have some memory concerns.

Q3:

DFS. If tree is wide, it means there is a lot of nodes and it's not a binary tree, it has a ton of nodes underneath each parent.
Because BFS is gonna need too much memory. The way BFS works is that it has to keep track of the nodes(and their children) in the current level in a sth called queue.
So because of that, it might take up too much memory.

Q4:

DFS. This is what DFS built for.

Q5:

BFS.

## 190-011 breadthFirstSearch()
As it goes through a level, we need to keep a reference to all the children of every node that we visit, so that we can go back to them and visit them.
That's where the memory usage of this algo is coming from. We're gonna use a queue DS to store them. 

The queue we have in BFS, can get large, because we have to keep the reference of nodes and their children, so the emory consumption can hurt us. So if we had
a wide tree(maybe a node have 10 child nodes) instead of a binary tree which a node only has a left and right nodes, the queue can become big and depending on the
node's value(for example a large object), the memory consumption might be big.

## 191-012 breadthFirstSearchRecursive()
Usually BFS is implemented with iterative approach. But for fun, we can do a recursive BFS.

In the answer(breadthFirstSearchR method), we didn't define the queue and list in the method itself. Why? Because in a recursive function, it's gonna be
called over and over and therefore we're gonna be resetting these variables if we declare them locally and list and queue would be an empty array in each
call. So we would need to pass queue and list as params and we pass params like: `BFSR([this.root], []);`. So this was a gotcha in recursive approach.

## 192-013 PreOrder, InOrder, PostOrder
There's 3 ways that we can implement DFS(3 types of traversals): preorder, inorder, postorder. There's 3 different orders that
we can return the `list` from the algo with DFS.

With **inorder**, we have everything in sorted order.

**Preorder** is useful if you want to recreate a tree.

## 193-014 depthFirstSearch()
Most of the time, DFS is implemented using recursion because it's simple to do so. Now sine with recursion, we're gonna call the function over and over,
we can't declare variables inside of it because they'll be reset by each call. So we're gonna pass it params.

When we have recursion, the parent function call which calls it's function again, stops at that line until the further recursive calls return:
```js
function recursive() {
    // code ...
    recursive() // this will be sit here until it's child recursive calls return(in case we want the result) or finish execution
    // ...    
}
```

With recursion, we're using a stack DS, each of the function calls are added to the call stack and we'll start to `return`, as they reach the end.

BFS -> uses queue stack(for remembering the visited nodes and their children)
DFS -> uses stack DS(for recursive calls)

The amount of space that we need in DFS unlike BFS which uses queue DS, is dependant on the height of the tree because the height of the tree will match the
deepest recursive function call and that's what's going to be added to the stack as memory. So our memory consumption in DFS is `O(height of tree)` which will
give us the worst case scenario when using DFS.

## 194-015 Optional Exercise Validate A BST
File TODO
## 195-016 Graph Traversals
Trees are a type of graph.

What items are the closes or related to the last book that we bought -> BFS

On facebook to see what type of friend reqs I should be recommended. For example if I have a connection on linkedin -> DFS to see what degree of connection
I have with that CEO.

These are the basis of how peer to peer networks work, how google maps work(using BFS).

BFS is usually good for shortest path, that is what's the closest to our node? What are the most related items on amazon? Who are our closest friends on facebook
or closest connections on linkedin?

DFS is good to see if sth exists. With DFS, we're able to go really deep into a graph fairly fast than BFS that might cost a bit of extra memory.

## 196-017 BFS in Graphs
BFS is used in recommendation engines, peer to peer networks, google maps, facebook friend requests and instagram recommendations.

BFS allows us to convert a graph essentially into a tree because we know who the children of the parent node is and then the grandchildren and then ... .

BFS pros:

Helps us to determine the shortest path and it's better if we know that a node that we're looking for is close to us, because it's gonna look at the 
closer nodes first. 

BFS is crafter to help us determine the shortest path between two nodes in a graph.

## 197-018 DFS in Graphs
You can solve a maze with DFS! Because DFS is exactly like solving a maze. Because in maze, the idea is to go as deep as we can and when you
git a roadblock, you backtrack and find a different route and then you keep backtracking until you find the desired node or you exit the maze.

You can now implement an algorithm that solves a maze..

The idea of backtracking after a dead end and then repeating the walk to another path, is **recursion**. 

DFS is good at saying does the path exits. However, it doesn't tell us the shortest path, but whether it even exists and it uses less memory than BFS.

The one downside with DFS is if you have a really deep graph, then it can get slow, because the deeper the graph, the more recursive calls, the more space
complexity you add because we have to keep track of those function calls on a stack.

## 198-019 Dijkstra + Bellman-Ford Algorithms
We can use Dijkstra or bellman-ford algos to figure out the shortest path problem. But didn't we use BFS for the shortest path problems? Why do we need these
two extra algos?

Yeah, BFS is great for the shortest path problem, but there's one thing that it can't do. It assumes that each jump(path) to another node in a graph, has the same
weight. With BFS and DFS we don't care what kind of weight an edge has. But in real life for example in google maps, some roads are faster than the
others. Maybe because of traffic or the distance from one node to another is shorter than other.

So DFS doesn't take into the account these weights, we need sth else.

So these two new algos allow us to find the shortest path between two nodes(vertices) of a weighted graph.

Bellman-ford is very effective at solving the shortest path over Dijkstra's algo because it can accommodate negative weights. So if a weighted graph
has negative weights or number, bellman-ford algo is gonna be able to solve the shortest path problem, while dijkstra won't be able to.

Now why would you ever use dijkstra's algo if bellman-ford can do better?

Because bellman-ford can take a long time to run in terms of complexity and it's not the most efficient algo. The worst case for bellman-ford algo is
usually O(n^2) , so it's not very efficient. dijkstra is faster with the downside that it can't accommodate for negative weights between vertices.

So if the graph is weighted and there's not negative weights in it, we use dijkstra.

## 199-020 Searching + Traversal Review

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
                    if(parentNode === null) {
                        this.root = currentNode.left;
                    } else {
                        currentNode.right.left = currentNode.left;

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
    BreadthFirstSearch(){
        let currentNode = this.root;
        let list = [];
        let queue = [];
        queue.push(currentNode);

        while(queue.length > 0){
            currentNode = queue.shift();
            list.push(currentNode.value);
            if(currentNode.left) {
                queue.push(currentNode.left);
            }
            if(currentNode.right) {
                queue.push(currentNode.right);
            }
        }
        return list;
    }
    BreadthFirstSearchR(queue, list) {
        if (!queue.length) {
            return list;
        }
        const currentNode = queue.shift();
        list.push(currentNode.value);

        if (currentNode.left) {
            queue.push(currentNode.left);
        }
        if (currentNode.right) {
            queue.push(currentNode.right);
        }

        return this.BreadthFirstSearchR(queue, list);
    }
    DFTPreOrder(currentNode, list) {
        return traversePreOrder(this.root, []);
    }
    DFTPostOrder(){
        return traversePostOrder(this.root, []);
    }
    DFTInOrder(){
        return traverseInOrder(this.root, []);
    }
}

/* In recursive calls, each call is pushed to the top of the call stack and will be waiting for the upper calls to get popped, in order to
   resume it's execution. So for example when we arrive to a node, first we visit it and then we do another call with it's left child and
   therefore andother function call is pushed to the stack, but the previous call is still in the call stack. So when we again arrive to the
   original call, we resume it's execution and we go to it's right child this time and ... .*/
function traversePreOrder(node, list){
    list.push(node.value);
    if(node.left) {
        traversePreOrder(node.left, list);
    }
    if(node.right) {
        traversePreOrder(node.right, list);
    }
    return list;
}

function traverseInOrder(node, list){
    if(node.left) {
        traverseInOrder(node.left, list);
    }
    list.push(node.value);
    if(node.right) {
        traverseInOrder(node.right, list);
    }
    return list;
}

function traversePostOrder(node, list){
    if(node.left) {
        traversePostOrder(node.left, list);
    }
    if(node.right) {
        traversePostOrder(node.right, list);
    }
    list.push(node.value);
    return list;
}


const tree = new BinarySearchTree();
tree.insert(9)
tree.insert(4)
tree.insert(6)
tree.insert(20)
tree.insert(170)
tree.insert(15)
tree.insert(1)
// tree.remove(170);
// JSON.stringify(traverse(tree.root))

console.log('BFS', tree.BreadthFirstSearch());
console.log('BFS', tree.BreadthFirstSearchR([tree.root], []))
console.log('DFSpre', tree.DFTPreOrder());
console.log('DFSin', tree.DFTInOrder());
console.log('DFSpost', tree.DFTPostOrder());

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
