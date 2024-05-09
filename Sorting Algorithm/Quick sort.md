### Quick Sort ⚡

**Definition**: Quick sort is a divide-and-conquer algorithm that works by selecting a "pivot" element from the array and partitioning the other elements into two sub-arrays according to whether they are less than or greater than the pivot. It then recursively sorts the sub-arrays. It's a highly efficient sorting algorithm with an average time complexity of O(n log n). 🚀

**Neat and Best Code**:
```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)

# Example Usage:
arr = [64, 34, 25, 12, 22, 11, 90]
sorted_arr = quick_sort(arr)
print("Sorted array is:", sorted_arr)
```

**Input**: An unsorted array `arr` of elements.

**Output**: A new array containing the same elements as `arr`, but sorted in ascending order.

**Implementation**:
1. Choose a pivot element from the array.
2. Partition the array into two sub-arrays: one containing elements less than the pivot and one containing elements greater than the pivot.
3. Recursively apply quick sort to the sub-arrays.
4. Concatenate the sorted sub-arrays and the pivot element to form the final sorted array.

**Logic**: Quick sort works by selecting a pivot element, partitioning the array around the pivot, and recursively applying the same process to the sub-arrays.

**Example**: 
- **Input**: [64, 34, 25, 12, 22, 11, 90]
- **Output**: [11, 12, 22, 25, 34, 64, 90]

**Use Case**: Quick sort is highly efficient and widely used in practice for sorting large datasets. It has an average time complexity of O(n log n) and a worst-case time complexity of O(n^2), but its worst-case behavior is rare in Practices 
