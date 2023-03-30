# Java

## Table of Contents

- [Generics][#Generics]

## Generics

Consider the following code:

```java
public class Tree<V extends Serializable & Comparable<V>>
```

- "The bound shown here requires that the value type V is comparable to itself, in other words, that it implements the Comparable interface directly. This rules out the use of types that inherit the Comparable interface from a superclass."

Perhaps that last phrase explains why the use of "extends" rather than "implements",

- source: [Reilly Book](https://www.oreilly.com/library/view/java-in-a/0596007736/ch04s01.html#ftn.javanut5-CHP-4-FNOTE-4)
