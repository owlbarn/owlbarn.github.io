---
layout: post
title:  "Quicksort"
date:   2023-11-20 20:46:37 +0200
categories: algorithm
---

# Introduction

Quicksort was developed by British computer scientist Tony Hoare in 1959. It is one of the most widely used sorting algorithms and is commonly used in computer science and engineering applications.  
   
Quicksort is particularly useful when sorting large datasets because it has an average time complexity of O(n log n), which is faster than many other sorting algorithms. It is also an in-place sorting algorithm, meaning that it does not require any additional memory beyond the input array.  
   
Quicksort is used in a variety of applications, including sorting large databases, sorting elements in computer graphics and image processing, and in network routing algorithms. It is also used in many programming languages as a built-in sorting function, such as Python's `sorted()` function and C++'s `std::sort()` function.

# Implementation
   
```  
let rec quicksort = function  
  | [] -> []  
  | pivot::tail ->  
    let lesser, greater = List.partition (fun x -> x < pivot) tail in  
    quicksort lesser @ [pivot] @ quicksort greater  
```  
   
This implementation uses a functional programming style and takes advantage of pattern matching to handle the two cases of the input list: the empty list, which is already sorted, and a non-empty list, which is partitioned into two sub-lists based on a pivot element (in this case, the first element of the list).  
   
The `List.partition` function is used to split the tail of the input list into two sub-lists: `lesser`, which contains all elements that are strictly less than the pivot, and `greater`, which contains all elements that are greater than or equal to the pivot. The `@` operator is used to concatenate the sorted `lesser` sub-list, the pivot element, and the sorted `greater` sub-list into a single sorted list.  
   
Here's an example usage of the `quicksort` function:  
   
```  
let unsorted = [5; 1; 3; 9; 2]  
let sorted = quicksort unsorted  
```  
   
After running this code, the `sorted` variable should contain the list `[1; 2; 3; 5; 9]`, which is the sorted version of the `unsorted` list.