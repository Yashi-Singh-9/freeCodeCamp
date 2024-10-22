# Gray code

### Description

Gray code is a form of binary encoding where transitions between consecutive numbers differ by only one bit.

This is a useful encoding for reducing hardware data hazards with values that change rapidly and/or connect to slower hardware as inputs.

It is also useful for generating inputs for Karnaugh maps in order from left to right or top to bottom.

---

Create a function to encode a number to and decode a number from Gray code. The function should will have 2 parameters.

The first would be a boolean. The function should encode for true and decode for false. The second parameter would be the number to be encoded/decoded.

Display the normal binary representations, Gray code representations, and decoded Gray code values for all 5-bit binary numbers (0-31 inclusive, leading 0's not necessary).

There are many possible Gray codes. The following encodes what is called "binary reflected Gray code."

Encoding (MSB is bit 0, b is binary, g is Gray code):
```
if b[i-1] = 1
  g[i] = not b[i]
else
  g[i] = b[i]
Or:

g = b xor (b logically right shifted 1 time)
Decoding (MSB is bit 0, b is binary, g is Gray code):

b[0] = g[0]

for other bits:
b[i] = g[i] xor b[i-1]
```

### Tests 

1. `gray` should be a function.
2. `gray(true,177)` should return a number.
3. `gray(true,177)` should return `233`.
4. `gray(true,425)` should return `381`.
5. `gray(true,870)` should return `725`.
6. `gray(false,233)` should return `177`.
7. `gray(false,381)` should return `425`.
8. `gray(false,725)` should return `870`.

### Answer:

```javascript
function gray(encode, num) {
    if (encode) {
        // Encoding from binary to Gray code
        return num ^ (num >> 1);
    } else {
        // Decoding from Gray code to binary
        let binary = num;
        let mask = num >> 1;
        while (mask > 0) {
            binary ^= mask;
            mask >>= 1;
        }
        return binary;
    }
}

// Test for all 5-bit binary numbers (0-31 inclusive)
console.log("Binary -> Gray Code -> Decoded Gray Code:");
for (let i = 0; i < 32; i++) {
    let encoded = gray(true, i);
    let decoded = gray(false, encoded);
    console.log(`Binary: ${i.toString(2).padStart(5, '0')}, Gray: ${encoded.toString(2).padStart(5, '0')}, Decoded: ${decoded}`);
}

// Test cases for specific numbers
console.log("\nTest cases:");
console.log(gray(true, 177)); // Expected: 233
console.log(gray(true, 425)); // Expected: 381
console.log(gray(true, 870)); // Expected: 725
console.log(gray(false, 233)); // Expected: 177
console.log(gray(false, 381)); // Expected: 425
console.log(gray(false, 725)); // Expected: 870
```