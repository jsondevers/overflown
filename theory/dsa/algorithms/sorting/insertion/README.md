# Insertion Sort

## Table of Contents
- [Insertion Sort](#insertion-sort)
  - [Table of Contents](#table-of-contents)
  - [Problem Name](#problem-name)
  - [Procedure](#procedure)
  - [Analysis](#analysis)
    - [Resources](#resources)

## Problem Name

Sorting a list/array in ascending order using insertion sort. Insertion sort is the simplest sorting algorithm with the simplest implementation.

## Procedure

1. An array or list of sortable items is provided as an argument.
2. The variable `n` gets assigned the length of the array.
3. For loop running for `n - 1` iterations, starting at index `1`.
4. While loop inside for loop starting at current `i` and compares each element to its left, `j`.
5. The while loop keeps moving the current element to the left as long as it is less than the element on the left.
6. When the element is in its correct position in the sorted portion of the array the while loop terminates.
7. The for loop keeps iterating through the array until it is sorted.

```
InsertionSort(array)
    for i = 1 to n - 1
        current = array[i]
        j = i - 1
        while j >= 0 and array[j] > current
            array[j + 1] = array[j]
            j = j - 1
        end while
        array[j + 1] = current
    end for
end function
```

## Analysis

- Time Complexity: O(N^2)
- Auxiliary Space: O(1)

### Resources

[Wikipedia - Insertion Sort](https://en.wikipedia.org/wiki/Insertion_sort)
