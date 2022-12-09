# Section 15: 15 - Algorithms Dynamic Programming 

## 200-001 Dynamic Programming Introduction
Dynamic programming is just an optimization technique using sth called caching. If you have sth that you can cache, then you can use
dynamic programming. the fun fact is dynamic programming actually means nothing! It's a buzzword!

Dynamic programming is a way to solve problems by breaking them down into a collection of sub-problems, solving each of those sub-problems just once and
storing their solutions, in case next time the same sub-problem occurs. 

## 201-002 Memoization 1
Caching is a way to store values so you can use them later on.

Memoization is a specific form of caching that involves **caching the return value** of a function based on it's parameters and if the parameters of 
that function doesn't change, then it's memoized which means it uses the cache since it's calculated the same thing before with the same parameters and
therefore it will return a cached version. If the parameters change, it's gonna calculate it.

Memoization is a way to remember a solution to a sub-problem, so you don't have to calculate it again.

We use memoization a lot in dynamic programming.

js tip:
```js
if (a.b) {}
// is similar to:
if (b in a) {}
```

## 202-003 Memoization 2
Ideally, we don't want to fill the cache in the global scope(to be living outside of the function in global place). It's a good practice 
to have memory or in this case the cache, to live inside of the function and not polluting the global scope. In JS, we can use closures for this.

After brining the cache declaration variable into the memory, each time the function runs, the cache gets reset. To get around this,
we can use closures in JS. We can return another function inside the memoized function and because sth called closure, we're able to access
the cache variable inside that inner function. This is an approach to avoid that cache being in global scope.

```js
function memoizedAddTo80() {
    let cache = {};
    
    return function (n) {
        if (n in cache) {
            return cache[n];
        } else {
            console.log('long time');
            cache[n] = n + 80;
            return cache[n];
        }
    }
}
```

Now we can do:
```js
const memoized = memoizedAddTo80();
memoized(5); // will go into else
memoized(5); // will go in if statement because it's the same param that we have in cache which is a hash table
```

## 203-004 Fibonacci and Dynamic Programming
When we say dynamic programming, just think about caching or about optimizing sth using a cache.

Fibonacci sequence with recursion is `O(2^n)` really bad time complexity! and remember with recursion, every nested function call adds to the call stack which
increases memory complexity.

How can we make it more efficient?

We can avoid this using dynamic programming which gives us O(n) in this case! That's right, we can go from O(2^n) to O(n) . So we can reduce the time
and space complexity of our algo by using memoization and we can do this because the solution to each sub-problem is **optimal** which means we do a lot
of problems repeatedly that are the same.

## 204-005 Dynamic Programming
When we want to calculate for example fib(7) , we're gonna calculate f(1) 5 times! or fib(2) would be called multiple times(same calculation
being repeated multiple times)!

With dynamic programming we can optimize this and use memoization by saying: To calculate fib(7), go recursively down to fib(6) ... fib(1) .
Now as we go back to fib(7) which means as we start to `return` the statements, since we've already calculated these fib(2) and ... , we can return a 
memoized version, so these calculations in the pic are no longer needed, so that we can just ask the memoized version of the blue ones:
![](../img/204-005-1.png ) .


You can think of dynamic programming as combining divide and conquer where we use recursion and using cache and memoization to get performance.

Set of rules for using dynamic programming(to see if a problem can use dynamic programming to optimize it):
1) First ask: Can the problem be divided into sub-problems? Is it a tree like structure 
2) where each problem is broken down into smaller problems, into smaller problems into ... which usually indicates a recursive solution?
3) this question is important because you can have tree like structures that don't have repetitive sub-problems but if these sub-problems are
repetitive, that is we're doing the same calculation over and over in these sub-problems?
4) if the answer is yes, then we can memoize these sub-problems. Once we do this, we're gonna see benefits and these benefits are used all over
computer science improve performance

So when a problem ha solutions composed of solutions to the same problem with smaller inputs, each sub-problem can be solved once and the result of
each sub-problem is stored in a table like a cache such as hash table for future reference to avoid re-calculations and you can
use this table to obtain the original solution of a repeated problem.

## 205-006 Implementing Dynamic Programming
Since we don't want to reset the cache, return another function inside the memoized fibonacci function 

Dynamic programming: If there's any repeated calculation, memoize the result of a function so that if the params are the same, we check in the cache first for
the result to avoid re-calculating the function with same params.

We made huge savings on time complexity but one drawback is that we increased the space complexity. With first approach, we had to add functions to the
call stack, but once we got to the bottom(fib(1) or fib(0)), we popped off the stack so that the stack was as deep as the tree. But with the memoized
version we also have the cache hash table that we have to store in memory. So we sometimes need to trade off space complexity for better time complexity.
In this case it worth it.

## 206-007 Interview Questions Dynamic Programming
File TODO
## 207-008 Dynamic Programming Review
There is one other way of incorporating dynamic programming and it's called bottom-up approach.

There's a third way to solve fibo bad time complexity problem using bottom-up approach. This type of approach avoids recursion.

---

003 Repl-Code
https://repl.it/@aneagoie/Dynamic-Programming

006 Solution-Code
https://repl.it/@aneagoie/Fib-Dynamic-Programming
