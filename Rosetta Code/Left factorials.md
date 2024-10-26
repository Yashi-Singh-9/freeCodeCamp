# Left factorials

### Description

Left factorials, $ !n $, may refer to either subfactorials or to factorial sums. The same notation can be confusingly seen used for the two different definitions. Sometimes, subfactorials (also known as derangements) may use any of the notations:

- $!n`$
- $!n$
- $n¡$

(It may not be visually obvious, but the last example uses an upside-down exclamation mark.) This task will be using this formula for left factorial:

$ !n = \sum_{k=0}^{n-1} k! $

where $!0 = 0$

---

Write a function to calculate the left factorial of a given number.

### Tests

1. `leftFactorial` should be a function.
2. `leftFactorial(0)` should return a number.
3. `leftFactorial(0)` should return `0`.
4. `leftFactorial(1)` should return `1`.
5. `leftFactorial(2)` should return `2`.
6. `leftFactorial(3)` should return `4`.
7. `leftFactorial(10)` should return `409114`.
8. `leftFactorial(17)` should return `22324392524314`.
9. `leftFactorial(19)` should return `6780385526348314`.

### Answer:

```javascript
function leftFactorial(n) {
    let sum = 0;
    let factorial = 1;

    for (let k = 0; k < n; k++) {
        if (k > 0) factorial *= k; // Calculate k! progressively
        sum += factorial; // Add k! to the sum
    }

    return sum;
}

// Testing the function with the examples given
console.log(leftFactorial(0)); // Expected: 0
console.log(leftFactorial(1)); // Expected: 1
console.log(leftFactorial(2)); // Expected: 2
console.log(leftFactorial(3)); // Expected: 4
console.log(leftFactorial(10)); // Expected: 409114
console.log(leftFactorial(17)); // Expected: 22324392524314
console.log(leftFactorial(19)); // Expected: 6780385526348314
```