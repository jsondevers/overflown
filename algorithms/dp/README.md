# Dynamic Programming


## Introduction

Dynamic programming is a method for solving a complex problem by breaking it down into a collection of simpler subproblems, solving each of those subproblems just once, and storing their solutions using a memory-based data structure (array, map,etc). Each of the subproblem solutions are indexed in some way, typically based on the values of their input parameters, so as to facilitate looking them up.

Dynamic programming differs from divide-and-conquer in that we typically solve the subproblems in a specific order, and we solve each subproblem only once. This is in contrast to divide-and-conquer, where we typically solve the subproblems in a recursive manner, and we solve each subproblem multiple times.

## Solving Dynamic Programming Problems

Dynamic programming is a method for solving a complex problem by breaking it down into a collection of simpler subproblems, solving each of those subproblems just once, and storing their solutions using a memory-based data structure (array, map,etc).

## Table of Contents

- [Weighted Interval Scheduling](wis/README.md)
- [Knapsack](knapsack/README.md)

### Steps to Solve a DP Problem


1. Visualize Examples
2. Find appropriate sub-problem
3. Finding relationships among sub-problems
4. Generalize the relationship
5. Implement by solving sub-problems in order


## Solving SRTBOT recursively (Taken from MIT 6.006, Erik Demaine) I owe a lot of my ability to solve DP problems Professor Demaine and MIT OpenCourseWare

1. `S`ub problem definition
    - Describe the meaning of the subproblem in words
    - Often subsets of input: prefixes, suffixes, substrings, etc
    - Often record partial state: add sub problems by incrementing some auxiliary variable(s)
2. `R`elate subproblem solutions recursively $x(i) = f(x(j), ...)$ for one or more $j < i$
3. `T`opological order on subproblems to guarantee a cyclic (subproblems $\implies$ call DAG), i.e to argue relation is acyclic and subproblems form a DAG
4. `B`ase cases of relation. State solutions for all (reachable) independent subproblems where relation breaks down
5. `O`riginal problem solve via sub problems
    - Show how to compute solution to original problem from solutions to subproblem(s)
    - Possibly use parent pointers to recover actual solution, not just objective function
6. `T`ime analysis
    - $\displaystyle \sum_{x \in X}work(x)$ or if $work(x) = O(W)$ for all $x \in X$, then $|X| \cdot O(W)$
    - $work(x)$ measures *nonrecursive* work in relation; treat recursions as taking $O(1)$ time

## How to relate subproblems to solutions

- The general approach we’re following to define a relation on subproblem solutions:
  - Identify a question about a subproblem solution that, if you knew the answer to, would reduce to “smaller” subproblem(s)
    *In case of bowling, the question is “how do we bowl the first couple of pins?”*
  - Then locally brute-force the question by trying all possible answers, and taking the best
    *In case of bowling, we take the max because the problem asks to maximize*
  - Alternatively, we can think of correctly guessing the answer to the question, and directly recursing; but then we actually check all possible guesses, and return the “best”
- The key for efficiency is for the question to have a small (polynomial) number of possible
answers, so brute forcing is not too expensive
- Often (but not always) the nonrecursive work to compute the relation is equal to the number
of answers we’re trying

## Merge sort using SRTBOT Framework

- Sub problem: $S(i,j)=$ sorted array on elements $A[i:j]$ for $0 \leq i \leq j \leq n$
- Relation: $S(i,j)=merge(S(i,m), S(m,j))$ where $m=\lfloor \frac{i+j}{2} \rfloor$
- Topological order: Increasing $j-i$
- Base cases: $S(i,i+1) = [A[i]]$
- Original problem: $S(0,n)$
- Time analysis: $T(n)=2T(\frac{n}{2})+O(n) = O(n \log n)$


