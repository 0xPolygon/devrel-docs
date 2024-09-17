# Polynomial time

As a high school refresher, in mathematics, a polynomial is an expression that
involves a sum of terms, where each term is a constant multiplied by a variable
raised to a non-negative integer power. For example:

- 3x^2 + 2x + 1 is a polynomial with three terms: 3x^2, 2x, and 1.
- x^3 + 4x^2 + x + 7 is another polynomial with four terms.

When we say a problem can be solved in polynomial time, we are talking about
how the time it takes to solve the problem depends on the size of the input.

- Input size: This is how big the problem is. For example, if you're sorting a
  list of numbers, the input size is the number of elements in the list.
- Polynomial time: This means that the amount of time a computer takes to solve
  the problem increases at a rate proportional to a polynomial function of the
  input size. In simpler terms, if the input size is n, then the time to solve
  the problem might grow like n^2, n^3, or even just n, but it doesn't grow too
  quickly.

For example:

- If a sorting algorithm runs in O(n^2) time, that means if you double the
  number of elements to be sorted, the time it takes to sort them might
  quadruple.
- If an algorithm runs in O(n) time, that means the time to solve the problem
  grows linearly with the input size (double the input, double the time).

## Non-polynomial time

In contrast, exponential time grows much faster. For example, 2^n grows much
more quickly than n^2 as n increases. For instance:

- For n = 10, n^2 = 100, while 2^n = 1024.
- For n = 20, n^2 = 400, but 2^n = 1,048,576.

In many computational problems (especially NP-complete problems), we suspect
they require exponential time to solve, which is why they become _intractable_
as the input size grows.

## Why is polynomial time important?

Problems that can be solved in polynomial time are considered “tractable” or
“efficient.” In practical terms, this means that for reasonable input sizes, a
computer can solve them in a realistic amount of time. Many problems in computer
science aim to find polynomial-time algorithms because exponential-time
algorithms would take too long as the input grows.

## Putting it simply

- Polynomial time: The time to solve a problem grows in a manageable way as the
  input gets bigger (like n^2 or n^3).
- Exponential time: The time grows way too fast (like 2^n or 3^n) as the input
  gets bigger.
  