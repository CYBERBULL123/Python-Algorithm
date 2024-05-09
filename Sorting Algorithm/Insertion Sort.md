### Insertion Sort 📜

**Definition**: Insertion sort is a simple sorting algorithm that builds the final sorted list one item at a time. It iterates over the input list and at each iteration, it removes one element from the input data, finds the location it belongs to in the sorted list, and inserts it there. The process is repeated until the entire list is sorted. 📝

**Neat and Best Code**:
```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key

# Example Usage:
arr = [64, 34, 25, 12, 22, 11, 90]
insertion_sort(arr)
print("Sorted array is:", arr)
```

**Input**: An unsorted array `arr` of elements.

**Output**: The same array `arr` sorted in ascending order.

**Implementation**:
1. Start with the second element (index 1) and consider it as the key.
2. Compare the key with the elements to its left in the sorted sublist.
3. Move elements greater than the key one position to the right.
4. Insert the key into its correct position in the sorted sublist.
5. Repeat steps 1-4 until the entire list is sorted.

**Logic**: Insertion sort works by iteratively selecting an element from the unsorted part of the list and inserting it into its correct position in the sorted part of the list.

**Example**: 
- **Input**: [64, 34, 25, 12, 22, 11, 90]
- **Output**: [11, 12, 22, 25, 34, 64, 90]

**Use Case**: Insertion sort is efficient for small data sets or when the input list is almost sorted. It's also useful when the input list is being built one element at a time. However, it's not efficient for large datasets due to its quadratic time complexity.
