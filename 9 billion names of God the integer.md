# 9 billion names of God the integer

This task is a variation of the short story by Arthur C. Clarke.

(Solvers should be aware of the consequences of completing this task.)

In detail, to specify what is meant by a "name":

- The integer 1 has 1 name "1".
- The integer 2 has 2 names "1+1" and "2".
- The integer 3 has 3 names "1+1+1", "2+1", and "3".
- The integer 4 has 5 names "1+1+1+1", "2+1+1", "2+2", "3+1", "4".
- The integer 5 has 7 names "1+1+1+1+1", "2+1+1+1", "2+2+1", "3+1+1", "3+2", "4+1", "5".
- This can be visualized in the following form:
```
          1
        1   1
      1   1   1
    1   2   1   1
  1   2   2   1   1
1   3   3   2   1   1
```
Where row  n corresponds to integer  n, and each column  C in row  m from left to right corresponds to the number of names beginning with  C.

Optionally note that the sum of the  n-th row  P(n) is the integer partition function.

---

Implement a function that returns the sum of the  n-th row.

### Tests

1. `numberOfNames` should be function.
2. `numberOfNames(5)` should equal 7.
3. `numberOfNames(12)` should equal 77.
4. `numberOfNames(18)` should equal 385.
5. `numberOfNames(23)` should equal 1255.
6. `numberOfNames(42)` should equal 53174.
7. `numberOfNames(123)` should equal 2552338241.

### Answer:

```javascript
function numberOfNames(n) {
    // Create an array dp where dp[i] represents the number of partitions for integer i
    let dp = Array(n + 1).fill(0);
    dp[0] = 1; // There's 1 way to partition 0, which is with an empty set

    // Dynamic programming approach to fill in the partition counts
    for (let i = 1; i <= n; i++) {
        for (let j = i; j <= n; j++) {
            dp[j] += dp[j - i];
        }
    }

    // The result is the total number of partitions for n, stored in dp[n]
    return dp[n];
}

// Testing the function with the provided test cases
console.log(numberOfNames(5));    // Expected output: 7
console.log(numberOfNames(12));   // Expected output: 77
console.log(numberOfNames(18));   // Expected output: 385
console.log(numberOfNames(23));   // Expected output: 1255
console.log(numberOfNames(42));   // Expected output: 53174
console.log(numberOfNames(123));  // Expected output: 2552338241

```