# Section 6: 06 - Data Structures Arrays

## 63-001 Arrays Introduction
## 64-002 Static vs Dynamic Arrays
## 65-003 Quick Note Upcoming Video
When we build data structures from scratch in this course, we will be using the Javascript's Class keyword to create these data structures. 
I have picked this way of doing things since it would be most familiar with most languages. If you would like to be a little bit more familiar with 
classes and how to create them, I have added an extra video from one of my other courses: The Complete Web Developer: Zero to Mastery which goes over this topic in the next lecture.

If you are already familiar with this topic you can skip over to the Implementing An Array video.

Ps, throughout the course I use var, let, and const to declare variables. It is not important that you understand the differences between them for this course
, but if you are curious, I recommend reading this: https://dev.to/sethusenthil/var-vs-let-vs-const-1cgc
## 66-004 Optional Classes In Javascript
## 67-005 Implementing An Array
## 68-006 Strings and Arrays
## 69-007 Exercise Reverse A String
## 70-008 Solution Reverse A String
In JS we can actually index into strings like arrays and access each character with [] notation. So we don't have to run any split() .

Tip: We can spread a string into an array without using split() :
```js
const string = 'hello';
console.log([...string]);
console.log(string.split(''));
```

## 71-009 Exercise Merge Sorted Arrays
## 72-010 Solution Merge Sorted Arrays
## 73-011 Interview Questions Arrays
Look at the file.

## 74-012 Arrays Review
Arrays are good at having sorted data. When it comes to sorting, arrays are awesome. Because they're in memory in sequential order according to their index(so the 
elements of array are close to each other in memory).

Arrays have slow inserts and deletes, because whenever the element that we want to insert or delete, won't be at the start or end of array, we need to shift the array.

