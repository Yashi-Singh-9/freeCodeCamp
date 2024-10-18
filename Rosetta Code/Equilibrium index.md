# Equilibrium index

### Description:

An equilibrium index of a sequence is an index into the sequence such that the sum of elements at lower indices is equal to the sum of elements at higher indices.

For example, in a sequence *A* :
    A<sub>0</sub> = −7    
    A<sub>1</sub> = 1    
    A<sub>2</sub> = 5    
    A<sub>3</sub> = 2    
    A<sub>4</sub> = −4
    A<sub>5</sub> = 3
    A<sub>6</sub> = 0
 
`3` is an equilibrium index, because:

A<sub>0</sub>+A<sub>1</sub>+A<sub>2</sub> = A<sub>4</sub>+A<sub>5</sub>+A<sub>6</sub>
 
`6` is also an equilibrium index, because:

A<sub>0</sub>+A<sub>1</sub>+A<sub>2</sub>+A<sub>3</sub>+A<sub>4</sub>+A<sub>5</sub>=0
 
(sum of zero elements is zero)

`7` is not an equilibrium index, because it is not a valid index of sequence *A*.

---

Write a function that, given a sequence, returns its equilibrium indices (if any).

Assume that the sequence may be very long.

---

### Tests

1. `equilibrium` should be a function.
2. `equilibrium([-7, 1, 5, 2, -4, 3, 0])` should return `[3,6]`.
3. `equilibrium([2, 4, 6])` should return `[]`.
4. `equilibrium([2, 9, 2])` should return `[1]`.
5. `equilibrium([1, -1, 1, -1, 1, -1, 1])` should `return [0,1,2,3,4,5,6]`.
6. `equilibrium([1])` should return `[0]`.
7. `equilibrium([])` should return `[]`.

### Answer:

```javascript
function equilibrium(arr) {
    const n = arr.length;
    const equilibriumIndices = [];
    let totalSum = 0;
    let leftSum = 0;

    // First calculate the total sum of the array
    for (let i = 0; i < n; i++) {
        totalSum += arr[i];
    }

    // Iterate through the array and check for equilibrium index
    for (let i = 0; i < n; i++) {
        // If leftSum equals the sum on the right side (totalSum - leftSum - arr[i])
        if (leftSum === totalSum - leftSum - arr[i]) {
            equilibriumIndices.push(i);
        }
        leftSum += arr[i];
    }

    return equilibriumIndices;
}

// Test cases:
console.log(equilibrium([-7, 1, 5, 2, -4, 3, 0]));  // Output: [3, 6]
console.log(equilibrium([2, 4, 6]));               // Output: []
console.log(equilibrium([2, 9, 2]));               // Output: [1]
console.log(equilibrium([1, -1, 1, -1, 1, -1, 1])); // Output: [0, 1, 2, 3, 4, 5, 6]
console.log(equilibrium([1]));                     // Output: [0]
console.log(equilibrium([]));                      // Output: []
```