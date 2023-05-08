# Weighted Interval Scheduling

## Problem

Given a set of intervals, find the maximum number of non-overlapping intervals that can be scheduled. Each interval has a weight associated with it. The weight of an interval is the sum of weights of all intervals that overlap with it. The goal is to find a set of non-overlapping intervals with maximum total weight. The problem is also known as weighted job scheduling. The problem is similar to interval scheduling, but the difference is that the weight of an interval is not 1, but can be any positive integer. The problem is NP-hard.

## Solution

The solution is based on dynamic programming. The recurrence is as follows:

`1. recursive`

Time complexity: $O(2^n)$

Space complexity: $O(2^n)$

```java
int recursiveWIS(int j){
    if (j == 0) return 0;
    else return max(recursiveWIS(j - 1), v[j] + recursiveWIS(p(j)));
}
```

`2. memoization`

Time complexity: $O(n)$

Space complexity: $O(n)$

```java
int memoized(int j){
    if (j == 0) return 0;
    else if (M[j] has been computed) return M[j];
    else {
        int leaveWeight = memoized(j - 1);
        int takeWeight = v[j] + memoized(p(j));
        if (leaveWeight > takeWeight){
            M[j] = leaveWeight;
            pred[j] = j - 1;
        } else {
            M[j] = takeWeight;
            pred[j] = p(j);
        }
        return M[j];
    }
}
```

`3. bottom-up`

Time complexity: $O(n)$

Space complexity: $O(n)$

```java
int bottomUp(){
    M[0] = 0;
    for (j = 1 to n){
        int leaveWeight = M[j - 1];
        int takeWeight = v[j] + M[p(j)];
        if (leaveWeight > takeWeight){
            M[j] = leaveWeight;
            pred[j] = j - 1;
        } else {
            M[j] = takeWeight;
            pred[j] = p(j);
        }
    }
}
```

Now we put this back into the actual schedule problem:

```java
getSchedule(){
    j = n;
    schedule = empty;
    while (j > 0){
        if (pred[j] == p(j)){
            prepend j to the front of schedule;
        }
        j = pred[j];
    }
    return schedule;
}
```
