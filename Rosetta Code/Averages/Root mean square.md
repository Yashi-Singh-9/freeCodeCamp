# Averages/Root mean square

### Description

Compute the Root Mean Square (RMS) of the numbers 1 through 10 inclusive.

The RMS is calculated by taking the square root of the mean of the squares of the numbers, given by the equation:

[](Images/roots.png)

### Tests

1. `rms` should be a function.
2. `rms([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])` should equal `6.2048368229954285`.

### Answers:

```javascript
function rms(numbers) {
    // Calculate the sum of the squares
    const sumOfSquares = numbers.reduce((sum, num) => sum + Math.pow(num, 2), 0);
    
    // Calculate the mean of the squares
    const meanOfSquares = sumOfSquares / numbers.length;
    
    // Return the square root of the mean of the squares
    return Math.sqrt(meanOfSquares);
}

// Test the rms function with numbers from 1 to 10
const result = rms([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
console.log(result); // Output: approximately 6.2048368229954285
```