# Overview of Common Sorting Algorithms

## Half Insertion Sort
- Modified version of insertion sort
- Searches for insertion position using binary search
- Reduces number of comparisons compared to standard insertion sort
- Still requires shifting elements, so movement operations remain O(n²)
- Time complexity: O(n log n) for comparisons, O(n²) overall
- Best suited for small arrays where movement cost is less significant

## Shell Sort (Hill Sort)
- Improvement over insertion sort
- Uses decreasing gap sequences to sort elements
- Process:
  1. Choose a gap sequence (e.g., n/2, n/4, n/8...)
  2. Sort elements at each gap distance using insertion sort
  3. Reduce gap and repeat until gap = 1
- Time complexity: depends on gap sequence
  - Best case: O(n log n)
  - Average case: O(n^1.25)
- Advantages:
  - Simple implementation
  - Works well for medium-sized arrays
  - In-place sorting

## Bubble Sort
- Simple comparison-based algorithm
- Repeatedly steps through the list
- Compares adjacent elements and swaps if needed
- Performance:
  - Time complexity: O(n²)
  - Space complexity: O(1)
- Characteristics:
  - Stable sort
  - In-place algorithm
  - Easy to implement but inefficient for large datasets

## Heap Sort
- Based on binary heap data structure
- Process:
  1. Build max heap from array
  2. Repeatedly extract maximum element
  3. Place it at the end of the array
- Performance:
  - Time complexity: O(n log n) in all cases
  - Space complexity: O(1)
- Advantages:
  - In-place sorting
  - Consistent performance
  - No worst case scenarios like QuickSort

## Two-Way Merge Sort
- Divide-and-conquer algorithm
- Process:
  1. Divide array into two halves
  2. Recursively sort each half
  3. Merge sorted halves
- Performance:
  - Time complexity: O(n log n)
  - Space complexity: O(n)
- Characteristics:
  - Stable sort
  - Predictable performance
  - Not in-place (requires extra space)

## Chained Radix Sort (Base Sort)
- Non-comparative sorting algorithm
- Sorts numbers by processing individual digits
- Basic concepts:
  1. Sort by least significant digit first
  2. Move to more significant digits
  3. Use counting sort for each digit
- Process example for base 10:
  - First pass: sort by ones digit
  - Second pass: sort by tens digit
  - Continue until most significant digit
- Performance:
  - Time complexity: O(d * n) where d is number of digits
  - Space complexity: O(n + b) where b is the base
- Characteristics:
  - Stable sort
  - Works best when range of possible digits is small
  - Efficient for integers or strings

## Comparison of Algorithms

### Time Complexity Summary
- O(n²):
  - Bubble Sort
  - Basic Insertion Sort
- O(n log n):
  - Heap Sort
  - Merge Sort
  - Half Insertion Sort (comparisons only)
- O(n^1.25):
  - Shell Sort (average case)
- O(d * n):
  - Radix Sort

### Space Complexity Summary
- O(1) (In-place):
  - Bubble Sort
  - Shell Sort
  - Heap Sort
- O(n):
  - Merge Sort
- O(n + b):
  - Radix Sort

### Best Use Cases
1. Small Arrays:
   - Bubble Sort
   - Insertion Sort

2. Medium Arrays:
   - Shell Sort
   - Heap Sort

3. Large Arrays:
   - Merge Sort
   - Radix Sort (for integers)

4. Nearly Sorted Data:
   - Insertion Sort
   - Shell Sort

5. Limited Memory:
   - Heap Sort
   - Shell Sort
