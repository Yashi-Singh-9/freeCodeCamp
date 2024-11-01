# Loop over multiple arrays simultaneously

### Description

Loop over multiple arrays and create a new array whose $i^{th}$ element is the concatenation of $i^{th}$ element of each of the given.

For this example, if you are given this array of arrays:
```
[ ["a", "b", "c"], ["A", "B", "C"], [1, 2, 3] ]
```

the output should be:

```
["aA1","bB2","cC3"]
```

---

Write a function that takes an array of arrays as a parameter and returns an array of strings satisfying the given description.

### Tests

1. `loopSimult` should be a function.
2. `loopSimult([["a", "b", "c"], ["A", "B", "C"], [1, 2, 3]])` should return a array.
3. `loopSimult([["a", "b", "c"], ["A", "B", "C"], [1, 2, 3]])` should return `["aA1", "bB2", "cC3"]`.
4. `loopSimult([["c", "b", "c"], ["4", "5", "C"], [7, 7, 3]])` should return `["c47", "b57", "cC3"]`.
5. `loopSimult([["a", "b", "c", "d"], ["A", "B", "C", "d"], [1, 2, 3, 4]])` should return `["aA1", "bB2", "cC3", "dd4"]`.
6. `loopSimult([["a", "b"], ["A", "B"], [1, 2]])` should return `["aA1", "bB2"]`.
7. `loopSimult([["b", "c"], ["B", "C"], [2, 3]])` should return `["bB2", "cC3"]`.

### Solution:

```javascript
function loopSimult(arrays) {
    // Use map with spread operator to iterate over elements at the same index in each sub-array
    return arrays[0].map((_, i) => arrays.map(array => array[i]).join(''));
}
```