# ABC Problem

### Description

You are given a collection of ABC blocks (e.g., childhood alphabet blocks). There are 20 blocks with two letters on each block. A complete alphabet is guaranteed amongst all sides of the blocks. The sample collection of blocks:
```
(B O)
(X K)
(D Q)
(C P)
(N A)
(G T)
(R E)
(T G)
(Q D)
(F S)
(J W)
(H U)
(V I)
(A N)
(O B)
(E R)
(F S)
(L Y)
(P C)
(Z M)
```

---
Implement a function that takes a string (word) and determines whether the word can be spelled with the given collection of blocks.

Some rules to keep in mind:

- Once a letter on a block is used, that block cannot be used again.
- The function should be case-insensitive.

### Tests 

1. `canMakeWord` should be a function.
2. `canMakeWord` should return a boolean.
3. `canMakeWord("bark")` should return true.
4. `canMakeWord("BooK")` should return false.
5. `canMakeWord("TReAT")` should return true.
6. `canMakeWord("COMMON")` should return false.
7. `canMakeWord("squAD")` should return true.
8. `canMakeWord("conFUSE")` should return true.

### Answer:

```javascript
function canMakeWord(word) {
  // Define the blocks as pairs of letters
  const blocks = [
    ['B', 'O'], ['X', 'K'], ['D', 'Q'], ['C', 'P'], ['N', 'A'],
    ['G', 'T'], ['R', 'E'], ['T', 'G'], ['Q', 'D'], ['F', 'S'],
    ['J', 'W'], ['H', 'U'], ['V', 'I'], ['A', 'N'], ['O', 'B'],
    ['E', 'R'], ['F', 'S'], ['L', 'Y'], ['P', 'C'], ['Z', 'M']
  ];

  // Convert word to uppercase for case-insensitivity
  const upperWord = word.toUpperCase();

  // Array to track which blocks have been used
  const usedBlocks = Array(blocks.length).fill(false);

  // Iterate over each letter in the word
  for (const letter of upperWord) {
    let letterFound = false;

    // Check each block to see if it contains the letter and hasn't been used
    for (let i = 0; i < blocks.length; i++) {
      if (!usedBlocks[i] && (blocks[i][0] === letter || blocks[i][1] === letter)) {
        usedBlocks[i] = true; // Mark the block as used
        letterFound = true;
        break; // Stop searching after finding a block
      }
    }

    // If no suitable block is found for the letter, return false
    if (!letterFound) {
      return false;
    }
  }

  // If all letters can be matched with blocks, return true
  return true;
}

// Test cases
console.log(canMakeWord("bark"));     // true
console.log(canMakeWord("BooK"));     // false
console.log(canMakeWord("TReAT"));    // true
console.log(canMakeWord("COMMON"));   // false
console.log(canMakeWord("squAD"));    // true
console.log(canMakeWord("conFUSE"));  // true

```