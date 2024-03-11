### Sorting Algorithms

#### 1. Bubble Sort:

Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted. It gets its name because smaller elements gradually "bubble" to the top of the list.

Bubble Sort has a time complexity of **O(n^2)**.

```javascript
// using JavaScript
function bubbleSort(arr) {
  const n = arr.length;

  // Traverse through all elements
  for (let i = 0; i < n; i++) {
    // Last i elements are already in place, so don't need to check
    for (let j = 0; j < n - i - 1; j++) {
      // Swap if the element found is greater than the next element
      if (arr[j] > arr[j + 1]) {
        // Using destructuring assignment to swap elements
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
      }
    }
  }
}

let arr = [64, 34, 25, 12, 22, 11, 90];
bubbleSort(arr);
console.log("Bubble sort result:", arr);
```

#### 2. Selection Sort

Selection Sort is a simple sorting algorithm that divides the input array into two parts: a sorted subarray and an unsorted subarray. It repeatedly selects the smallest (or largest, depending on the sorting order) element from the unsorted subarray and moves it to the end of the sorted subarray.

Selection Sort has a time complexity of **O(n^2)**.

```javascript
// using JavaScript
function selectionSort(arr) {
  const n = arr.length;

  // Traverse through all elements in the array
  for (let i = 0; i < n - 1; i++) {
    // Assume the current element is the minimum
    let minIndex = i;

    // Iterate through the unsorted subarray to find the minimum element
    for (let j = i + 1; j < n; j++) {
      // If the current element is smaller than the assumed minimum,
      // update the index of the minimum element
      if (arr[j] < arr[minIndex]) {
        minIndex = j;
      }
    }

    // Swap the minimum element with the first element of the unsorted subarray
    if (minIndex !== i) {
      let temp = arr[i];
      arr[i] = arr[minIndex];
      arr[minIndex] = temp;
    }
  }
}

let arr = [64, 34, 25, 12, 22, 11, 90];
selectionSort(arr);
console.log("Selection sort result:", arr);
```

#### 3. Insertion Sort

Insertion Sort is another simple sorting algorithm that builds the final sorted array one item at a time. It iterates through the input array and grows a sorted array behind it. At each iteration, the algorithm removes one element from the input data, finds its correct position within the sorted array, and inserts it there.

Insertion Sort has a time complexity of **O(n^2)**.

```javascript
// using JavaScript
function insertionSort(arr) {
  const n = arr.length;

  // Traverse through all elements in the array
  for (let i = 1; i < n; i++) {
    // Select the current element to be inserted into the sorted subarray
    let currentElement = arr[i];
    let j = i - 1;

    // Move elements of the sorted subarray that are greater than the current element
    // to one position ahead of their current position
    while (j >= 0 && arr[j] > currentElement) {
      arr[j + 1] = arr[j];
      j--;
    }

    // Insert the current element into its correct position in the sorted subarray
    arr[j + 1] = currentElement;
  }
}

let arr = [64, 34, 25, 12, 22, 11, 90];
insertionSort(arr);
console.log("Insertion sort result:", arr);
```

#### 4. Merge Sort

Merge Sort is a popular divide-and-conquer sorting algorithm. It works by recursively dividing the input array into smaller subarrays until each subarray contains only one element. Then, it merges these subarrays back together in a sorted manner.

Merge Sort has a time complexity of **O(n log n)**

```javascript
// using JavaScript
function mergeSort(arr) {
  const n = arr.length;

  // Base case: If the array has only one element, it is already sorted
  if (n <= 1) {
    return arr;
  }

  // Calculate the middle index of the array
  const mid = Math.floor(n / 2);

  // Divide the array into two subarrays
  const leftSubarray = arr.slice(0, mid);
  const rightSubarray = arr.slice(mid);

  // Recursively sort the left and right subarrays
  const sortedLeft = mergeSort(leftSubarray);
  const sortedRight = mergeSort(rightSubarray);

  // Merge the sorted subarrays
  return merge(sortedLeft, sortedRight);
}

function merge(left, right) {
  let result = [];
  let leftIndex = 0;
  let rightIndex = 0;

  // Compare elements from both arrays and merge them in sorted order
  while (leftIndex < left.length && rightIndex < right.length) {
    if (left[leftIndex] < right[rightIndex]) {
      result.push(left[leftIndex]);
      leftIndex++;
    } else {
      result.push(right[rightIndex]);
      rightIndex++;
    }
  }

  // Merge remaining elements from the left subarray, if any
  while (leftIndex < left.length) {
    result.push(left[leftIndex]);
    leftIndex++;
  }

  // Merge remaining elements from the right subarray, if any
  while (rightIndex < right.length) {
    result.push(right[rightIndex]);
    rightIndex++;
  }

  return result;
}

let arr = [64, 34, 25, 12, 22, 11, 90];
let sortedArr = mergeSort(arr);
console.log("Merge sort result:", arr);
```

