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
## 164-012 Exercise Insertion Sort
File attached
## 165-013 Solution Insertion Sort
## 166-014 Merge Sort and O(n log n)
## 167-015 Exercise Merge Sort
File attached
## 168-016 Solution Merge Sort
## 169-017 Stable VS Unstable Algorithms
File attached
## 170-018 Quick Sort
## 171-019 Optional Exercise Quick Sort
File attached
## 172-020 Which Sort Is Best
## 173-021 Resources Heap Sort
File attached
## 174-022 Radix Sort + Counting Sort
## 175-023 Resources Radix Sort + Counting Sort
File attached
## 176-024 Exercise Sorting Interview
## 177-025 Solution Sorting Interview
## 178-026 Sorting In Your Language
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
