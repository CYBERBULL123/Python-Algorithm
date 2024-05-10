## Longest Common Subsequence

The Longest Common Subsequence (LCS) problem is a classic problem in dynamic programming that seeks to find the longest subsequence that is common to two sequences (strings). Unlike substrings, subsequences are not required to occupy consecutive positions within the original sequences.

Here's how the Longest Common Subsequence problem can be solved using dynamic programming:

1. **Initialization**:
   - Create a 2D table (matrix) with dimensions \( (m+1) \times (n+1) \), where \( m \) and \( n \) are the lengths of the two input sequences.
   - Initialize the first row and the first column of the table to zeros.

2. **Dynamic Programming**:
   - Iterate over the characters of the two input sequences.
   - At each iteration, compare the characters at the current positions.
   - If the characters are equal, increment the value in the table at the corresponding position by 1 plus the value in the table at the previous diagonal position.
   - If the characters are not equal, take the maximum of the values in the table at the previous row and the previous column.
   - Continue this process until all positions in the table are filled.

3. **Backtracking (Optional)**:
   - Once the table is filled, perform backtracking to reconstruct the longest common subsequence.
   - Start from the bottom-right corner of the table and backtrack based on the values in the table.
   - Follow the direction of the maximum value until reaching the top-left corner of the table, recording the characters encountered along the way.

4. **Output**:
   - The value in the bottom-right corner of the table represents the length of the longest common subsequence.
   - If backtracking is performed, the reconstructed subsequence can also be obtained.

The time complexity of the dynamic programming approach for the Longest Common Subsequence problem is \( O(m \times n) \), where \( m \) and \( n \) are the lengths of the input sequences.

Here's a Python implementation of the Longest Common Subsequence problem:

```python
def longest_common_subsequence(X, Y):
    m, n = len(X), len(Y)
    # Initialize the LCS table
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    
    # Fill the table using dynamic programming
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if X[i - 1] == Y[j - 1]:
                dp[i][j] = dp[i - 1][j - 1] + 1
            else:
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
    
    # Perform backtracking to reconstruct the LCS
    lcs = []
    i, j = m, n
    while i > 0 and j > 0:
        if X[i - 1] == Y[j - 1]:
            lcs.append(X[i - 1])
            i -= 1
            j -= 1
        elif dp[i - 1][j] > dp[i][j - 1]:
            i -= 1
        else:
            j -= 1
    
    # Reverse the LCS to get the correct order
    lcs.reverse()
    return lcs, dp[m][n]

# Example usage:
X = "ABCBDAB"
Y = "BDCAB"
lcs, length = longest_common_subsequence(X, Y)
print("Longest Common Subsequence:", "".join(lcs))
print("Length of LCS:", length)
```

This code demonstrates how to find the longest common subsequence between two sequences (strings) using dynamic programming and optionally reconstructs the subsequence.
