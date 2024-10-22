# Gamma function

### Description

Implement one algorithm (or more) to compute the Gamma function (in the real field only).

The Gamma function can be defined as:
```
$\Gamma(x) = \displaystyle\int_0^\infty t^{x-1}e^{-t} dt$
```

### Tests

1. `gamma` should be a function.
2. `gamma(.1)` should return a number.
3. `gamma(.1)` should return `9.513507698668736`.
4. `gamma(.2)` should return `4.590843711998803`.
5. `gamma(.3)` should return `2.9915689876875904`.
6. `gamma(.4)` should return `2.218159543757687`.
7. `gamma(.5)` should return `1.7724538509055159`.

### Answer:

```javascript
function gamma(x) {
  // Lanczos approximation constants
  const p = [
    676.5203681218851,
    -1259.1392167224028,
    771.32342877765313,
    -176.61502916214059,
    12.507343278686905,
    -0.13857109526572012,
    9.9843695780195716e-6,
    1.5056327351493116e-7
  ];

  if (x < 0.5) {
    // Use reflection formula for x < 0.5
    return Math.PI / (Math.sin(Math.PI * x) * gamma(1 - x));
  }

  x -= 1;
  let a = 0.99999999999980993;
  const t = x + 7.5;
  
  for (let i = 0; i < p.length; i++) {
    a += p[i] / (x + i + 1);
  }

  return Math.sqrt(2 * Math.PI) * Math.pow(t, x + 0.5) * Math.exp(-t) * a;
}

// Testing the gamma function
console.log(gamma(0.1));  // Expected ~9.513507698668736
console.log(gamma(0.2));  // Expected ~4.590843711998803
console.log(gamma(0.3));  // Expected ~2.9915689876875904
console.log(gamma(0.4));  // Expected ~2.218159543757687
console.log(gamma(0.5));  // Expected ~1.7724538509055159
