# Deepcopy

### Description

Write a function that returns a deep copy of a given object. The copy must not be the same object that was given.

This task will not test for:

- Objects with properties that are functions
- Date objects or object with properties that are Date objects
- RegEx or object with properties that are RegEx objects
- Prototype copying

---

### Tests

1. `deepcopy` should be a function.
2. `deepcopy({test: "test"})` should return an object.
3. `deepcopy` should not return the same object that was provided.
4. When passed an object containing an array, `deepcopy` should return a deep copy of the object.
5. When passed an object containing another object, `deepcopy` should return a deep copy of the object.

### Answer:

```javascript
function deepcopy(obj) {
    // Check if the input is an object or array
    if (obj === null || typeof obj !== 'object') {
        return obj; // Return primitive values as is
    }

    // Create an array or object to hold the copy
    const copy = Array.isArray(obj) ? [] : {};

    // Iterate through the properties of the object
    for (const key in obj) {
        if (obj.hasOwnProperty(key)) {
            // Recursively call deepcopy for nested objects/arrays
            copy[key] = deepcopy(obj[key]);
        }
    }

    return copy; // Return the deep copy
}

// Example usage:
const original = { test: "test", nested: { a: 1, b: [2, 3] } };
const copied = deepcopy(original);

// Test cases
console.log(copied); // Should log the deep copied object
console.log(copied !== original); // Should be true, ensuring a new object is created
console.log(copied.nested !== original.nested); // Should also be true
console.log(copied.nested.b !== original.nested.b); // Should be true, arrays are copied
```