---
layout: post
title:  "Quicksort"
date:   2023-11-20 20:46:37 +0200
categories: algorithm
---

## Introduction

Quicksort was developed by British computer scientist Tony Hoare in 1959. It is one of the most widely used sorting algorithms and is commonly used in computer science and engineering applications.  

Quicksort is particularly useful when sorting large datasets because it has an average time complexity of O(n log n), which is faster than many other sorting algorithms. It is also an in-place sorting algorithm, meaning that it does not require any additional memory beyond the input array.  

Quicksort is used in a variety of applications, including sorting large databases, sorting elements in computer graphics and image processing, and in network routing algorithms. It is also used in many programming languages as a built-in sorting function, such as Python's `sorted()` function and C++'s `std::sort()` function.

## Implementation
   
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

## Step-by-step Explanation

Here's a step-by-step explanation of how the quicksort algorithm works:  
   
1. Choose a pivot element from the list. This can be any element, but a common choice is the first or last element in the list.  
   
2. Partition the list into two sub-lists, with one sub-list containing elements less than the pivot and the other sub-list containing elements greater than or equal to the pivot. This can be done by iterating through the list and swapping elements as necessary to ensure that all elements less than the pivot are on one side of the pivot and all elements greater than or equal to the pivot are on the other side.  
   
3. Recursively apply steps 1 and 2 to the sub-lists until the entire list is sorted. This can be done by calling the quicksort function on each sub-list.  
   
Here's an example of how this algorithm would sort the list `[5; 1; 3; 9; 2]`:  
   
1. Choose the first element, `5`, as the pivot.  
   
2. Partition the list into two sub-lists: `[1; 3; 2]` and `[9]`. All elements less than `5` are on the left and all elements greater than or equal to `5` are on the right.  
   
3. Recursively apply steps 1 and 2 to each sub-list. For the left sub-list, choose `1` as the pivot and partition it into `[ ]`, `[1]`, and `[3; 2]`. For the right sub-list, it is already sorted.  
   
4. Recursively apply steps 1 and 2 to the sub-lists `[1]` and `[3; 2]`. Both sub-lists are already sorted, so no further partitioning is necessary.  
   
5. Concatenate the sorted sub-lists in the order `[1]`, `[2; 3]`, `[5]`, and `[9]` to obtain the sorted list `[1; 2; 3; 5; 9]`.  

This example shows how the quicksort algorithm works by recursively dividing the input list into smaller sub-lists, sorting them, and then combining them to obtain the final sorted list.

## Complexity

The time complexity of quicksort is O(n log n) on average, where n is the number of elements in the input list.   
  
The average case occurs when the pivot element is chosen randomly and is close to the median value of the list. In this case, the list is divided roughly in half with each partition, and the algorithm will make log n recursive calls to sort the entire list. The partitioning step takes linear time, so the total time complexity is O(n log n).  
   
However, in the worst case, quicksort can have a time complexity of O(n^2) if the pivot element is consistently chosen poorly. For example, if the pivot is always chosen as the smallest or largest element in the list, then each partition will only remove one element from the list, and the algorithm will make n recursive calls to sort the entire list. This worst-case scenario is rare in practice, but it can occur in certain edge cases.  
   
In terms of space complexity, quicksort is an in-place sorting algorithm, meaning that it does not require any additional memory beyond the input list. However, the recursive nature of the algorithm means that it has a space complexity of O(log n) due to the call stack used for the recursive calls.  
   
Overall, quicksort is a highly efficient sorting algorithm with a time complexity of O(n log n) on average, making it a popular choice for sorting large datasets.