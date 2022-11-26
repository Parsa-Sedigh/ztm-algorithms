# Section 12: 12 - Algorithms Recursion

## 151-001 Introduction to Algorithms
## 152-002 Recursion Introduction
Recursion isn't technically an algorithm. It's more of a concept, we use it to write algorithms.

For example when we get into sorting and searching through a BST, we're gonna be using recursion.

When you're searching on your files on computer, you want to look at folders recursively, or when we do DOM traversal(tree traversal in general).

Recursion is when you define sth in terms of itself. Recursion is good for tasks that have repeated subtasks to do.

## 153-003 Stack Overflow
If you run this function:
```js
function inception() {
    inception();
}
```
You will get an error that says: `Uncaught RangeError: Maximum call stack size exceede` and eventually, if google chrome console(or other envs) doesn't stop this,
it's gonna crash. This is called stack overflow. 

If you put a `debugger` in the place where the function gets called over and over again, you will see in the call stack of devtools that the function name is
added again to the call stack and never gets removed but will added to the call stack again and again.
![](../img/153-003-1.png)

One of the biggest problems with recursion is that it can be very dangerous because we can run programs that overflow(never stop).
Also it costs memory. The **call stack** is holding these function calls and one of the downsides of recursion is that we have to hold on to these function
calls and remember them one by one, which can get expensive.

So the computer needs to allocate memory to remember things. Stack overflow can occur when we have recursion and there's no way to stop this recursive call.
So the call stack won't have any memory left and stack overflow would occur.

## 154-004 Anatomy Of Recursion
Every recursive function needs to have sth called a base case or a stop point.

Recursive functions have 2 paths:
1) the recursive case 
2) base case: stop calling the function

Q: What will the console look like after running this?
```js
function inception() {
    inception();
    console.log('hello');
}
inception();
```

A: Nothing will be logged to the console. Because we never reach to the log line because of stack overflow(RangeError: Maximum call stack size exceeded error).

In this example:
```js
let counter = 0;
function inception() {
    if (counter > 3) {
        return 'done';
    }
    
    counter++;
    inception();
}
inception();
```
After calling the function multiple times, we would have multiple inception functions in the call stack and after the counter became 4, the last inception function
call would get removed from callstack and the Return value would be 'done', but after the first call stack pop, the Return value would become undefined. Because
we don't return the result of calling inception. Yeah, in the last call stack value which is the last inception call, we return 'done', but the function calls
before that last one, are only calling inception() without returning the result of calling it. So we need to write: `return inception()` at the last line of function
to actually propagate the result of calling that function recursively.

So there's usually a base case and you always want to make sure you `return`, so that the value you want, gets bubled up all the way to the first call stack value(which
would be a function call definitely, because it's a **call** stack, right? It remembers function calls). 

To build recursive functions:
1) identify the base case(when to stop?)
2) identify the recursive case(when we don't go to the base case)
3) get closer and closer and `return` when needed. Usually you have 2 return keywords(for the base case and recursive case, because you want to return sth at the
end of the function)

So everytime we recurse, the function gets closer and closer to the base case and eventually when it gets to the base case, it finally returns and pops functions off
the stack.

## 155-005 Exercise Factorial
## 156-006 Solution Factorial
## 157-007 Exercise Fibonacci
## 158-008 Solution Fibonacci
## 159-009 Recursive VS Iterative
## 160-010 When To Use Recursion
## 151-011 Exercise Reverse String With Recursion
File attached

## 152-012 Recursion Review

---

005 Exercise-Repl
https://repl.it/@aneagoie/Recursion-factorial

006 Solution-Code
https://repl.it/@aneagoie/Recursion-factorial-solution

007 Exercise-Repl
https://repl.it/@aneagoie/Recursion-fibonacci

008 Solution-Code
https://repl.it/@aneagoie/Recursion-fibonacci-solution

009 What-is-Tail-Call-Optimization
http://2ality.com/2015/06/tail-call-optimization.html

010 Tree-Data-Structure-Code
https://repl.it/@aneagoie/Data-Structures-Trees

011 Exercise-Repl
https://repl.it/@aneagoie/reverseString-exercise

011 Solution-Code
https://repl.it/@aneagoie/reverseString

012 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview-click-here-for-course-link
