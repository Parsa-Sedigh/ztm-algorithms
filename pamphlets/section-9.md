# Section 9: 09 - Data Structures Stacks + Queues

## 109-001 Stacks + Queues Introduction
These two are very similar. They are both what we call linear data structures and linear data structures allow us to traverse data sequentially, one by one. In which
only one data element can be directly reached.

The reason that these are similar is that they can be implemented in similar ways and the main difference is only how items get removed from these data structures.

Unlike an array, in stacks and queues, there's no random access operation, you mainly use stacks and queues to run commands like push, peek, pop, all of which
deal exclusively with the element at the beginning or the end of the DS.

Does it sound limiting that with stacks and queues, we usually only can access the first or the last element in the DS? Why would we ever want to use sth like this?

In CS, you will see that we can build things like stacks and queues which are using arrays or linked lists, except unlike arrays and linked lists, we have **less**
methods or actions that we can perform on stacks and queues and sometimes it's good to have these higher level data structures that are built on top of
lower level ones like linked lists and arrays, to **limit** the operations you can do on them. That's actually a benefit.

## 110-002 Stacks
**LIFO** -> last in first out

They are good when you need to know the very last value that was seen or added and they're important in language specific engines. Most programming languages are
modeled with the stack architecture in mind and when functions get called in a programming lang, usually hey follow this model of last in, first out.
A function within a function within a function gets called and then we start popping those functions until we get to the beginning.

Stacks can be used in browser history for example going forward or backward in browser history. Or undoing and redoing(forwarding) in text, the idea comes from stacks. That
is you store the previous state of your work in memory in such an order that the last one appears first.

peek -> view the top most plate

Lookup in stack is **O(n)**(it's a heavy operation) and you usually don't want to traverse through an entire stack. 

## 111-003 Queues
**FIFO** -> first in, first out

If you had any sort of wait-list app to buy tickets, that uses queues. It can be used in Uber or lift when you want to grab a ride. The person that requested the
ride first, will get it.

enqueue -> add to the queue
dequeue -> remove the **first** item
peek -> view the **first** item(peek in the stack, will get the last item)

You usually don't do a lookup in queue, like stack.

Q: Why would you **not** want to use an array to build a queue?

A: It's very inefficient. When we remove the first item from the queue(O(1)), in arrays, if you unshift sth(remove the first item), you're gonna have to shift all those
indexes. So creating a queue from arrays, although you can do it, is really bad.

Unshift in arrays -> remove the first item

## 112-004 Exercise Stacks VS Queues
JS doesn't have it's own stacks or queues data structures.

There are two ways we can build stacks and queues, with arrays or linked lists.

**Q:** Why would we want to build stacks and queues with arrays vs using linked lists?

## 113-005 Solution Stacks VS Queues
For stacks, both arrays and linked lists are gonna work fairly well. So it depends on the pros and cons of arrays and linked lists and what your priorities are.
We've talked about these. But one major thing is that arrays allow sth called **cache locality** which makes them technically faster when accessing it's items in memory because
they're right next to each other vs a linked list that has them scattered all over memory and also linked lists have extra memory associated with them because we have to
hold on to those pointers. But on the other hand, they have more dynamic memory and we can keep adding things to the list vs an array where you have either a static or 
dynamic array that has certain amount of memory and as soon as it's about to reach it's limit, it's gonna have to double up that memory and create
new space for it somewhere in memory. So you have to think about what sort of operations you're gonna do and why your priorities are, to decide which one you want. But they
could both work.

Queues on the other hand, you would never want to build it with an array. So ideally you would want to implement them with linked lists.
Why?

A: Arrays have indexes associated with them and unshifting elements is an expensive operation(O(n)) because we need to shift the indexes. Versus removing the
first item in linked list is O(1) or constant time.


## 114-006 Quick Note Upcoming Video
File attached
## 115-007 Optional How Javascript Works
Q: What is a program?
A: A program has to allocate memory, otherwise we wouldn't be able to have variables or even have a file on our computer. It also has to parse and execute scripts which means
read and run commands.

The v8 engine reads JS code and changes it into machine executable instructions for the browser. 

The engine(like v8) consists of 2 parts:
1) a memory heap
2) a call stack

