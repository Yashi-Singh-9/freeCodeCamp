# Zeckendorf number representation

Just as numbers can be represented in a positional notation as sums of multiples of the powers of ten (decimal) or two (binary); all the positive integers can be represented as the sum of one or zero times the distinct members of the Fibonacci series. Recall that the first six distinct Fibonacci numbers are: `1, 2, 3, 5, 8, 13`.

The decimal number eleven can be written as `0*13 + 1*8 + 0*5 + 1*3 + 0*2 + 0*1` or `010100` in positional notation where the columns represent multiplication by a particular member of the sequence. Leading zeroes are dropped so that 11 decimal becomes `10100`. 10100 is not the only way to make 11 from the Fibonacci numbers however `0*13 + 1*8 + 0*5 + 0*3 + 1*2 + 1*1` or 010011 would also represent decimal 11. For a true Zeckendorf number there is the added restriction that no two consecutive Fibonacci numbers can be used which leads to the former unique solution.

---

Write a function that generates and returns the Zeckendorf number representation of `n`.

### Tests

1. `zeckendorf` should be a function.
2. `zeckendorf(0)` should return `0`.
3. `zeckendorf(1)` should return `1`.
4. `zeckendorf(2)` should return `10`.
5. `zeckendorf(3)` should return `100`.
6. `zeckendorf(4)` should return `101`.
7. `zeckendorf(5)` should return `1000`.
8. `zeckendorf(6)` should return `1001`.
9. `zeckendorf(7)` should return `1010`.
10. `zeckendorf(8)` should return `10000`.
11. `zeckendorf(9)` should return `10001`.
12. `zeckendorf(10)` should return `10010`.
13. `zeckendorf(11)` should return `10100`.
14. `zeckendorf(12)` should return `10101`.
15. `zeckendorf(13)` should return `100000`.
16. `zeckendorf(14)` should return `100001`.
17. `zeckendorf(15)` should return `100010`.
18. `zeckendorf(16)` should return `100100`.
19. `zeckendorf(17)` should return `100101`.
20. `zeckendorf(18)` should return `101000`.
21. `zeckendorf(19)` should return `101001`.
22. `zeckendorf(20)` should return `101010`.

### Solution

```javascript
function zeckendorf(n) {
  if (n === 0) return '0'; // Special case for 0

  // Step 1: Generate Fibonacci numbers up to n
  let fibs = [1, 2]; // Starting Fibonacci numbers (we skip 0 since it's not needed)
  while (fibs[fibs.length - 1] <= n) {
    fibs.push(fibs[fibs.length - 1] + fibs[fibs.length - 2]);
  }

  // Step 2: Create Zeckendorf representation
  let result = [];
  for (let i = fibs.length - 1; i >= 0; i--) {
    if (fibs[i] <= n) {
      result.push(1); // Use this Fibonacci number
      n -= fibs[i];  // Subtract the Fibonacci number
    } else {
      if (result.length > 0) {
        result.push(0); // Don't use this Fibonacci number
      }
    }
  }

  // Step 3: Convert the result to a string
  return result.join('');
}

// Test cases:
console.log(zeckendorf(0));  // "0"
console.log(zeckendorf(1));  // "1"
console.log(zeckendorf(2));  // "10"
console.log(zeckendorf(3));  // "100"
console.log(zeckendorf(4));  // "101"
console.log(zeckendorf(5));  // "1000"
console.log(zeckendorf(6));  // "1001"
console.log(zeckendorf(7));  // "1010"
console.log(zeckendorf(8));  // "10000"
console.log(zeckendorf(9));  // "10001"
console.log(zeckendorf(10)); // "10010"
console.log(zeckendorf(11)); // "10100"
console.log(zeckendorf(12)); // "10101"
console.log(zeckendorf(13)); // "100000"
console.log(zeckendorf(14)); // "100001"
console.log(zeckendorf(15)); // "100010"
console.log(zeckendorf(16)); // "100100"
console.log(zeckendorf(17)); // "100101"
console.log(zeckendorf(18)); // "101000"
console.log(zeckendorf(19)); // "101001"
console.log(zeckendorf(20)); // "101010"
```