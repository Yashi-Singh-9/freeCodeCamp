# Factorial

### Description

Write a function to return the factorial of a number.

Factorial of a number is given by:

n! = n * (n-1) * (n-2) * ..... * 1

For example:

- `3! = 3 * 2 * 1 = 6`
- `4! = 4 * 3 * 2 * 1 = 24`

Note: `0! = 1`

### Tests

1. `factorial` should be a function.
2. `factorial(2)` should return a number.
3. `factorial(3)` should return 6.
4. `factorial(5)` should return 120.
5. `factorial(10)` should return 3,628,800.

### Answer:

```javascript
function factorial(n) {
    if (n === 0 || n === 1) {
        return 1;
    } else {
        let result = 1;
        for (let i = 2; i <= n; i++) {
            result *= i;
        }
        return result;
    }
}
```