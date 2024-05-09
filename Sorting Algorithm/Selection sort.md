### Selection Sort ✔

**Definition**: Selection sort is a simple sorting algorithm that divides the input list into two parts: the sublist of items already sorted and the sublist of items remaining to be sorted. It repeatedly selects the smallest (or largest) element from the unsorted sublist and swaps it with the leftmost unsorted element. The sorted sublist grows incrementally until the entire list is sorted. 🎯

**Neat and Best Code**:
```python
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_index = i
        for j in range(i+1, n):
            if arr[j] < arr[min_index]:
                min_index = j
        arr[i], arr[min_index] = arr[min_index], arr[i]

# Example Usage:
arr = [64, 34, 25, 12, 22, 11, 90]
selection_sort(arr)
print("Sorted array is:", arr)
```

**Input**: An unsorted array `arr` of elements.

**Output**: The same array `arr` sorted in ascending order.

**Implementation**:
1. Divide the input list into two parts: the sublist of items already sorted and the sublist of items remaining to be sorted.
2. Find the smallest element in the unsorted sublist.
3. Swap it with the leftmost unsorted element.
4. Expand the sorted sublist by moving the sublist boundary one element to the right.
5. Repeat steps 2-4 until the entire list is sorted.

**Logic**: Selection sort works by repeatedly selecting the smallest (or largest) element from the unsorted sublist and swapping it with the leftmost unsorted element.

**Example**: 
- **Input**: [64, 34, 25, 12, 22, 11, 90]
- **Output**: [11, 12, 22, 25, 34, 64, 90]

**Use Case**: Selection sort is suitable for small data sets or when memory space is limited, as it requires only a single additional memory space for the swap operation. However, it's not efficient for large datasets due to its quadratic time complexity.
