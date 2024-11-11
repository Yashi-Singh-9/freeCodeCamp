# Subleq

### Description

Subleq is an example of a One-Instruction Set Computer (OISC).

It is named after its only instruction, which is SUbtract and Branch if Less than or EQual to zero.

Your task is to create an interpreter which emulates such a machine.

The machine's memory consists of an array of signed integers. Any reasonable word size is fine, but the memory must be able to hold negative as well as positive numbers.

Execution begins with the instruction pointer aimed at the first word, which is address 0. It proceeds as follows:

1. Let A, B, and C be the value stored in the three consecutive words in memory starting at the instruction pointer.
2. Advance the instruction pointer 3 words to point at the address after the one containing C.
3. If A is -1, then a character is read from standard input and its code point stored in the address given by B. C is unused.
4. If B is -1, then the number contained in the address given by A is interpreted as a code point and the corresponding character output. C is again unused.
5. Otherwise, both A and B are treated as the addresses of memory locations. The number contained in the address given by A is subtracted from the number at the address given by B (and the result stored back in address B). If the result is zero or negative, the value C becomes the new instruction pointer.
6. If the instruction pointer becomes negative, execution halts.

Other negative addresses besides -1 may be treated as equivalent to -1, or generate an error, as you see fit.

Your solution should accept a program to execute on the machine, separately from the input fed to the program itself.

This program should be in raw subleq "machine code" - whitespace-separated decimal numbers, with no symbolic names or other assembly-level extensions, to be loaded into memory starting at address 0. Show the output of your solution when fed this "Hello, world!" program. (Note that the example assumes ASCII or a superset of it, such as any of the Latin-N character sets or Unicode. You may translate it into another character set if your implementation is on a non-ASCiI-compatible environment.)

15 17 -1 17 -1 -1 16 1 -1 16 3 -1 15 15 0 0 -1 72 101 108 108 111 44 32 119 111 114 108 100 33 10 0

Which corresponds to something like this in a hypothetical assembler language:

```
start:
    zero, message, -1
    message, -1, -1
    neg1, start+1, -1
    neg1, start+3, -1
    zero, zero, start
zero: 0
neg1: -1
message: "Hello, world!\n\0"
```

---

Write a function that takes an array of integers as a parameter. This represents the memory elements. The function should interpret the sequence and return the output string. For this task, assume that there is no standard input.

### Tests

1. `Subleq` should be a function.
2. `Subleq([15, 17, -1, 17, -1, -1, 16, 1, -1, 16, 3, -1, 15, 15, 0, 0, -1, 72, 101, 108, 108, 111, 44, 32, 119, 111, 114, 108, 100, 33, 0])` should return a string.
3. `Subleq([15, 17, -1, 17, -1, -1, 16, 1, -1, 16, 3, -1, 15, 15, 0, 0, -1, 72, 101, 108, 108, 111, 44, 32, 119, 111, 114, 108, 100, 33, 0])` should return `"Hello, world!"`.

### Solution:

```javascript
function Subleq(memory) {
    let instructionPointer = 0;
    let output = '';
    
    // Helper function to handle the reading of memory at an index.
    function getMemory(address) {
        return memory[address] || 0;
    }

    // Main execution loop.
    while (instructionPointer >= 0 && instructionPointer < memory.length) {
        let A = getMemory(instructionPointer);
        let B = getMemory(instructionPointer + 1);
        let C = getMemory(instructionPointer + 2);
        
        instructionPointer += 3; // Move to the next instruction set.

        // Case 1: A is -1, read character from input (no input in this problem)
        if (A === -1) {
            memory[B] = C; // Store the character's code point in memory[B]
        }
        // Case 2: B is -1, output a character from memory[A]
        else if (B === -1) {
            output += String.fromCharCode(getMemory(A)); // Convert the value at A to a character and append it to output
        }
        // Case 3: General subtract and conditional jump
        else {
            memory[B] -= getMemory(A); // Subtract memory[A] from memory[B]
            if (memory[B] <= 0) {
                instructionPointer = C; // Jump to the address in C if the result is <= 0
            }
        }
    }
    
    return output;
}

// Example usage:
const memory = [
    15, 17, -1, 17, -1, -1, 16, 1, -1, 16, 3, -1,
    15, 15, 0, 0, -1, 72, 101, 108, 108, 111, 44, 32,
    119, 111, 114, 108, 100, 33, 0
];

console.log(Subleq(memory)); // "Hello, world!"
```