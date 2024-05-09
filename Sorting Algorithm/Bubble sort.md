### Bubble Sort 🫧

**Definition**: Bubble sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted. 🛁

**Neat and Best Code**:
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n-1):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]

# Example Usage:
arr = [64, 34, 25, 12, 22, 11, 90]
bubble_sort(arr)
print("Sorted array is:", arr)
```

**Input**: An unsorted array `arr` of elements.

**Output**: The same array `arr` sorted in ascending order.

**Implementation**:
1. Start with the first element and compare it with the next element.
2. If the current element is greater than the next element, swap them.
3. Repeat this process for each pair of adjacent elements until the entire array is sorted.

**Logic**: Bubble sort works by repeatedly stepping through the list, comparing each pair of adjacent items and swapping them if they are in the wrong order.

**Example**: 
- **Input**: [64, 34, 25, 12, 22, 11, 90]
- **Output**: [11, 12, 22, 25, 34, 64, 90]

**Use Case**: Bubble sort is suitable for small data sets or nearly sorted arrays. However, it's not efficient for large datasets due to its quadratic time complexity.

Feel free to ask about anything else or any other algorithm!
