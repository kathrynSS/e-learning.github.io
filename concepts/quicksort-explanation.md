# Quick Sort: Basic Ideas

## Core Concept
Quick Sort is a divide-and-conquer algorithm that works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays according to whether they are less than or greater than the pivot.

## How It Works

### Main Steps
1. **Choose Pivot**: Select a pivot element from the array
2. **Partition**: Rearrange elements so that:
   - Elements smaller than pivot go to the left
   - Elements larger than pivot go to the right
   - Pivot is in its final position
3. **Recursion**: Recursively apply steps 1-2 to sub-arrays

### Visual Example
Array: [64, 34, 25, 12, 22, 11, 90]
Pivot: 64

```
Initial Partition:
[64, 34, 25, 12, 22, 11, 90]
Choose 64 as pivot

Partitioning Process:
[34, 25, 12, 22, 11, 64, 90]
(All elements ≤64 moved left, >64 moved right)

Recursive Partitioning:
Left: [34, 25, 12, 22, 11]
Right: [90]

Continue recursively...
```

## Implementation Example
```python
def quicksort(arr, low, high):
    def partition(low, high):
        pivot = arr[high]  # Choose last element as pivot
        i = low - 1  # Index of smaller element
        
        for j in range(low, high):
            # If current element is smaller than or equal to pivot
            if arr[j] <= pivot:
                i += 1  # Increment index of smaller element
                arr[i], arr[j] = arr[j], arr[i]
        
        arr[i + 1], arr[high] = arr[high], arr[i + 1]
        return i + 1
    
    if low < high:
        # pi is partitioning index
        pi = partition(low, high)
        
        # Separately sort elements before and after partition
        quicksort(arr, low, pi - 1)
        quicksort(arr, pi + 1, high)
```

## Key Features

### Pivot Selection Strategies
1. **First Element**: Simple but poor for sorted arrays
2. **Last Element**: Simple but poor for reverse sorted arrays
3. **Random Element**: Good average case performance
4. **Median-of-Three**: Best practice for most cases
   - Takes median of first, middle, and last elements

### Performance Analysis

#### Time Complexity
- Best Case: O(n log n)
  - Occurs when partition always divides array in half
- Average Case: O(n log n)
  - Most practical implementations achieve this
- Worst Case: O(n²)
  - Occurs with poor pivot selection (e.g., already sorted array)

#### Space Complexity
- O(log n) average case
- O(n) worst case due to recursion stack

### Advantages
1. Usually fastest in practice
2. In-place sorting (minimal extra space)
3. Cache friendly
4. Average case O(n log n) performance

### Disadvantages
1. Not stable (equal elements may reorder)
2. Poor worst-case performance
3. Recursive (uses stack space)

## Optimizations

### 1. Insertion Sort Hybrid
```python
def optimized_quicksort(arr, low, high):
    # Use insertion sort for small subarrays
    if high - low + 1 <= 10:
        insertion_sort(arr, low, high)
        return
    
    # Regular quicksort for larger subarrays
    if low < high:
        pi = partition(arr, low, high)
        optimized_quicksort(arr, low, pi - 1)
        optimized_quicksort(arr, pi + 1, high)
```

### 2. Three-Way Partitioning
- Handles equal elements efficiently
- Particularly useful with many duplicate elements

## Common Applications
1. General purpose sorting
2. Used in standard libraries (e.g., C++ STL)
3. Virtual memory systems
4. Numerical computations
5. When average-case performance is critical

## Best Practices
1. Always use a good pivot selection strategy
2. Consider hybrid approaches for small subarrays
3. Handle equal elements efficiently
4. Be aware of stack space in recursive implementations
5. Use iterative version for very large arrays
