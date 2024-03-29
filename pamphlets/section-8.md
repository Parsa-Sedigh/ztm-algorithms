# Section 8: 08 - Data Structures Linked Lists

## 88-001 Linked Lists Introduction
What problem did we encounter with arrays?

With static arrays, we only had a certain amount of data or memory that can be allocated next to each other in memory. But then both dynamic and static arrays can
increase their memory once it hits a certain limit and double up that memory in another location. But that operation, every once in a while of doubling up the
array in order to create more memory, had a performance implication and it cost us O(n) . Additionally, arrays also had bad performance for any sort of operations like
insert and delete that had to shift indexes over, especially when you inserted or deleted any item that wasn't the end of the array.

Hash tables solve some of the problems of array but they weren't ordered. How can we solve this problem? Linked lists!

There are tradeoffs when it comes to data structures!

## 89-002 What Is A Linked List
A list(in the pic, a singly linked list), contains a set of nodes. In the slide, both red and green blocks together create a node. These nodes
have two elements:
1) The value
2) a pointer to the next node

First node -> head
last node -> tail

Note: Some people call the tail anything that is after the head! But we call it the very last node.

Linked lists are what we call null terminated which signifies that it's the end of the list. So we know that last node is the tail node because it
points to null.

You can have the linked lists sorted or unsorted.

JS doesn't come with linked lists builtin. But for example java has linked list. But we can build one in JS.

## 90-003 Exercise Imposter Syndrome

## 91-004 Exercise Why Linked Lists
Q: Why do you think linked lists may be better than hash tables or arrays?

