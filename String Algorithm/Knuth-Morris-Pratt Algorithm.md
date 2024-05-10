## Knuth-Morris-Pratt Algorithm

The Knuth-Morris-Pratt (KMP) algorithm is a string searching algorithm that efficiently finds occurrences of a pattern within a longer text. It works by precomputing a partial match table (also known as the failure function or longest prefix-suffix array) based on the pattern, which allows it to avoid unnecessary backtracking during the search process.

Here's how the Knuth-Morris-Pratt algorithm works:

1. **Preprocessing (Building the Partial Match Table)**:
   - Given a pattern \( P \), construct a partial match table \( F \) of length \( m \), where \( m \) is the length of the pattern.
   - Initialize \( F[0] = 0 \) and \( F[1] = 0 \).
   - Iterate through the pattern from left to right, updating the values of \( F[i] \) based on the previous values and the current character of the pattern.
   - \( F[i] \) represents the length of the longest proper prefix of the substring \( P[0:i] \) that is also a suffix of \( P[0:i] \).

2. **Searching (Using the Partial Match Table)**:
   - Given a text \( T \) of length \( n \) and a pattern \( P \) of length \( m \), iterate through the text from left to right.
   - Maintain two pointers: \( i \) for the text and \( j \) for the pattern.
   - Compare the characters of the text and the pattern at positions \( i \) and \( j \):
     - If they match (\( T[i] == P[j] \)), increment both \( i \) and \( j \).
     - If they don't match and \( j > 0 \), update \( j \) using the partial match table (\( j = F[j] \)).
     - If they don't match and \( j = 0 \), increment only \( i \).
   - Repeat this process until the end of the text or until a match is found.

3. **Output**:
   - If a match is found, the index \( i - m \) in the text indicates the starting position of the match.
   - Repeat the search process to find all occurrences of the pattern in the text.

The time complexity of the Knuth-Morris-Pratt algorithm is \( O(n + m) \), where \( n \) is the length of the text and \( m \) is the length of the pattern. This makes it more efficient than naive string matching algorithms, especially for large texts and patterns.

Here's a Python implementation of the Knuth-Morris-Pratt algorithm:

```python
def compute_partial_match_table(pattern):
    m = len(pattern)
    F = [0] * m
    k = 0

    for i in range(1, m):
        while k > 0 and pattern[k] != pattern[i]:
            k = F[k - 1]
        if pattern[k] == pattern[i]:
            k += 1
        F[i] = k

    return F

def kmp_search(text, pattern):
    n, m = len(text), len(pattern)
    F = compute_partial_match_table(pattern)
    j = 0

    for i in range(n):
        while j > 0 and pattern[j] != text[i]:
            j = F[j - 1]
        if pattern[j] == text[i]:
            j += 1
        if j == m:
            print("Found pattern at index:", i - m + 1)
            j = F[j - 1]

# Example usage:
text = "ABABABCABAABABABABABAB"
pattern = "ABABAB"
kmp_search(text, pattern)
```

This code demonstrates how to use the Knuth-Morris-Pratt algorithm to search for occurrences of a pattern within a text.
