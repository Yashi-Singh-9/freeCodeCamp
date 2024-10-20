# Execute Brain****

### Description

Write a function to implement a Brain**** interpreter. The function will take a string as a parameter and should return a string as the output. More details are given below:

RCBF is a set of [Brainf***](https://rosettacode.org/wiki/Category:Brainf***) compilers and interpreters written for Rosetta Code in a variety of languages.

Below are links to each of the versions of RCBF.

An implementation need only properly implement the following instructions:

Command	Description
```
>	Move the pointer to the right
<	Move the pointer to the left
+	Increment the memory cell under the pointer
-	Decrement the memory cell under the pointer
.	Output the character signified by the cell at the pointer
,	Input a character and store it in the cell at the pointer
[	Jump past the matching ] if the cell under the pointer is 0
]	Jump back to the matching [ if the cell under the pointer is nonzero
```

Any cell size is allowed, EOF (End-O-File) support is optional, as is whether you have bounded or unbounded memory.

### Tests

1. `brain(hello)` should return a string
2. `brain("++++++[>++++++++++<-]>+++++.")` should return "A"
3. `brain(hello)` should return `Hello World!\n`
4. `brain(fib)` should return `1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89`

### Answer:

```javascript
function brainfuckInterpreter(code, inputString = "") {
    let memory = Array(30000).fill(0);  // Initialize memory with 30,000 cells
    let pointer = 0;  // Memory pointer
    let inputPointer = 0;  // Input string pointer
    let output = [];  // To store output characters
    let codePointer = 0;  // Code pointer
    let loopStack = [];  // Stack to handle loops
    
    while (codePointer < code.length) {
        let command = code[codePointer];
        
        switch (command) {
            case '>':
                pointer++;
                if (pointer >= memory.length) {
                    memory.push(0);  // Expand memory if necessary
                }
                break;
            case '<':
                pointer--;
                if (pointer < 0) {
                    throw new Error("Pointer moved to negative position");
                }
                break;
            case '+':
                memory[pointer] = (memory[pointer] + 1) % 256;  // Increment and wrap around at 256
                break;
            case '-':
                memory[pointer] = (memory[pointer] - 1 + 256) % 256;  // Decrement and wrap around at 0
                break;
            case '.':
                output.push(String.fromCharCode(memory[pointer]));  // Output the character
                break;
            case ',':
                if (inputPointer < inputString.length) {
                    memory[pointer] = inputString.charCodeAt(inputPointer);  // Store the input character
                    inputPointer++;
                } else {
                    memory[pointer] = 0;  // EOF case
                }
                break;
            case '[':
                if (memory[pointer] === 0) {
                    // Jump to the matching ']'
                    let openBrackets = 1;
                    while (openBrackets > 0) {
                        codePointer++;
                        if (code[codePointer] === '[') openBrackets++;
                        if (code[codePointer] === ']') openBrackets--;
                    }
                } else {
                    loopStack.push(codePointer);  // Remember the position
                }
                break;
            case ']':
                if (memory[pointer] !== 0) {
                    codePointer = loopStack[loopStack.length - 1];  // Jump back to the matching '['
                } else {
                    loopStack.pop();  // Exit the loop
                }
                break;
            default:
                // Ignore any other characters (comments, etc.)
                break;
        }
        
        codePointer++;
    }
    
    return output.join('');  // Return the final output as a string
}

// Function to interpret and run Brain**** code
function brain(code) {
    return brainfuckInterpreter(code);
}

// Example test cases
console.log(brain("++++++[>++++++++++<-]>+++++."));  // Should print 'A'

// Add more tests as needed
```