The memory heap is where the memory allocation happens and in call stack is where your code is read and executed, it tells you where you are in the program.

Global variables are bad because if we don't forget to cleanup after ourselves, we fill up the memory heap and eventually the browser will not be able to work.

JS is a single threaded lang that can be non blocking.

Single threaded means that it has only 1 call stack. You can do only 1 thing at a time. If a lang has multiple call stacks, that lang is called multi-threaded.

What stack overflow means?
When call stack gets bigger and bigger until it doesn't have enough space anymore.

How can we recreates a stack overflow?
We can do a recursion:
```js
function foo() {
    foo();
}

foo();
```

Async programming in js:
Now that we know js is single threaded, how do we get not blocked on lines of code that takes a lot of time to execute? Like a timeout with 10 seconds?

In order for JS to run, in addition to JS engine with memory heap and call stack, we need more than the JS engine. We need a JS runtime environment and it's part of
the browser(and we have nodejs and deno too) and they have Web APIs(like setTimeout), callback queue and an event loop.

Event loop keeps checking and says: Is the call stack empty? and if the call stack is empty, it's gonna say: Do we have any callbacks? So it's gonna check the
callback queue and checks if there's sth there. If there is some, it's gonna move one of them at a time to call stack and that code will run there in call stack.

Callback functions gets run in the background and then if they got triggered, they go to callback queue and back to the call stack by event loop.

## 116-008 Exercise Stack Implementation (Linked Lists)

## 117-009 Solution Stack Implementation (Linked Lists)

## 118-010 Exercise Stack Implementation (Array)
Arrays already have push and pop methods, so implementing stacks with arrays is gonna be easy.
Also, we don't need `top`, `bottom` and `length` properties in the Stack class, because we're using arrays and they have indexing ability.

`peek` means we want to see the end of the stack(the very top thing which in stack means the very last thing we pushed) and in queues, peek would give us the first item.

One of the nice things about using an array is arrays at least in JS, already act like stacks and it makes things simple when implementing stacks with them.

## 119-011 Solution Stack Implementation (Array)
**dequeue** is similar to **pop**, except we grab the node from the beginning instead of the end.

## 120-012 Exercise Queue Implementation

## 121-013 Solution Queue Implementation

## 122-014 Queues Using Stacks
One of the most common interview questions is: **implement a queue using stacks**. This is an easy one if you create a stack using arrays.

## 123-015 Stacks + Queues Review
We learned how to build stacks with arrays and linked lists and also why we might not want to use an arrays to build queues, so we build queues with linked lists.

**So we wouldn't want to use an array for our queue.**

- Stacks and queues are great for some fast operations such as removing or inserting at the end of the DS.
- We can also access the very first item in a queue or very top item in a stack
- All of our data in these two data structures are ordered, which is nice

Note: We don;'t usually use our stacks or queues to do any sort of lookup or search through the DS. They are useful sine they restrict our use of what we can do with them so they
make sure what we're allowed to do with them, are gonna be really fast.

---

008 Exercise-Repl
https://repl.it/@aneagoie/Data-Structures-Stacks-Implementation-linked-list-1

009 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Stacks-Implementation-linked-list

010 Exercise-Repl
https://repl.it/@aneagoie/Data-Structures-Stacks-Implementation-linked-list

011 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Stacks-Implementation-array

012 Exercise-Repl
https://repl.it/@aneagoie/Data-Structures-Queue-Implementation-1

013 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Queue-Implementation

014 Solution-Code
https://repl.it/@aneagoie/Data-Structures-Queues-2-stacks

014 Questions-From-Leetcode
https://leetcode.com/problems/implement-queue-using-stacks/description/

015 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview
