### Linear Search 📏

**Definition**: Linear search, also known as sequential search, is a simple searching algorithm that sequentially checks each element in a list or array until the target element is found or the end of the list is reached. It's the most basic and intuitive searching algorithm, suitable for small lists or unsorted arrays. 🔍

**Neat and Best Code**:
```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1

# Example Usage:
arr = [10, 20, 30, 40, 50]
target = 30
index = linear_search(arr, target)
if index != -1:
    print(f"Element {target} found at index {index}")
else:
    print(f"Element {target} not found in the array")
```

**Input**: An array `arr` of elements and a target element to search for.

**Output**: The index of the target element in the array if found, or -1 if the target element is not present in the array.

**Implementation**:
1. Iterate through each element in the array sequentially.
2. Compare each element with the target element.
3. If a match is found, return the index of the element.
4. If the target element is not found after iterating through the entire array, return -1.

**Logic**: Linear search works by checking each element in the array one by one until the target element is found or the end of the array is reached.

**Example**: 
- **Input**: [10, 20, 30, 40, 50], target = 30
- **Output**: Element 30 found at index 2

**Use Case**: Linear search is suitable for small lists or unsorted arrays where the elements are not arranged in any particular order. However, it's not efficient for large datasets due to its linear time complexity.
