### Interpolation Search ➗

**Definition**: Interpolation search is an improved searching algorithm that works on sorted arrays of numbers. It calculates the probable position of the target element by using interpolation formula, which estimates the position of the target element based on the values of the endpoints of the search interval and the value of the target itself. It's particularly effective for uniformly distributed data and can be more efficient than binary search in certain scenarios. 📈

**Neat and Best Code**:
```python
def interpolation_search(arr, target):
    low, high = 0, len(arr) - 1
    
    while low <= high and arr[low] <= target <= arr[high]:
        if low == high:
            if arr[low] == target:
                return low
            return -1
        
        pos = low + ((target - arr[low]) * (high - low)) // (arr[high] - arr[low])
        
        if arr[pos] == target:
            return pos
        elif arr[pos] < target:
            low = pos + 1
        else:
            high = pos - 1
    
    return -1

# Example Usage:
arr = [10, 20, 30, 40, 50]
target = 30
index = interpolation_search(arr, target)
if index != -1:
    print(f"Element {target} found at index {index}")
else:
    print(f"Element {target} not found in the array")
```

**Input**: A sorted array `arr` of elements and a target element to search for.

**Output**: The index of the target element in the array if found, or -1 if the target element is not present in the array.

**Implementation**:
1. Initialize two pointers, `low` and `high`, to the beginning and end of the array, respectively.
2. Repeat the following steps while `low` is less than or equal to `high` and the target element is within the search interval:
   - Calculate the probable position `pos` of the target element using the interpolation formula.
   - If the target element is found at position `pos`, return its index.
   - If the target element is greater than the value at position `pos`, search in the right half of the array.
   - If the target element is less than the value at position `pos`, search in the left half of the array.
3. If the target element is not found after the loop, return -1.

**Logic**: Interpolation search estimates the position of the target element based on the values of the endpoints of the search interval and the value of the target itself, resulting in a more precise guess compared to binary search, especially for uniformly distributed data.

**Example**: 
- **Input**: [10, 20, 30, 40, 50], target = 30
- **Output**: Element 30 found at index 2

**Use Case**: Interpolation search is particularly effective for searching in large datasets with uniformly distributed values, where the target element is likely to be closer to its actual position within the array.
