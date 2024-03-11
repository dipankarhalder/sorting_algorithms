### Sorting Algorithms

1. Bubble Sort:

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

2. Selection Sort

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

2. Insertion Sort

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
