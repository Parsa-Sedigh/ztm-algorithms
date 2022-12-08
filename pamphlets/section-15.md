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
## 203-004 Fibonacci and Dynamic Programming
## 204-005 Dynamic Programming
## 205-006 Implementing Dynamic Programming
## 206-007 Interview Questions Dynamic Programming
File
## 207-008 Dynamic Programming Review

---

003 Repl-Code
https://repl.it/@aneagoie/Dynamic-Programming

006 Solution-Code
https://repl.it/@aneagoie/Fib-Dynamic-Programming
