# Sum of a series

### Description

Compute the n<sup>th</sup> term of a series, i.e. the sum of the n first terms of the corresponding sequence. Informally this value, or its limit when n tends to infinity, is also called the sum of the series, thus the title of this task. For this task, use: $S_n = \displaystyle\sum_{k=1}^n \frac{1}{k^2}$.

---

Write a function that take $a$ and $b$ as parameters and returns the sum of $a^{th}$ to $b^{th}$ members of the sequence.

### Tests

1. `sum` should be a function.
2. `sum(1, 100)` should return a number.
3. `sum(1, 100)` should return `1.6349839001848923`.
4. `sum(33, 46)` should return `0.009262256361481223`.
5. `sum(21, 213)` should return `0.044086990748706555`.
6. `sum(11, 111)` should return `0.08619778593108679`.
7. `sum(1, 10)` should return `1.5497677311665408`.

### Solution

```javascript
function sum(a, b) {
    let result = 0;
    for (let k = a; k <= b; k++) {
        result += 1 / (k * k); // adding the value of 1/k^2 to the sum
    }
    return result;
}
```