#### 5. Quick Sort

Quick Sort is a widely used sorting algorithm known for its efficiency and average-case performance of O(n log n). It follows the divide-and-conquer approach by recursively partitioning the array into smaller subarrays based on a chosen pivot element.

Quick Sort has an average-case time complexity of **O(n log n)** and a worst-case time complexity of **O(n^2)**.

```javascript
// using JavaScript
function quickSort(arr, left = 0, right = arr.length - 1) {
  if (left < right) {
    // Partition the array and get the index of the pivot element
    const pivotIndex = partition(arr, left, right);

    // Recursively sort the subarrays before and after the pivot element
    quickSort(arr, left, pivotIndex - 1);
    quickSort(arr, pivotIndex + 1, right);
  }
  return arr;
}

function partition(arr, left, right) {
  // Choose the rightmost element as the pivot
  const pivot = arr[right];
  let i = left - 1;

  // Move elements smaller than the pivot to the left of the pivot
  for (let j = left; j < right; j++) {
    if (arr[j] <= pivot) {
      i++;
      // Swap arr[i] and arr[j]
      [arr[i], arr[j]] = [arr[j], arr[i]];
    }
  }

  // Move the pivot element to its correct position
  [arr[i + 1], arr[right]] = [arr[right], arr[i + 1]];

  // Return the index of the pivot element
  return i + 1;
}

let arr = [64, 34, 25, 12, 22, 11, 90];
quickSort(arr);
console.log("Quick sort result:", arr);
```

#### 6. Heap Sort

Heap Sort is a comparison-based sorting algorithm that builds a binary heap from the input array and repeatedly extracts the maximum (for a max-heap) or minimum (for a min-heap) element from the heap, thereby forming a sorted array.

Heap Sort has a time complexity of **O(n log n)**.

```javascript
// using JavaScript
function heapSort(arr) {
  // Build the max heap
  buildMaxHeap(arr);

  // Extract elements from the heap one by one
  for (let i = arr.length - 1; i > 0; i--) {
    // Move the current root (maximum element) to the end of the array
    [arr[0], arr[i]] = [arr[i], arr[0]];

    // Call maxHeapify on the reduced heap
    maxHeapify(arr, 0, i);
  }

  return arr;
}

function buildMaxHeap(arr) {
  const n = arr.length;
  const lastNonLeafIndex = Math.floor(n / 2) - 1;

  // Build a max heap by calling maxHeapify on each non-leaf node
  for (let i = lastNonLeafIndex; i >= 0; i--) {
    maxHeapify(arr, i, n);
  }
}

function maxHeapify(arr, index, heapSize) {
  const leftChildIndex = 2 * index + 1;
  const rightChildIndex = 2 * index + 2;
  let largest = index;

  // Find the largest element among the current node, its left child, and its right child
  if (leftChildIndex < heapSize && arr[leftChildIndex] > arr[largest]) {
    largest = leftChildIndex;
  }

  if (rightChildIndex < heapSize && arr[rightChildIndex] > arr[largest]) {
    largest = rightChildIndex;
  }

  // If the largest element is not the current node, swap it with the largest child
  if (largest !== index) {
    [arr[index], arr[largest]] = [arr[largest], arr[index]];

    // Recursively call maxHeapify on the affected subtree
    maxHeapify(arr, largest, heapSize);
  }
}

let arr = [64, 34, 25, 12, 22, 11, 90];
heapSort(arr);
console.log("Heap sort result:", arr);
```
