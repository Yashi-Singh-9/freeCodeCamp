# Linear congruential generator

A linear congruential generator (LCG) is an algorithm that yields a sequence of pseudo-randomized numbers calculated with a discontinuous piecewise linear equation. All linear congruential generators use this formula:

$$r_{n + 1} = (a \times r_n + c) \bmod m$$

Where:

- $ r_0 $ is a seed.
- $r_1$, $r_2$, $r_3$, ..., are the random numbers.
- $a$, $c$, $m$ are constants.

If one chooses the values of $a$, $c$ and $m$ with care, then the generator produces a uniform distribution of integers from $0$ to $m - 1$.

LCG numbers have poor quality. $r_n$ and $r_{n + 1}$ are not independent, as true random numbers would be. Anyone who knows $r_n$ can predict $r_{n + 1}$, therefore LCG is not cryptographically secure. The LCG is still good enough for simple tasks like Miller-Rabin primality test, or FreeCell deals. Among the benefits of the LCG, one can easily reproduce a sequence of numbers, from the same $r_0$. One can also reproduce such sequence with a different programming language, because the formula is so simple.

---

Write a function that takes $r_0,a,c,m,n$ as parameters and returns $r_n$.

### Tests

1. `linearCongGenerator` should be a function.
2. `linearCongGenerator(324, 1145, 177, 2148, 3)` should return a number.
3. `linearCongGenerator(324, 1145, 177, 2148, 3)` should return `855`.
4. `linearCongGenerator(234, 11245, 145, 83648, 4)` should return `1110`.
5. `linearCongGenerator(85, 11, 1234, 214748, 5)` should return `62217`.
6. `linearCongGenerator(0, 1103515245, 12345, 2147483648, 1)` should return `12345`.
7. `linearCongGenerator(0, 1103515245, 12345, 2147483648, 2)` should return `1406932606`.

### Answer:

```javascript
function linearCongGenerator(r0, a, c, m, n) {
    let r = r0;
    for (let i = 0; i < n; i++) {
        r = (a * r + c) % m;
    }
    return r;
}
```