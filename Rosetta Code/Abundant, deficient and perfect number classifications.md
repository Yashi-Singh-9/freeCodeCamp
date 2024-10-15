# Abundant, deficient and perfect number classifications

### Description

These define three classifications of positive integers based on their proper divisors.

Let  P(n) be the sum of the proper divisors of `n` where proper divisors are all positive integers `n` other than `n` itself.

If `P(n) < n` then `n` is classed as `deficient`

If `P(n) === n` then `n` is classed as `perfect`

If `P(n) > n` then `n` is classed as `abundant`

Example: `6` has proper divisors of `1`, `2`, and `3`. `1 + 2 + 3 = 6`, so `6` is classed as a perfect number.

---

Implement a function that calculates how many of the integers from `1` to `num` (inclusive) are in each of the three classes. Output the result as an array in the following format `[deficient, perfect, abundant]`.

---

### Tests

1. `getDPA` should be a function.
2. `getDPA(5000)` should return an array.
3. `getDPA(5000)` return array should have a length of `3`.
4. `getDPA(5000)` should return `[3758, 3, 1239]`.
5. `getDPA(10000)` should return `[7508, 4, 2488]`.
6. `getDPA(20000)` should return `[15043, 4, 4953]`.

### Answer: 

```javascript
function getDPA(num) {
    let deficient = 0;
    let perfect = 0;
    let abundant = 0;

    function sumOfProperDivisors(n) {
        let sum = 0; 
        for (let i = 1; i <= Math.floor(n / 2); i++) {
            if (n % i === 0) {
                sum += i;
            }
        }
        return sum;
    }

    for (let i = 1; i <= num; i++) {
        const sum = sumOfProperDivisors(i);
        
        if (sum < i) {
            deficient++;
        } else if (sum === i) {
            perfect++;
        } else {
            abundant++;
        }
    }

    return [deficient, perfect, abundant];
}

// Example tests
console.log(getDPA(5000));  // Should print: [3758, 3, 1239]
console.log(getDPA(10000)); // Should print: [7508, 4, 2488]
console.log(getDPA(20000)); // Should print: [15043, 4, 4953]

```