# Greatest subsequential sum

Given a sequence of integers, find a continuous subsequence which maximizes the sum of its elements, that is, the elements of no other single subsequence add up to a value larger than this one.

An empty subsequence is considered to have the sum of \( 0 \); thus if all elements are negative, the result must be the empty sequence.

### Tests

1. `maximumSubsequence` should be a function.
2. `maximumSubsequence([ 1, 2, -1, 3, 10, -10 ])` should return an array.
3. `maximumSubsequence([ 1, 2, -1, 3, 10, -10 ])` should return `[ 1, 2, -1, 3, 10 ]`.
4. `maximumSubsequence([ 0, 8, 10, -2, -4, -1, -5, -3 ])` should return `[ 0, 8, 10 ]`.
5. `maximumSubsequence([ 9, 9, -10, 1 ])` should return `[ 9, 9 ]`.
6. `maximumSubsequence([ 7, 1, -5, -3, -8, 1 ])` should return `[ 7, 1 ]`.
7. `maximumSubsequence([ -3, 6, -1, 4, -4, -6 ])` should return `[ 6, -1, 4 ]`.
8. `maximumSubsequence([ -1, -2, 3, 5, 6, -2, -1, 4, -4, 2, -1 ])` should return `[ 3, 5, 6, -2, -1, 4 ]`.

### Answer:

```javascript
function maximumSubsequence(arr) {
    if (arr.length === 0) return [];

    let maxSum = 0;        // Maximum subsequence sum found
    let currentSum = 0;    // Sum of the current subsequence
    let start = 0;         // Start index of the current subsequence
    let end = 0;           // End index of the maximum subsequence
    let tempStart = 0;     // Temporary start index for tracking subsequences

    for (let i = 0; i < arr.length; i++) {
        currentSum += arr[i];

        if (currentSum > maxSum) {
            maxSum = currentSum;
            start = tempStart;
            end = i;
        }

        // If current sum goes negative, reset the current subsequence
        if (currentSum < 0) {
            currentSum = 0;
            tempStart = i + 1; // Start new subsequence from the next element
        }
    }

    // Return the maximum subsequence
    return arr.slice(start, end + 1);
}

// Test cases
console.log(maximumSubsequence([1, 2, -1, 3, 10, -10])); // [1, 2, -1, 3, 10]
console.log(maximumSubsequence([0, 8, 10, -2, -4, -1, -5, -3])); // [0, 8, 10]
console.log(maximumSubsequence([9, 9, -10, 1])); // [9, 9]
console.log(maximumSubsequence([7, 1, -5, -3, -8, 1])); // [7, 1]
console.log(maximumSubsequence([-3, 6, -1, 4, -4, -6])); // [6, -1, 4]
console.log(maximumSubsequence([-1, -2, 3, 5, 6, -2, -1, 4, -4, 2, -1])); // [3, 5, 6, -2, -1, 4]
```