### Counting Sort 🔢

**Definition**: Counting sort is an integer sorting algorithm that operates by counting the number of occurrences of each unique element in the input array and using arithmetic to determine the position of each element in the sorted output array. It's efficient for sorting integers when the range of input values is relatively small compared to the number of elements to be sorted. 📊

**Neat and Best Code**:
```python
def counting_sort(arr):
    max_val = max(arr)
    counts = [0] * (max_val + 1)
    sorted_arr = [0] * len(arr)

    for num in arr:
        counts[num] += 1

    for i in range(1, max_val + 1):
        counts[i] += counts[i - 1]

    for num in reversed(arr):
        sorted_arr[counts[num] - 1] = num
        counts[num] -= 1

    return sorted_arr

# Example Usage:
arr = [4, 2, 2, 8, 3, 3, 1]
sorted_arr = counting_sort(arr)
print("Sorted array is:", sorted_arr)
```

**Input**: An unsorted array `arr` of non-negative integers.

**Output**: A new array containing the same elements as `arr`, but sorted in ascending order.

**Implementation**:
1. Find the maximum value in the input array to determine the size of the counting array.
2. Count the occurrences of each element in the input array and store the counts in a counting array.
3. Modify the counting array to store the cumulative sum of counts.
4. Iterate through the input array in reverse order, placing each element in its correct position in the sorted output array using the counting array.

**Logic**: Counting sort works by counting the occurrences of each unique element in the input array and using arithmetic to determine the position of each element in the sorted output array.

**Example**: 
- **Input**: [4, 2, 2, 8, 3, 3, 1]
- **Output**: [1, 2, 2, 3, 3, 4, 8]

**Use Case**: Counting sort is efficient when the range of input values is relatively small compared to the number of elements to be sorted, making it suitable for sorting integers in a bounded range.
