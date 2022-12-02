# Section 13: 13 - Algorithms Sorting

## 153-001 Sorting Introduction
Sorting is not a big deal when it comes to small input data. Kinda like when we talked about Big O . We don't care about small inputs. That's
easy to do, especially with our modern fast computers. It starts costing companies a lot of money, when we have to perform operations on larger and
larger datasets. We can;t usually just use a builtin sort method that comes with the language, we usually need custom sort methods based on the data, so that
we can lower the costs. Most places sort their data or pre-processes it.

## 154-002 The Issue With sort()
In js, the sort() method the way it sorts numbers, is that it actually converts them to string. So isntead of just comparing numbers, it first **converts
that number to string and then grabs the character code of first index of string**, for example: `'65'.charCodeAt(0)` which will give us a number
which is the unicode and then it sorts those numbers instead of original numbers.

Different engines implement js methods differently. So the time and space complexity varies from engine to engine. The v8 engine would use a different
JS implementation than firefox and what kind of sort algorithm they use underneath the hood is dependent on the browser(actually the JS engine used by
the browser).

Another example of weirdness of builtin sort():
If we were sorting an array of spanish words, because of the unicode characters, the `a` in spanish, is not the actual a that would come before `c` in spanish!
So in this case, to solve this problem, we would have to pass a function to sort() like:
```js
const spanishWords = ['...', '...'];
spanishWords.sort(function (a, b) {
    return a.localeCompare(b);
});
```


## 155-003 Sorting Algorithms
Elementary sorts: bubble sort, insertion sort, selection sort

Merge sort and quick sort are more complex that most of the time can be more efficient than the first ones.

## 156-004 Bubble Sort
## 157-005 Exercise Bubble Sort
File attached
## 158-006 Solution Bubble Sort
## 159-007 Selection Sort
## 160-008 Exercise Selection Sort
File attached
## 161-009 Solution Selection Sort
## 162-010 Dancing Algorithms
## 163-011 Insertion Sort
Insertion sort is not the most efficient algo either, but there's cases where it's actually extremely fast. It's useful for times
when you're pretty sure the list(array) is almost sorted, or it's already sorted. In the best case scenario, you can get O(n) or linear time
when the list is almost sorted.

How it works?

Look at the first item and just leave it where it is. Now look at the next item, if it's smaller than first item, swap them. Then the third element.
Hey third element! Where are you in relation to the first and second elements? If it's less than those, shift those two and put the third item in the beginning.
Now repeat these steps... .

This type of sorting performs really well when it comes to small datasets.


## 164-012 Exercise Insertion Sort
File attached
## 165-013 Solution Insertion Sort
## 166-014 Merge Sort and O(n log n)
Let's look at merge sort and quick sort. Unlike bubble, insertion and selection sort, **the merge and quick sort use the divide and conquer technique(and the
idea of recursion)** which means when looking through a phone book, we open up that book not from the first page but from the middle page and we 
keep breaking up the pages until we find the name we're looking for.

So they use divide and conquer and the idea of recursion to divide the problem down to do work on each subset and then combining the solutions.

Anytime you see a divide and conquer, it usually gives you a `log n` advantage.

## 167-015 Exercise Merge Sort
File attached
## 168-016 Solution Merge Sort
## 169-017 Stable VS Unstable Algorithms
File attached
## 170-018 Quick Sort
Quick sort uses pivoting technique to break main list into smaller lists and the smaller lists use the pivoting technique until they are sorted.

Quick sort can be implemented in different ways, but the idea of a pivot is the same.

Quick sort is really useful and between quick sort and merge sort, those are the most used sorting algorithms.

Quick sort worst case is when the pivot is the smallest or the largest item in the list, because then, you're not really splitting the list in half and
because of this, you want to make sure that you pick a good pivot for quick sort. So in those cases, merge sort might be better.

