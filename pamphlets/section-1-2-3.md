# Section 1

## 1-001 How To Succeed In This Course
## 2-002 Join Our Online Classroom!
## 3-003 Exercise Meet Your Classmates and Instructor
## 4-004 Monthly Coding Challenges, Free Resources and Guides
001 Interview-Mind-Map
https://coggle.it/diagram/W5u8QkZs6r4sZM3J/t/master-the-interview

001 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview

# Section 2
## 5-001 Section Overview
## 6-002 Resume
## 7-003 Exercise Resume Walkthrough
## 8-004 Resume Review
## 9-005 Resources Resume Templates
## 10-006 What If I Don't Have Enough Experience_en
## 11-007 Optional Exercise Github Master
## 12-008 LinkedIn
## 13-009 Optional Exercise LinkedIn Endorsements
## 14-010 Portfolio
## 15-011 Resources Free Portfolio Templates
## 16-012 Email
## 17-013 Resources Email
## 18-014 Where To Find Jobs
## 19-015 Resources Where To Find Jobs
## 20-016 When Should You Start Applying
## 21-017 Section Summary
## 22-018 Monthly Industry Updates
001 Interview-Mind-Map
https://coggle.it/diagram/W5u8QkZs6r4sZM3J/t/master-the-interview

002 Resume-Template
https://www.resumemaker.online/

003 Resume-Cheat-Sheet
https://github.com/aneagoie/resume-checklist

004 JobScan
https://www.jobscan.co/

006 ZTM-Open-Source-Community
https://github.com/zero-to-mastery/start-here-guidelines

006 ZTM-Job-Board
https://github.com/zero-to-mastery/ZtM-Job-Board

## Section 3

## 23-001 Setting Up Your Environment
## 24-002 Section Overview
## 25-003 Python, Java, CC++, C#, Golang, Swift, Kotlin, TypeScript, + Perl Solutions!
## 26-004 Big O Cheatsheet
## 27-005 What Is Good Code


## 28-006 Big O and Scalability
How long it takes for this function to run?
```js
let t0 = performance.now();
// some loop or code
let t1 = performance.now();

console.log('Call to function took ' + (t1-t0) + 'milliseconds')
```

```js
const largeArr = new Array(100).fill('nemo');
```

When we talk about bigO and scalability of code, we mean when we grow bigger and bigger with our input, how much does the algo or function slow down?

Instead of using performance.now() and using time to measure the efficiency of our function, we can just calculate how many operations a computer has to
perform. Because each operation takes time on a computer.

## 29-007 O(n)
O(n) -> linear time(proportionally)

BigO doesn't measure things in seconds. Instead, we're focusing on how quickly our runtime grows? We do this by using the size of the input which we
call `n` (or anything else that we want really!) and compare to the number of operations that increase. That's what scalability means: As things grow larger and larger,
does it scale?

## 30-008 O(1)
O(1) -> constant time . The number of operations is 1, no matter how big the number of inputs is.

O(1) means it's only gonna run once, when we run that function, it doesn't matter how big the input is, it just runs once.

## 31-009 Exercise Big O Calculation

## 32-010 Solution Big O Calculation
```js
// What is the Big O of the below function? (Hint, you may want to go line by line)
function funChallenge(input) {
  let a = 10; // O(1)
  a = 50 + 3; // O(1)

  for (let i = 0; i < input.length; i++) { // O(n)
    anotherFunction(); // O(n)
    let stranger = true; // O(n)
    a++; // O(n)
  }
  return a; // O(1)
}
```

## 33-011 Exercise Big O Calculation 2
It's time to try calculating the Big O based on what you have learned up until this point. Don't worry though, we will go over the solution in the next video :)

Exercise can be found here

If you have any questions, reach out in our private Discord chat community in the #helpme channel (Link can be found in Lecture 3 on your Udemy course dashboard)!

By the way, you may notice that there are different "types" of O's in the Big O Cheatsheet. You can think of them all as the same thing as we are almost 
always interested in the worst case (Big O), but for those that are curious, have a read at this: 
[link](https://www.quora.com/What-is-the-difference-between-big-oh-big-omega-and-big-theta-notations)

## 34-012 Solution Big O Calculation 2
## 35-013 Simplifying Big O
## 36-014 Big O Rule 1
## 37-015 Big O Rule 2
O(2n) -> drop the constants -> O(n)
O(n/1000) -> drop the constants -> O(n)

## 38-016 Big O Rule 3
What is the bigO of this function?
```js
function compareBoxesTwice(boxes, boxes2) {
    boxes.forEach(function (box) {
        console.log(box);
    });

    boxes2.forEach(function (box) {
        console.log(box);
    });
}
```
The result is: `O(a+b)` or `O(boxes1+boxes2)` and **NOT** O(n).
`a` is for the first for loop which uses the first input

## 39-017 O(n^2)
Q: Log all pairs of an array:
A:
```js
const boxes = [1, 2, 3, 4, 5];

function logAllPairsOfArr(array) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j< arr.length; j++) {
            console.log(arr[i], arr[j]);
        }
    }
}

logAllPairsOfArr(boxes)
```
If you see nested loops, that means, instead of using +, so `O(n) + O(n) = O(n)`, we use multiplication(*). So: `O(n) * O(n) = O(n^2)`.

Q: What is BigO?
```js
function compareBoxesTwice(boxes, boxes2) {
    boxes.forEach(function (box1) {
        console.log(box1);
        
        boxes2.forEach(function (box2) {
            console.log(box2);
        });
    });
}
```
A: `O(a*b)`. Note: Different inputs should have different variables when writing the BigO notation.

## 40-018 Big O Rule 4
Big O means time complexity.

O(n + n^2) -> drop the non-dominant terms -> O(n^2) . Because we only worried about scale. We don't care about insignificant items.

Note: If you have 3 nested loops(O(n^3)), 99% of the time, that's usually a bad idea, it scales really badly and most likely you're doing sth wrong!

## 41-019 Big O Cheat Sheet
2 separate inputs should have 2 separate variables in BigO notation.

## 42-020 What Does This All Mean
Scalable means we worry about large inputs.

In JS, `unshift()` is **O(n)**. 

Data structures are ways to store data and algorithms are functions or ways to use data structures to write our programs.

2 rules of good code: readable and scalable.
Scalable means Big O notation. **But!** actually it means 2 things: 
1) speed
2) memory

We're gonna use BigO to see what is a good solution to a problem and what is a bad solution to a problem.

## 43-021 O(n!)
This is called **factorial time**.

If you're writing any code that has this big o notation, you're definitely doing sth wrong! You're probably never gonna encounter it.
It means we're adding a nested loop for every input that we have. Or you're adding a loop for every element that you're iterating over.



## 44-022 3 Pillars Of Programming
For a code being scalable, we want to consider 2 things:
1) speed: How fast is our runtime on the code? How much time does it take for a function to run? How many operations does it cost?
2) memory: There's another aspect when it comes to machines, in machines we have 2 valuable resources: first one was the time and speed of our code and the
   other one is memory.

Speed is type of code that we call time complexity, has a big O time complexity that is efficient, it scales well.

To measure how much memory is used, we use big O once again to talk about space-complexity. So the same notation, but different topic.

One is space, the other one is time. One is speed, the other one is memory.

Mose code solutions, there's usually a trade-off between speed and memory. You want things to go faster, then you might have to sacrifice more memory. You want less memory,
then you might have to sacrifice with increased speed(I think less speed???).

## 45-023 Space Complexity
## 46-024 Exercise Space Complexity
## 47-025 Exercise Twitter
## 48-026 Optional Javascript Loops
## 49-027 Section Summary
