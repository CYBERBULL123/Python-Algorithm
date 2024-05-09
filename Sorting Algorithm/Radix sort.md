### Radix Sort #️⃣

**Definition**: Radix sort is a non-comparative sorting algorithm that sorts integers by grouping digits that have the same value and sorting them based on their position. It processes the digits of the elements from the least significant digit (rightmost) to the most significant digit (leftmost). Radix sort can be performed using either the LSD (Least Significant Digit) or MSD (Most Significant Digit) variant. It's efficient for sorting integers with fixed-length representations. 🔢

**Neat and Best Code (LSD Radix Sort)**:
```python
def counting_sort(arr, exp):
    n = len(arr)
    output = [0] * n
    counts = [0] * 10

    for i in range(n):
        index = arr[i] // exp
        counts[index % 10] += 1

    for i in range(1, 10):
        counts[i] += counts[i - 1]

    i = n - 1
    while i >= 0:
        index = arr[i] // exp
        output[counts[index % 10] - 1] = arr[i]
        counts[index % 10] -= 1
        i -= 1

    for i in range(n):
        arr[i] = output[i]

def radix_sort(arr):
    max_val = max(arr)
    exp = 1
    while max_val // exp > 0:
        counting_sort(arr, exp)
        exp *= 10

# Example Usage:
arr = [170, 45, 75, 90, 802, 24, 2, 66]
radix_sort(arr)
print("Sorted array is:", arr)
```

**Input**: An unsorted array `arr` of non-negative integers.

**Output**: The same array `arr` sorted in ascending order.

**Implementation**:
1. Define a counting sort function to sort the input array based on a specific digit position (exp).
2. Iterate through each digit position (from the least significant digit to the most significant digit) and apply counting sort.
3. Repeat step 2 until all digits have been processed.

**Logic**: Radix sort sorts integers by processing digits from the least significant digit (rightmost) to the most significant digit (leftmost), using a stable sorting algorithm (e.g., counting sort) to sort each digit position.

**Example**: 
- **Input**: [170, 45, 75, 90, 802, 24, 2, 66]
- **Output**: [2, 24, 45, 66, 75, 90, 170, 802]

**Use Case**: Radix sort is efficient for sorting integers with fixed-length representations or for sorting integers with a limited range of values. It's commonly used in applications where integer sorting is required, such as string sorting, integer sorting, and more.
