# Merge Sort

## Table of Contents
- [Merge Sort](#merge-sort)
  - [Table of Contents](#table-of-contents)
  - [Problem Name](#problem-name)
  - [Procedure](#procedure)
  - [Analysis](#analysis)
    - [Resources](#resources)

## Problem Name

Sorting a list/array in ascending order using merge sort. Merge sort works by dividing an array into sub-arrays, sorting those sub-arrays and putting them back together.

## Procedure

1. Check if the array has one element or is empty. If so, return the array as it is already sorted.
2. Calculate the midpoint of the array.
3. Recursively call Merge Sort on the left half of the array, from the start to the midpoint.
4. Recursively call Merge Sort on the right half of the array, from the midpoint to the end.
5. Merge the sorted left and right halves by comparing elements and placing them in the correct order.
6. Initialize an empty array to hold the merged result and set two index pointers, one for each half.
7. While both index pointers are within their halves compare the elements at the current index positions of the left and right halves, then append the smaller element to the merged result array and increment the index pointer.
8. If there are remaining elements in either the left or right half, append them to the merged result array.
9. Return the merged and sorted array.

```
MergeSort(arr):
    if n <= 1:
        return arr
    end if
    
    middle = length of arr / 2
    left = MergeSort(arr[0:middle])
    right = MergeSort(arr[mid:end])
    
    return Merge(left, right)
end function

Merge(left, right):
    result = empty array
    leftIndex = 0
    rightIndex = 0
    
    while leftIndex < length of left and rightIndex < length of right:
        if left[leftIndex] <= right[rightIndex]:
            append left[leftIndex] to result
            leftIndex = leftIndex + 1
        else:
            append right[rightIndex] to result
            rightIndex = rightIndex + 1
        end while
    
    append remaining elements in left starting from leftIndex to result
    append remaining elements in right starting from rightIndex to result
    
    return result
end function
```

## Analysis

- Time Complexity: O(N log(N))
- Auxiliary Space: O(N)

### Resources

- [Wikipedia - Merge Sort](https://en.wikipedia.org/wiki/Merge_sort)
