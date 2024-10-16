# Averages/Pythagorean means

### Description

Compute all three of the [Pythagorean means](https://en.wikipedia.org/wiki/Pythagorean_means) of the set of integers 1 through 10 (inclusive).

[](Images/avg.png)

---

When writing your function, assume the input is an ordered array of all-inclusive numbers.

For the answer, please output an object in the following format:
```
{
  values: {
    Arithmetic: 5.5,
    Geometric: 4.528728688116765,
    Harmonic: 3.414171521474055
  },
  test: 'is A >= G >= H ? yes'
}
```

### Tests

1. `pythagoreanMeans` should be a function.
2. `pythagoreanMeans([1, 2, ..., 10])` should equal the same output above.

### Answer:

```javascript
function pythagoreanMeans(numbers) {
    const n = numbers.length;

    // Calculate Arithmetic Mean (A)
    const A = numbers.reduce((sum, num) => sum + num, 0) / n;

    // Calculate Geometric Mean (G)
    const product = numbers.reduce((prod, num) => prod * num, 1);
    const G = Math.pow(product, 1 / n);

    // Calculate Harmonic Mean (H)
    const reciprocalSum = numbers.reduce((sum, num) => sum + 1 / num, 0);
    const H = n / reciprocalSum;

    // Check the inequality A >= G >= H
    const inequalityTest = (A >= G && G >= H) ? 'yes' : 'no';

    // Prepare the output object
    return {
        values: {
            Arithmetic: A,
            Geometric: G,
            Harmonic: H
        },
        test: `is A >= G >= H ? ${inequalityTest}`
    };
}

// Test the function with the integers from 1 to 10
const result = pythagoreanMeans([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);

// Output the result
console.log(result);
```