# Generator/Exponential

### Description

A generator is an executable entity (like a function or procedure) that contains code that yields a sequence of values, one at a time, so that each time you call the generator, the next value in the sequence is provided.

Generators are often built on top of coroutines or objects so that the internal state of the object is handled "naturally".

Generators are often used in situations where a sequence is potentially infinite, and where it is possible to construct the next value of the sequence with only minimal state.

---

Write a function that uses generators to generate squares and cubes. Create a new generator that filters all cubes from the generator of squares.

The function should return the \( n^{th} \) value of the filtered generator.

For example for \(n=7\), the function should return 81 as the sequence would be 4, 9, 16, 25, 36, 49, 81. Here 64 is filtered out, as it is a cube.

### Tests

1. `exponentialGenerator` should be a function.
2. `exponentialGenerator()` should return a number.
3. `exponentialGenerator(10)` should return `144`.
4. `exponentialGenerator(12)` should return `196`.
5. `exponentialGenerator(14)` should return `256`.
6. `exponentialGenerator(20)` should return `484`.
7. `exponentialGenerator(25)` should return `784`.

### Answer:

```javascript
function* squares() {
    let i = 2;
    while (true) {
        yield i * i;
        i++;
    }
}

function* cubes() {
    let i = 2;
    while (true) {
        yield i * i * i;
        i++;
    }
}

function* filterCubes(squaresGen, cubesGen) {
    let square = squaresGen.next().value;
    let cube = cubesGen.next().value;
    
    while (true) {
        if (square === cube) {
            square = squaresGen.next().value;
            cube = cubesGen.next().value;
        } else if (square < cube) {
            yield square;
            square = squaresGen.next().value;
        } else {
            cube = cubesGen.next().value;
        }
    }
}

function exponentialGenerator(n) {
    const squaresGen = squares();
    const cubesGen = cubes();
    const filteredGen = filterCubes(squaresGen, cubesGen);

    let result;
    for (let i = 0; i < n; i++) {
        result = filteredGen.next().value;
    }

    return result;
}

// Test the function with some examples
console.log(exponentialGenerator(2));  // Output: 9
console.log(exponentialGenerator(10)); // Output: 144
console.log(exponentialGenerator(12)); // Output: 196
console.log(exponentialGenerator(14)); // Output: 256
console.log(exponentialGenerator(20)); // Output: 484
console.log(exponentialGenerator(25)); // Output: 784
```