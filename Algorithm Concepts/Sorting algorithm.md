Sorting algorithms are algorithms that arrange elements in a specific order, usually ascending or descending. Here are some common sorting algorithms:

1. **Bubble Sort**:
   - Compares adjacent elements and swaps them if they are in the wrong order.
   - Repeats this process until the list is sorted.
   - Simple to implement but inefficient for large lists.

2. **Selection Sort**:
   - Divides the input list into a sorted and an unsorted region.
   - Finds the minimum element in the unsorted region and swaps it with the leftmost element of the unsorted region.
   - Repeats this process until the entire list is sorted.
   - Not very efficient for large lists but performs better than Bubble Sort.

3. **Insertion Sort**:
   - Builds the final sorted list one element at a time by repeatedly taking elements from the unsorted part and inserting them into their correct position in the sorted part.
   - Efficient for small lists and partially sorted lists but not ideal for large lists.

4. **Merge Sort**:
   - Divides the input list into two halves, sorts each half recursively, and then merges the sorted halves.
   - A divide-and-conquer algorithm with a time complexity of O(n log n).
   - Efficient and stable for large lists but requires additional memory space.

5. **Quick Sort**:
   - Chooses a pivot element and partitions the list into two sublists: elements less than the pivot and elements greater than the pivot.
   - Recursively sorts the sublists.
   - Efficient and widely used for its average-case time complexity of O(n log n), but can degrade to O(n^2) in the worst case.

6. **Heap Sort**:
   - Builds a binary heap from the input list and repeatedly extracts the maximum element from the heap and rebuilds the heap.
   - Efficient and has a worst-case time complexity of O(n log n), but not stable.

7. **Counting Sort**:
   - Assumes that the input consists of integers within a specific range.
   - Counts the occurrences of each integer and uses this information to place each element in its correct position in the output array.
   - Linear time complexity but requires additional memory space.

8. **Radix Sort**:
   - Sorts numbers by processing individual digits from the least significant digit to the most significant digit.
   - Performs counting sort for each digit position.
   - Efficient for sorting integers with fixed length but requires additional memory space.

Each sorting algorithm has its advantages and disadvantages, and the choice of algorithm depends on factors such as the size of the input, the nature of the data, and the desired performance characteristics.
