## Dynamic Programming

**Definition**: Dynamic Programming (DP) is a powerful optimization technique used to solve problems by breaking them down into smaller subproblems and solving each subproblem only once, storing the results in a table (usually an array or a matrix) to avoid redundant computations. DP is applicable to problems with overlapping subproblems and optimal substructure, where the solution to a problem can be constructed from solutions to its subproblems. It can be implemented using either a top-down approach (memoization) or a bottom-up approach (tabulation). 🔄

**Neat and Best Explanation**:
Dynamic programming can be divided into two main approaches:

1. **Memoization (Top-down)**:
   - In memoization, also known as top-down DP, solutions to subproblems are computed recursively and stored in a memoization table (usually a dictionary or an array) to avoid redundant computations.
   - The recursive function checks if the solution to the subproblem is already stored in the memoization table. If yes, it returns the stored result; otherwise, it computes the result recursively and stores it in the memoization table for future use.
   - Memoization is suitable for problems with a recursive structure and overlapping subproblems.

2. **Tabulation (Bottom-up)**:
   - In tabulation, also known as bottom-up DP, solutions to subproblems are computed iteratively, starting from the smallest subproblems and building up to larger subproblems.
   - Tabulation involves creating a table (usually a 1D or 2D array) to store the solutions to subproblems. Each cell in the table represents the solution to a subproblem.
   - The table is filled iteratively, typically using nested loops, where each cell's value is computed based on previously computed values.
   - Tabulation is suitable for problems with optimal substructure, where the solution to a problem can be constructed from solutions to its subproblems, and it avoids the overhead of function calls and recursion.

**Example**:
Consider the problem of computing the Fibonacci sequence:

1. **Memoization**:
   - We can use memoization to store the results of previously computed Fibonacci numbers and avoid redundant computations.
   - For example, when computing `fibonacci(5)`, instead of recomputing `fibonacci(3)` and `fibonacci(4)` separately, we can use the stored results from the memoization table.
   
2. **Tabulation**:
   - In tabulation, we start with the base cases (`fibonacci(0)` and `fibonacci(1)`) and iteratively compute larger Fibonacci numbers.
   - We fill up a table (array) with the Fibonacci numbers, using the previously computed values to compute the next Fibonacci number.

**Use Case**:
Dynamic programming is widely used in various domains, including computer science, mathematics, optimization, and artificial intelligence, to efficiently solve problems with overlapping subproblems and optimal substructure. It is commonly used in problems such as shortest paths, knapsack problems, matrix chain multiplication, and many others.