If your list was pre-sorted for whatever reason and in that list if we pick the pivot to be the first item or the last item,
then our sorting would take a long time because again, the list will not really be split in half and ideally in a quicksort, you're picking the pivot
intelligently based on your list.

There are a lot of variants to quicksort and there's different implementations.

Quicksort is usually the fastest on average, but the one downside is that it has some pretty nasty worst case behaviors. So if you
have to guarantee no bad data, or you can't guarantee that the pivot's gonna be good, then you should be avoiding quick sort. But on average
it's usually the best sorting algo like merge sort.

When should we use which sorting algo?

## 171-019 Optional Exercise Quick Sort
File attached
## 172-020 Which Sort Is Best
When should you use insertion sort?

Insertion sort:

Insertion sort should be used with only a few items. If your input is small or items are mostly sorted, it's really fast. It uses little space and most 
importantly, it's easy to implement in code. So only a few items and mostly sorted data, you should use insertion sort.

Bubble sort:

You're never gonna use bubble sort. It's only used for educational purposes.

Selection sort:

Most likely, you won'be using it.

Merge sort:

Merge sort is really good because of divide and conquer. It's fast and because best, average and worst cases are always O(nlog(n)) which means we always divide up
the list evenly, you can always guarantee that this is gonna be the case which is not the case for most other algorithms. So if you're worried about
worst case scenarios, you should use merge sort. But if you wanna sort in-memory on your machine and you're worried about space complexity, 
merge sort is gonna be expensive(space complexity: O(n)). However, if you had huge files that can be sorted in memory, so you have a external sorting that you need,
maybe like a process outside of memory, it's suitable for external sorting, then merge sort is good because we won't care as much about space complexity. 

Quick sort:

Quick sort is better than merge sort, it's probably one of the most popular sorting algos. But one downside of it is it's worst case. If you don't pick
the pivot properly, you could have a slow sorting and if you're worried about the worst case, then your rather pick sth else.

Heap sort:

Is similar to quick sort and merge sort, but it has a space complexity of O(1) . Heap sort can sort in-place. Isn't this the best algo?
On average, it's slower than quick sort in most cases.

If you're really worried about worst case and memory complexity, you might use heap sort, but most of the time you're using quick sort or mergesort.

## 173-021 Resources Heap Sort
TODO
File attached
## 174-022 Radix Sort + Counting Sort
Merge sort and quick sort although they're harder to implement, are the most often used algos in real life because they use divide and conquer to get us
O(n log n). But can we beat O(n log n) ?

A: Mathematically, it's impossible to improve on this. Because O(n log n) means that we have to sort by comparison. All of the sorting algos that are
under comparison sort in slide have to compare every number to each other. But there is one exception to this rule: You can improve this, if you don't make
comparisons. What does it mean? There's a small section of inputs that we can actually beat O(n log(n)) and these are called non-comparison sorts.

Counting sort and radix sort only work with numbers, specifically integers in a restricted range. So if you have only numbers and the range of those numbers
go from for example 0 to 100(they only work for fixed length integers), you would use sth like these to make things fast.
They only work with numbers because of the way numbers are stored in memory.

## 175-023 Resources Radix Sort + Counting Sort
File attached
## 176-024 Exercise Sorting Interview
## 177-025 Solution Sorting Interview
Q1:

Insertion sort. The input is small, we need sth simple. This algo is fast on small inputs. Also it has space complexity of O(1) . It also could be that
these 10 schools are already pre-sorted or nearly sorted, so insertion sort is good for these type of things.

Q2:

radix or counting sort. Because a bid is usually a number between 1$ to 50000$, probably even less when it comes to payments on eBay, let's say 1$ to 100$.
So we have fixed length numbers of integers that need to be sorted. So we would use radix or counting to beat that O(n log(n)) , knowing that the bids
are always gonna be numbers within a certain range.

Q3:

