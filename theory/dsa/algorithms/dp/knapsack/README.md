# Knapsack

## Problem

Given a set of items, each with a weight and a value, determine the number of each item to include in a collection so that the total weight is less than or equal to a given limit and the total value is as large as possible. The problem is also known as the 0-1 knapsack problem. The problem is NP-hard.

## Algorithm

```java
knapsack(v[1..n], w[1..n], W){
    allocate V[0..n][0..W]
    for (j = 0 to W){
        V[0][j] = 0; // initialize
    }
    for (i = 1 to n){
        for (j = 0 to W){
            leave_val = V[i - 1, j] // value if we leave i
            if (j >= w[i]){ // enough capacity to take i
                take_val = v[i] + V[i - 1, j - w[i]] // value if we take i
            } else {
                take_val = -INF // can't take i
            }
            V[i, j] = max(leave_val, take_val) // take the best
        }
    }
    return V[n, W]
}
```
