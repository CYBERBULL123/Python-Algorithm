## Rabin-Karp Algorithm

The Rabin-Karp algorithm is a string searching algorithm that efficiently finds occurrences of a pattern within a longer text. It works by using hashing to quickly compare substrings of the text with the pattern, thereby avoiding unnecessary character comparisons.

Here's how the Rabin-Karp algorithm works:

1. **Preprocessing (Hashing)**:
   - Given a pattern \( P \) of length \( m \) and a text \( T \) of length \( n \), compute the hash value of the pattern.
   - Compute the hash value of each \( m \)-length substring of the text starting from index \( 0 \) to \( n - m \).
   - Use a rolling hash function to efficiently compute the hash value of each substring based on the previous substring.

2. **Searching (Using Hashing)**:
   - Compare the hash value of the pattern with the hash value of each substring of the text.
   - If the hash values match, perform a character-by-character comparison to confirm the match.
   - If a match is found, record the starting index of the match in the text.

3. **Rolling Hash**:
   - To efficiently compute the hash value of each substring, update the hash value based on the previous hash value and the new character being added or removed.
   - Use a rolling hash function such as the polynomial rolling hash function to update the hash value in \( O(1) \) time.

4. **Collision Handling**:
   - Since hash values are computed modulo a large prime number to prevent overflow, collisions (two different substrings having the same hash value) may occur.
   - To handle collisions, perform a character-by-character comparison to confirm the match when hash values match.

The time complexity of the Rabin-Karp algorithm is \( O(n + m) \) on average, where \( n \) is the length of the text and \( m \) is the length of the pattern. In the worst case, the time complexity can be \( O(n \cdot m) \) if all substrings have the same hash value.

Here's a Python implementation of the Rabin-Karp algorithm:

```python
def rabin_karp_search(text, pattern):
    n, m = len(text), len(pattern)
    prime = 101  # A prime number for hashing
    pattern_hash = 0
    text_hash = 0
    prime_power = 1

    # Calculate the hash value of the pattern and the first m-length substring of the text
    for i in range(m):
        pattern_hash = (pattern_hash * prime + ord(pattern[i])) % prime
        text_hash = (text_hash * prime + ord(text[i])) % prime

    # Calculate the prime_power value (prime^(m-1))
    for i in range(m - 1):
        prime_power = (prime_power * prime) % prime

    # Iterate through each substring of length m in the text
    for i in range(n - m + 1):
        # Check if the hash values match
        if pattern_hash == text_hash:
            # Perform a character-by-character comparison to confirm the match
            if text[i:i + m] == pattern:
                print("Found pattern at index:", i)
        # Update the hash value of the next substring using rolling hash
        if i < n - m:
            text_hash = (prime * (text_hash - ord(text[i]) * prime_power) + ord(text[i + m])) % prime
            # Ensure the hash value is positive
            if text_hash < 0:
                text_hash += prime

# Example usage:
text = "ABABABCABAABABABABABAB"
pattern = "ABABAB"
rabin_karp_search(text, pattern)
```

This code demonstrates how to use the Rabin-Karp algorithm to search for occurrences of a pattern within a text.
