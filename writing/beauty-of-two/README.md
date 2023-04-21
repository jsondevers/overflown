# Beauty of Two

## By Jason Devers

The structure of this writing will be written as a proof for my claim for why the number $2$ is the most beautiful number, but this is not a formal proof. I am simply writing this in a proof like structure as a way to ironically prove my claim.

This was *not* any assignment for any class, I just wanted to write this.

$Corollary:$ I've worn the number $2$ as my jersey positive integer for Lacrosse since I was freshman in high school.

$Proof:$  [My Hudl Account from HS](https://www.hudl.com/profile/8521344/Jason-Devers) $\square$

$Lemma$ $0$: 2 is the best

$Proof:$ "First is the worst, second is the best"

$Lemma$ $1$: The number $2$ is the only even prime positive integer.

$Proof:$ Suppose by way of contradiction that there exists an even prime positive integer $p$ other than $2$. Then $p$ is an even positive integer, and $p > 2$. Since $p$ is prime, it cannot be divisible by any positive integer other than 1 and $p$. But $p$ is even, so $p$ is divisible by $2$. This is a contradiction, so there is no even prime positive integer other than $2$. $\square$

$Lemma$ $2$: The number $2$ is what allows us to define the concept of parity.

$Proof:$ Consider the definition of oddness: a positive integer, $x$ is odd if $\exists$ a positive integer, $k$, such that $x = 2k + 1$. Similarly, consider the definition of evenness: a positive integer, $k$ is even if $\exists$ a positive integer, $k$, such that $x = 2k$. This definition of oddness and evenness is only possible because of the existence of the positive integer $2$. $\square$

$Corollary:$ Binary is what allows us to communicate with computers.

$Proof:$ Digital systems use binary to communicate with the system. Programming languages and software in our computers break down to a set of instructions in assembly that can be broken down into binary which is what the computer understands. Thus, all programming is an abstraction from binary. $\square$

$Corollary:$ The powers of $2$ are so heavily used because of their representation in binary.

$2^0 = 1$, $2^1=2$, $2^2=4$, $2^3=8$, , $2^4=16$, $2^5=32$, , $2^6=64$, $2^7=128$, $2^8=256$, $2^9=512$, $2^{10}=1024$, $2^{11}=2048$, $2^{12}=4096$, ..., $\displaystyle \prod_{i = 0} ^{n}2$  

$Proof:$ The powers of $2$ are used in many different ways in computing. For example, the size of a data type in a programming language is often a power of $2$. The size of a data type is the positive integer of bits that are used to represent that data type. For example, the size of an integer in C is $4$ bytes, or $32$ bits. Powers of two make it easier to design and implement digital systems because their binary representations are simple and regular. Similarly, memory addresses and buffer sizes are often chosen to be powers of two to make them easier to work with. $\square$

$Lemma$ $3$: The number $2$ is the only non-zero positive integer that satisfies the following: $2^2 \equiv  2 \cdot 2 \equiv 2 + 2 $.

$Proof:$ Proven by a direct proof. To start, let us break down $2^2$, and write this as $a^a$, we know that this is the same as $a \cdot a$ and if we look at the next term, $2 \cdot 2$, we can see that this is the same as $a \cdot a$. Now, let us look at the last term, $2 + 2$, we can see that this is the same as $a + a$ which was the same as $a \cdot a$. Now, we can see that $2^2 \equiv 2 \cdot 2 \equiv 2 + 2$. $\square$

A *stronger* $Proof$ of $Lemma$ $3$: Imagine $\exists$ a number $x$ such that: $x^x = (x)(x)$

If $x$ is positive then we could take the logarithms of either side and see:

- $log(x^x) = log((x)(x))$
- $x log(x) = log(x) + log(x)$
- $x log(x) - 2log(x) = 0$
- $(x-2)log(x) = 0$

Thus, we proceed by cases:

- Case 1: $x-2=0 \Rightarrow x=2$, ($x$ minus two is zero, so $x$ is two)
- Case 2: $log(x) = 0 \Rightarrow x=1$, ($x$ is one)

That all follows as *necessarily true* just from the assumption that $x$ meets the condition and is positive: If those facts are true then $x$ MUST be either $1$ or $2$.

If $x$ were zero then we'd have to assign a precise value to $0^0$ which is undefined.

Suppose by contradiction that x was negative. From our original equation, we could write $x^x = (x)(x)$ then if $x$ was negative then we could write this as $(-x)(-x)$ which is the same as $x = -x$. This implies that $x = 0$ which contradicts our assumption that $x$ is negative. Thus, $x$ cannot be negative.

Now consider the equation $(x)(x) = x + x$. We can rewrite this as:

$(x)(x) - x -x = 0$
$(x-2)x=0$

From this equation, we see that either $x-2 = 0$ or $x = 0$. However, we have already shown that $x$ cannot be $0$. Therefore, $x-2 = 0$, which implies $x = 2$.

In conclusion, the only possible value of $x$ that satisfies both equations is $x = 2$.

$Lemma$ $4$: The number $2$ provides the foundation of answering questions.

$Proof:$ Something can either be either true or false (1 or 0). We can see this in the form of truth tables and various other applications. It's fundamental in answering dynamic programming problems, for example, starting from the end of the optimal solution and asking if this element is included in the optimal solution, yes or no? Or even in Shakespeare, "To be or, or not to be". There are two options and somehow many problems can be reduced into a yes or no question. $\square$

$Theorem:$ The positive integer $2$ is the most beautiful positive integer.

$Proof:$

### TODO

- [ ] Add symmetry
- [ ] Add pairs
