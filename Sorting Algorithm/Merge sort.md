### Merge Sort 🔀

**Definition**: Merge sort is a divide-and-conquer algorithm that divides the input list into two halves, recursively sorts each half, and then merges the sorted halves to produce a single sorted list. It's a stable, efficient, and comparison-based sorting algorithm with a time complexity of O(n log n). 🔄

**Neat and Best Code**:
```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        left_half = arr[:mid]
        right_half = arr[mid:]

        merge_sort(left_half)
        merge_sort(right_half)

        i = j = k = 0

        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1

        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1

        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1

# Example Usage:
arr = [64, 34, 25, 12, 22, 11, 90]
merge_sort(arr)
print("Sorted array is:", arr)
```

**Input**: An unsorted array `arr` of elements.

**Output**: The same array `arr` sorted in ascending order.

**Implementation**:
1. Divide the input list into two halves.
2. Recursively apply merge sort to each half.
3. Merge the sorted halves into a single sorted list.

**Logic**: Merge sort divides the input list into smaller sublists until each sublist contains only one element, which is inherently sorted. Then, it merges the sorted sublists back together to produce a single sorted list.

**Example**: 
- **Input**: [64, 34, 25, 12, 22, 11, 90]
- **Output**: [11, 12, 22, 25, 34, 64, 90]

**Use Case**: Merge sort is efficient for sorting large datasets due to its consistent O(n log n) time complexity. It's also a stable sorting algorithm, meaning it preserves the relative order of equal elements.