Play around with [visualgo.net/en/list](https://visualgo.net/en/list)

## 92-005 Solution Why Linked Lists
One key thing is that linked lists have a sort of loose structure that allows you to insert a value into the middle of the list by resetting a few pointers and
this is the same for deleting a node. Remember with an array DS, when we wanted to insert sth that wasn't at the end of the array, we had to add the item, let's say
in memory space 1 and then shift all the other items indexes down which costs us a lot of time(O(n)).

The main difference between arrays and linked lists is that in an array, elements are indexed. So if I wanted to go to item at index 5, we can do that easily. In a 
linked list, you start at the head and traverse the list until you get to item 5 which is O(n) and this idea of **traversal** is the same as 
**iteration** that we did with arrays where we go through indexes, except, we like to call that one traversal, because you don't really know when the linked list will end,
you start from the head and you keep going until you hit null and we have to use sth like a `while` loop when we implement our own linked list, because we don't
usually know how long the list is going to be.

Iterating = you know when it's gonna end

Traversal = you **don't** know where it's gonna end

Another advantage that array might have is that most computers have caching systems that make reading from sequential memory(memory next to each other), faster than
reading scattered addresses. Array items are always located right next to each other in memory. Linked lists(it's nodes) instead are scattered all over memory, kind of
like hash tables. So traversing through a linked list is usually quite a bit slower than iterating through items in an array, even though they're technically both O(n) .

However, the inserts that we can do in the middle of a linked list, is a lot better than an array.

What about hash tables?

Just like hash tables when we insert sth into a linked list, we just scatter it all over our memory and we can just keep adding it and we don't have to do any
unshifting or shifting on the indexes that we did with arrays.

You can also delete nodes easily vs with an array.

One advantage that it has over hash tables is that there is some sort of order to linked list, each node points to the next node, so you can have sorted data unlike
hash tables.

prepend -> add to the beginning
append -> add a new item to the end
lookup -> traversal to look for an item

**insert** in linked list is O(n) because we have to go one by one, find the index(we don't know how long our linked list is), find the index and then insert there which
is O(n) .

**delete** is also O(n) because we have to find the item.

Now you're thinking: Insert and delete in arrays are also O(n), so how is this better?
We're talking about worst case, in which case we insert or delete the very last item(worst case) and most of the times that won't be the case in linked list.

## 93-006 What Is A Pointer
```js
const obj1 = {a: true};
const obj2 = obj1;
```
Here, we're not copying the obj1. We're not creating another location in memory for obj2. When we look at RAM, there's only one entry which is {a: true}. Both obj1
and obj2 point to the same location in memory.


## 94-007 Our First Linked List
## 95-008 Solution append()
## 96-009 Solution prepend()
## 97-010 Node Class
## 98-011 insert()
While loops are good if we don't know the length of our linked list or other DS, or we just want to do sth while a condition is met.

## 99-012 Quick Note Upcoming Video
File attached

A quick heads up! In the next lecture we will create the insert() method. For those astute programmers, you may notice that the solution has 
a bug if index === 0. In this case, all you need to do is to insert into the code a condition:

```js
if (index === 0) {
    this.prepend(value);
    return this.printList();
}
```

## 100-013 Solution insert()
When inserting, the first node that we're connected the new node to, is called **leader** and the new node is gonna point to the old node that was
at the index we specified the new node to be now there.


## 101-014 Solution remove()
## 102-015 Doubly Linked Lists
Doubly linked list allows us to traverse our list backwards.

Searching through a doubly linked list can actually be a little bit more efficient and lookup can be O(n/2) because we can start at both ends and if we know
in which half of the list what we're looking for is, we can pick the optimum place to start. But we drop the constant so lookup is still `O(n)` , but it's still
technically a little bit faster.

The downside to a doubly linked list, is that we might have to hold more memory.

Now let's convert our singly linked list that we've built to a doubly one.

## 103-016 Exercise Doubly Linked Lists
File attached
## 104-017 Solution Doubly Linked Lists

## 105-018 Singly VS Doubly Linked Lists
The pro of a singly linked list, is that it's a fairly simple implementation, especially compared to the doubly one. It requires lesser memory and because
there's less memory when we do things like delete and insert and because there is technically less operation, we don't have to move around the `prev` property of a node,
it's a little bit faster.

The downside with a singly linked list is that it can't be iterated in reverse or traversed from back to front. If we ever lose the reference to `this.head` node of the
list, the list can actually be lost in memory forever.

So singly list is appropriate to use when you have less memory or memory is really expensive and you want to be careful of how much you use and your main goal is that
you want to do fast insertion and deletion and you don't really have that much searching, especially when you have insertion at the beginning of the list.

About doubly one:
The good side of it is that it can be iterated or traversed both from the front or from the back. Another beauty is that if you need to delete a previous node,
you don't need to traverse from the head node and find what the previous node is, which a singly linked list has no concept of. You can do that easily with a 
doubly linked list.

The downside is that it's complex to implement and requires more memory and storage because of prev property and there are some extra operations that we need to
perform to make sure that when we do insert and delete, that prev property is updated as well.

So doubly linked lists are good when you don't have that much limitation on memory and when you want good operation for searching of elements, such as 
searching backwards instead of just forwards.

## 106-019 Exercise reverse()
One of the most popular interview questions about linked lists is to reverse a linked list.

## 107-020 Solution reverse()
todo: Didn't understand!
## 108-021 Linked Lists Review
In some languages they aren't builtin, because linked lists are low level data structures. It's used a lot in other data structures like hash tables, stacks
and queues. It's a fundamental DS.

In linked lists, there's no random access in the sense that when looking for sth, you have to actually traverse the list, but with hash tables, we can find things
**right away**. With arrays, we can find things through indexes.

Linked lists are ordered unlike hash tables.

If we had a large number of items in an array and we keep adding to that array, we'd have to have excessive overhead cost for copying the array in memory and doubling up
the space when it reaches the limit to create a larger array. Versus a linked list where we can have a fast insertion and deletion, especially once we have a 
reference to where we want to insert or delete that node. This also becomes really fast when it's at the beginning or end of the list(we're gonna see this in stacks and
queues).

**The primary reason to choose a linked list over sth like an array, is simplicity and ability to grow and shrink as needed.**

Linked lists are used in file systems or browser history when you go back and forth on a browser, because you can traverse one by oen from one place to another and
remember in hash tables, how we had this issue of collision and when we had a collison, when two or more key-value pairs had collision, we combined them into
nodes and the first node pointing to the next one and ... .

If you look at the hash table implementation in this course and in `set` method, we did a check to check if a memory address 
exist and if it does, we used an **array** to push our items in case we had multiple items(when we had a collision), because
sometimes we can set our hash table memory size to be a lot smaller(therefore we might get get collision) like 2 and now you can see why
now instead of using an array which everytime we need to insert a new item, yeah it work, but if we had to delete an item on the
hash table and that item was collided and therefore in an array, we'd have to **unshift** the array which is very slow. So we can use
a linked list so delete becomes easier.

---
### Linked list:
```js
class LinkedList {
    constructor(value) {
        this.head = {
            value: value,
            next: null
        };
        this.tail = this.head;
        this.length = 1;
    }
    append(value) {
        const newNode = {
            value: value,
            next: null
        }
        console.log(newNode)
        this.tail.next = newNode;
        this.tail = newNode;
        this.length++;
        return this;
    }
    prepend(value) {
        const newNode = {
            value: value,
            next: null
        }
        newNode.next = this.head;
        this.head = newNode;
        this.length++;
        return this;
    }
    printList() {
        const array = [];
        let currentNode = this.head;
        while(currentNode !== null){
            array.push(currentNode.value)
            currentNode = currentNode.next
        }
        return array;
    }
    insert(index, value){
        //Check for proper parameters;
        if(index >= this.length) {
            console.log('yes')
            return this.append(value);
        }

        const newNode = {
            value: value,
            next: null
        }
        const leader = this.traverseToIndex(index-1);
        const holdingPointer = leader.next;
        leader.next = newNode;
        newNode.next = holdingPointer;
        this.length++;
        return this.printList();
    }
    traverseToIndex(index) {
        //Check parameters
        let counter = 0;
        let currentNode = this.head;
        while(counter !== index){
            currentNode = currentNode.next;
            counter++;
        }
        return currentNode;
    }
    remove(index) {
        // Check Parameters      
        const leader = this.traverseToIndex(index-1);
        const unwantedNode = leader.next;
        leader.next = unwantedNode.next;
        this.length--;
        return this.printList();
    }
    reverse() {
        if (!this.head.next) {
            return this.head;
        }
        let first = this.head;
        this.tail = this.head;
        let second = first.next;

        while(second) {
            const temp = second.next;
            second.next = first;
            first = second;
            second = temp;
        }

        this.head.next = null;
        this.head = first;
        return this.printList();
    }
}

let myLinkedList = new LinkedList(10);
myLinkedList.append(5)
myLinkedList.append(16)
myLinkedList.prepend(1)
myLinkedList.printList()
myLinkedList.insert(2, 99)
myLinkedList.insert(20, 88)
myLinkedList.printList()
myLinkedList.remove(2)
myLinkedList.reverse()
```

### Doubly linked list:
```js
class DoublyLinkedList {
    constructor(value) {
        this.head = {
            value: value,
            next: null,
            prev: null
        };
        this.tail = this.head;
        this.length = 1;
    }
    append(value) {
        const newNode = {
            value: value,
            next: null,
            prev: null
        }
        console.log(newNode)
        newNode.prev = this.tail
        this.tail.next = newNode;
        this.tail = newNode;
        this.length++;
        return this;
    }
    prepend(value) {
        const newNode = {
            value: value,
            next: null,
            prev: null
        }
        newNode.next = this.head;
        this.head.prev = newNode
        this.head = newNode;
        this.length++;
        return this;
    }
    printList() {
        const array = [];
        let currentNode = this.head;
        while(currentNode !== null){
            array.push(currentNode.value)
            currentNode = currentNode.next
        }
        return array;
    }
    insert(index, value){
        //Check for proper parameters;
        if(index >= this.length) {
            return this.append(value);
        }

        const newNode = {
            value: value,
            next: null,
            prev: null
        }
        const leader = this.traverseToIndex(index-1);
        const follower = leader.next;
        leader.next = newNode;
        newNode.prev = leader;
        newNode.next = follower;
        follower.prev = newNode;
        this.length++;
        console.log(this)
        return this.printList();
    }
    traverseToIndex(index) {
        //Check parameters
        let counter = 0;
        let currentNode = this.head;
        while(counter !== index){
            currentNode = currentNode.next;
            counter++;
        }
        return currentNode;
    }
}

let myLinkedList = new DoublyLinkedList(10);
myLinkedList.append(5)
myLinkedList.append(16)
myLinkedList.prepend(1)
myLinkedList.insert(2, 99)
// myLinkedList.insert(20, 88)
// myLinkedList.printList()
// myLinkedList.remove(2)
// myLinkedList.reverse()
```
---

002 Linked-Lists-Repl
https://repl.it/@aneagoie/Data-Structures-Linked-Lists

004 VisuAlgo-Linked-List
https://visualgo.net/en/list

007 Exercise-Repl
https://repl.it/@aneagoie/Data-Structures-Linked-Lists-Implementation-1

008 Solution-Exercise-Code
https://repl.it/@aneagoie/Data-Structures-Linked-Lists-Implementation-2

009 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Linked-Lists-Implementation-2-

011 Exercise-Repl
https://repl.it/@aneagoie/Data-Structures-Linked-Lists-Implementation-3

011 VisuAlgo-Linked-List
https://visualgo.net/en/list

013 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Linked-Lists-Implementation-4-

014 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Linked-Lists-Implementation-4

016 Singly-Linked-List
https://repl.it/@aneagoie/Data-Structures-Linked-Lists-Implementation-4

017 Solution-Code
https://repl.it/@aneagoie/Data-Structure-Doubly-Linked-List-Implementation

019 Exercise-Repl
https://repl.it/@aneagoie/Data-Structures-Linked-Lists-Implementation-5

020 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Linked-Lists-Implementation

021 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview

021 My-Favourite-Video-Comparing-Linked-Lists-to-Arrays
https://www.youtube.com/watch?v=DyG9S9nAlUM