Quick sort. Sport scores can vary, there's decimal points, there's different formats such as tennis and soccer. Although we might have the worst case,
I doubt that the scores are gonna be sorted because they're just so many different kinds, but I'm also worried about in-memory sorting. If we use
mergesort, it might be a little to much for this, because of our increased space complexity.

Q4:

Merge sort

If data that you wanna sort can't be fit all into memory(a lot of data to handle like big DBs), you should use **merge sort**.
Also because the data is so big, we're worried about performance, so we don't want the worst case of quick sort(O(n^2)), we want to make sure
no matter what, we're gonna get `O(m log(n))`.

If the data is huge but it's mostly sorted, we can use **insertion sort**. Insertion sort for pre-sorted list, is gonna work better than any type of sorting algo.

We can't fill all the data into memory to sort it as the question says, so we probably need to sort it externally. Why merge sort?
Because it sounds that we're not gonna be sorting really in memory because the data is big, but because the data is big, I'm really worried about the performance. So
we don't want the worst case of quick sort which is O(n^2) , we want to make sure that no matter what, I'm gonna get O(n log(n)) .

Q5:

Insertion sort

We have a massive list of udemy reviews. Why insertion sort? Although the data might be huge in this case, we're assuming that most of the previous data(the data
before adding our 2 new reviews) is already sorted. **Insertion sort for pre-sorted list is gonna work better than any other type of sorting.**  

Q6:

At first, we would use radix or counting sort IF the temperatures have no decimal places. If we're saying the range is between -30 to 40 degrees. That's an
integer number between a small range. That would work well with radix or counting sort. But if we want to sort through data that also has temperatures that are
really accurate and have decimal points which you can't do with radix or counting sort, then we're gonna use **quick sort**, just so that we can do in-memory sorting and
hopefully save on that space complexity.

Q7:

We don't have enough info to make a decision here. Maybe we would use **merge sort** if we have enough memory and memory isn't too expensive on the machine.
Or we'll use quick sort, if we're not too worried about worst case and the username DB is not that large(just to save on that memory space, if it's
expensive) and also IF we can pick a good pivot.

Q8:

Bubble sort and selection sort.


## 178-026 Sorting In Your Language
The sort builtin function in programming languages in most cases is gonna be either quicksort or insertion sort and merge sort combined together.

In js, there's no requirement to JS as to which sorting algo to use. We have ecmascript in JS which is the standard but because the standard doesn't mention how 
this should be implemented, different browsers that have different JS engines, they all implement it differently.

In mozilla, they use mergesort and in V8, sort is implemented with quicksort and also insertion sort for the smaller arrays.

## 179-027 Sorting Review

--- 


002 MDN-sort-
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort

002 localeCompare-
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare

003 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview-click-here-for-course-link

003 Toptal-Sorting-Algorithm-Animations
https://www.toptal.com/developers/sorting-algorithms

004 Big-O-Cheat-Sheet
http://bigocheatsheet.com/

005 Exercise-Repl
https://repl.it/@aneagoie/bubbleSort-exercise

006 Solution-Code
https://repl.it/@aneagoie/bubbleSort

008 Exercise-Repl
https://repl.it/@aneagoie/selectionSort-exercise

009 Solution-Code
https://repl.it/@aneagoie/selectionSort

010 Dancing-Algorithms
https://www.youtube.com/user/AlgoRythmics/videos

012 Exercise-Repl
https://repl.it/@aneagoie/insertionSort-exercise

013 Solution-Code
https://repl.it/@aneagoie/insertionSort

015 Exercise-Repl
https://repl.it/@aneagoie/mergeSort-exercise

016 Solution-Code
https://repl.it/@aneagoie/mergeSort

019 Exercise-Repl
https://repl.it/@aneagoie/quickSort-exercise

019 Solution-Code
https://repl.it/@aneagoie/quickSort

024 Sorting-Interview
https://repl.it/@aneagoie/sorting-exercise

025 Solution
https://repl.it/@aneagoie/sorting-exercise-solution

027 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview-click-here-for-course-link
