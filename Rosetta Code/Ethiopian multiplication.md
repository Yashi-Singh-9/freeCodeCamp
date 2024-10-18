# Ethiopian multiplication

### Description

Ethiopian multiplication is a method of multiplying integers using only addition, doubling, and halving.

Method:

1. Take two numbers to be multiplied and write them down at the top of two columns
2. In the left-hand column repeatedly halve the last number, discarding any remainders, and write the result below the last in the same column, until you write a value of `1`
3. In the right-hand column repeatedly double the last number and write the result below. stop when you add a result in the same row as where the left hand column shows `1`
4. Examine the table produced and discard any row where the value in the left column is even
5. Sum the values in the right-hand column that remain to produce the result of multiplying the original two numbers together

For example: `17 × 34`

17   34

Halving the first column:

17      34 <br>
8 <br>
4 <br>
2 <br>
1

Doubling the second column:

17   34 <br>
8    68 <br>
4   136 <br>
2   272 <br>
1   544 

Strike-out rows whose first cell is even:

17   34 <br>
8    <strike>68</strike> <br>
4   <strike>136</strike> <br>
2   <strike>272</strike> <br>
1   544

Sum the remaining numbers in the right-hand column:
```
17   34
8    --
4   ---
2   ---
1   544
   ====
    578
```
So `17` multiplied by `34`, by the Ethiopian method is `578`.

---

The task is to define three named functions/methods/procedures/subroutines:

1. one to halve an integer,
2. one to double an integer, and
3. one to state if an integer is even

Use these functions to create a function that does Ethiopian multiplication.

---

### Tests

1. `eth_mult` should be a function.
2. `eth_mult(17,34)` should return `578`.
3. `eth_mult(23,46)` should return `1058`.
4. `eth_mult(12,27)` should return `324`.
5. `eth_mult(56,98)` should return `5488`.
6. `eth_mult(63,74)` should return `4662`.

### Answer:

```javascript
// Function to halve an integer
function halve(num) {
    return Math.floor(num / 2);
}

// Function to double an integer
function double(num) {
    return num * 2;
}

// Function to check if an integer is even
function isEven(num) {
    return num % 2 === 0;
}

// Function to perform Ethiopian multiplication
function eth_mult(a, b) {
    let sum = 0;

    while (a >= 1) {
        if (!isEven(a)) {
            sum += b;
        }

        a = halve(a);
        b = double(b);
    }

    return sum;
}

// Example usage with test cases
console.log(eth_mult(17, 34));  // Expected output: 578
console.log(eth_mult(23, 46));  // Expected output: 1058
console.log(eth_mult(12, 27));  // Expected output: 324
console.log(eth_mult(56, 98));  // Expected output: 5488
console.log(eth_mult(63, 74));  // Expected output: 4662
```