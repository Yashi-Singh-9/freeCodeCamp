# Symmetric difference

### Description

Given two sets A and B, compute $(A \setminus B) \cup (B \setminus A).$ That is, enumerate the items that are in A or B but not both. This set is called the symmetric difference of A and B. In other words: $(A \cup B) \setminus (A \cap B)$ (the set of items that are in at least one of A or B minus the set of items that are in both A and B).

Example:

For sets `A = [1, 2, 3]`, and `B = [1, 3, 4]`, the symmetric difference of A and B is `[2, 4]`.

---

Write a function that takes two arrays as parameters and returns the symmetric difference. Sort the resultant array before returning it.

### Tests

1. `symmetricDifference` should be a function.
2. `symmetricDifference(["John", "Bob", "Mary", "Serena"], ["Jim", "Mary", "John", "Bob"])` should return an array.
3. `symmetricDifference(["John", "Bob", "Mary", "Serena"], ["Jim", "Mary", "John", "Bob"])` should return `["Jim", "Serena"]`.
4. `symmetricDifference([1, 2, 3], [3, 4])` should return `[1, 2, 4]`.
5. `symmetricDifference([1, 2, 3, 4, 5], [3, 4, 8, 7])` should return `[1, 2, 5, 7, 8]`.
6. `symmetricDifference([1, 2, 3, 4, 5, 6, 7, 8], [1, 3, 5, 6, 7, 8, 9])` should return `[2, 4, 9]`.
7. `symmetricDifference([1, 2, 4, 7, 9], [2, 3, 7, 8, 9])` should return `[1, 3, 4, 8]`.

### Solution

```javascript
function symmetricDifference(arr1, arr2) {
    // Convert arrays to sets
    const set1 = new Set(arr1);
    const set2 = new Set(arr2);

    // Get the symmetric difference
    const result = [
        ...arr1.filter(item => !set2.has(item)),
        ...arr2.filter(item => !set1.has(item))
    ];

    // Sort the result array and return it
    return result.sort();
}
```