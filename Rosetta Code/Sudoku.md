# Sudoku

### Description

Write a function to solve a partially filled-in normal 9x9 Sudoku grid and return the result. The blank fields are represented by `-1`.

### Tests

1. `solveSudoku` should be a function.
2. `solveSudoku([[8, 1, 9, -1, -1, 5, -1, -1, -1],[-1, -1, 2, -1, -1, -1, 7, 5, -1],[-1, 3, 7, 1, -1, 4, -1, 6, -1],[4, -1, -1, 5, 9, -1, 1, -1, -1],[7, -1, -1, 3, -1, 8, -1, -1, 2],[-1, -1, 3, -1, 6, 2, -1, -1, 7],[-1, 5, -1, 7, -1, 9, 2, 1, -1],[-1, 6, 4, -1, -1, -1, 9, -1, -1],[-1, -1, -1, 2, -1, -1, 4, 3, 8]])` should return an array.
3. `solveSudoku([[8, 1, 9, -1, -1, 5, -1, -1, -1],[-1, -1, 2, -1, -1, -1, 7, 5, -1],[-1, 3, 7, 1, -1, 4, -1, 6, -1],[4, -1, -1, 5, 9, -1, 1, -1, -1],[7, -1, -1, 3, -1, 8, -1, -1, 2],[-1, -1, 3, -1, 6, 2, -1, -1, 7],[-1, 5, -1, 7, -1, 9, 2, 1, -1],[-1, 6, 4, -1, -1, -1, 9, -1, -1],[-1, -1, -1, 2, -1, -1, 4, 3, 8]])` should return `[[8, 1, 9, 6, 7, 5, 3, 2, 4],[6, 4, 2, 9, 8, 3, 7, 5, 1],[5, 3, 7, 1, 2, 4, 8, 6, 9],[4, 2, 6, 5, 9, 7, 1, 8, 3],[7, 9, 5, 3, 1, 8, 6, 4, 2],[1, 8, 3, 4, 6, 2, 5, 9, 7],[3, 5, 8, 7, 4, 9, 2, 1, 6],[2, 6, 4, 8, 3, 1, 9, 7, 5],[9, 7, 1, 2, 5, 6, 4, 3, 8]].`
4. `solveSudoku([[5, 3, -1, -1, 2, 4, 7, -1, -1],[-1, -1, 2, -1, -1, -1, 8, -1, -1],[1, -1, -1, 7, -1, 3, 9, -1, 2],[-1, -1, 8, -1, 7, 2, -1, 4, 9],[-1, 2, -1, 9, 8, -1, -1, 7, -1],[7, 9, -1, -1, -1, -1, -1, 8, -1],[-1, -1, -1, -1, 3, -1, 5, -1, 6],[9, 6, -1, -1, 1, -1, 3, -1, -1],[-1, 5, -1, 6, 9, -1, -1, 1, -1]])` should return `[[5, 3, 9, 8, 2, 4, 7, 6, 1],[6, 7, 2, 1, 5, 9, 8, 3, 4],[1, 8, 4, 7, 6, 3, 9, 5, 2],[3, 1, 8, 5, 7, 2, 6, 4, 9],[4, 2, 5, 9, 8, 6, 1, 7, 3],[7, 9, 6, 3, 4, 1, 2, 8, 5],[8, 4, 1, 2, 3, 7, 5, 9, 6],[9, 6, 7, 4, 1, 5, 3, 2, 8],[2, 5, 3, 6, 9, 8, 4, 1, 7]]`.
5. `solveSudoku([[-1, -1, 3, -1, 2, -1, 6, -1, -1],[9, -1, -1, 3, -1, 5, -1, -1, 1],[-1, -1, 1, 8, -1, 6, 4, -1, -1],[-1, -1, 8, 1, -1, 2, 9, -1, -1],[7, -1, -1, -1, -1, -1, -1, -1, 8],[-1, -1, 6, 7, -1, 8, 2, -1, -1],[-1, -1, 2, 6, -1, 9, 5, -1, -1],[8, -1, -1, 2, -1, 3, -1, -1, 9],[-1, -1, 5, -1, 1, -1, 3, -1, -1]])` should return `[[4, 8, 3, 9, 2, 1, 6, 5, 7],[9, 6, 7, 3, 4, 5, 8, 2, 1],[2, 5, 1, 8, 7, 6, 4, 9, 3],[5, 4, 8, 1, 3, 2, 9, 7, 6],[7, 2, 9, 5, 6, 4, 1, 3, 8],[1, 3, 6, 7, 9, 8, 2, 4, 5],[3, 7, 2, 6, 8, 9, 5, 1, 4],[8, 1, 4, 2, 5, 3, 7, 6, 9],[6, 9, 5, 4, 1, 7, 3, 8, 2]]`.

### Solution: 

```javascript
function solveSudoku(board) {
    function isValid(board, row, col, num) {
        // Check if the number exists in the row
        for (let i = 0; i < 9; i++) {
            if (board[row][i] === num) return false;
        }

        // Check if the number exists in the column
        for (let i = 0; i < 9; i++) {
            if (board[i][col] === num) return false;
        }

        // Check if the number exists in the 3x3 sub-grid
        const startRow = Math.floor(row / 3) * 3;
        const startCol = Math.floor(col / 3) * 3;
        for (let i = startRow; i < startRow + 3; i++) {
            for (let j = startCol; j < startCol + 3; j++) {
                if (board[i][j] === num) return false;
            }
        }

        return true;
    }

    function solve(board) {
        for (let row = 0; row < 9; row++) {
            for (let col = 0; col < 9; col++) {
                if (board[row][col] === -1) { // If the cell is empty
                    for (let num = 1; num <= 9; num++) { // Try numbers 1 to 9
                        if (isValid(board, row, col, num)) {
                            board[row][col] = num; // Place the number
                            if (solve(board)) { // Recursively solve the rest of the board
                                return true;
                            }
                            board[row][col] = -1; // Backtrack if not valid
                        }
                    }
                    return false; // If no valid number is found, return false
                }
            }
        }
        return true; // If no empty cells remain, the puzzle is solved
    }

    solve(board); // Call the solve function to fill the board
    return board; // Return the solved board
}
```