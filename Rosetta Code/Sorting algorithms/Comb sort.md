# Sorting algorithms/Comb sort

### Descritpion

Implement a comb sort.

The Comb Sort is a variant of the Bubble Sort.

Like the Shell sort, the Comb Sort increases the gap used in comparisons and exchanges.

Dividing the gap by $(1-e^{-\varphi})^{-1} \approx 1.247330950103979$ works best, but 1.3 may be more practical.

Some implementations use the insertion sort once the gap is less than a certain amount.

Variants:

- Combsort11 makes sure the gap ends in (11, 8, 6, 4, 3, 2, 1), which is significantly faster than the other two possible endings.
- Combsort with different endings changes to a more efficient sort when the data is almost sorted (when the gap is small). Comb sort with a low gap isn't much better than the Bubble Sort.

Pseudocode:

```
function combsort(array input)
  gap := input.size //initialize gap size
  loop until gap = 1 and swaps = 0
    //update the gap value for a next comb. Below is an example
    gap := int(gap / 1.25)
    if gap < 1 
      //minimum gap is 1
      gap := 1
    end if
    i := 0
    swaps := 0 //see Bubble Sort for an explanation
    //a single "comb" over the input list
    loop until i + gap >= input.size //see Shell sort for similar idea
      if input[i] > input[i+gap]
        swap(input[i], input[i+gap])
        swaps := 1 // Flag a swap has occurred, so the
            // list is not guaranteed sorted
      end if
      i := i + 1
    end loop
  end loop
end function
```
---

Write a function that sorts a given array using Comb sort.

### Tests

1. `combSort` should be a function.
2. `combSort([25, 32, 12, 7, 20])` should return an array.
3. `combSort([25, 32, 12, 7, 20])` should return `[7, 12, 20, 25, 32]`.
4. `combSort([38, 45, 35, 8, 13])` should return `[8, 13, 35, 38, 45]`.
5. `combSort([43, 36, 20, 34, 24])` should return `[20, 24, 34, 36, 43]`.
6. `combSort([12, 33, 26, 18, 1, 16, 38])` should return `[1, 12, 16, 18, 26, 33, 38]`.
7. `combSort([3, 39, 48, 16, 1, 4, 29])` should return `[1, 3, 4, 16, 29, 39, 48]`.

### Solution:

```javascript
function combSort(arr) {
  const shrinkFactor = 1.3; // 1.3 is a practical choice for shrink factor
  let gap = arr.length; // Initial gap size
  let swaps = true; // Flag to check if any swaps were made

  while (gap > 1 || swaps) {
    // Update gap size
    gap = Math.floor(gap / shrinkFactor);
    if (gap < 1) gap = 1; // Minimum gap is 1

    swaps = false; // Reset the swap flag for each pass

    for (let i = 0; i + gap < arr.length; i++) {
      if (arr[i] > arr[i + gap]) {
        // Swap if elements are out of order
        [arr[i], arr[i + gap]] = [arr[i + gap], arr[i]];
        swaps = true; // Set swap flag if a swap is made
      }
    }
  }

  return arr; // Return the sorted array
}
```