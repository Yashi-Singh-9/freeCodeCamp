# Longest common subsequence

### Description

The **longest common subsequence** (or **LCS**) of groups A and B is the longest group of elements from A and B that are common between the two groups and in the same order in each group. For example, the sequences `1234` and `1224533324` have an LCS of `1234`:

1234

1224533324

For a string example, consider the sequences `thisisatest` and `testing123testing`. An LCS would be `tsitest`:

thisisatest

testing123testing.

Your code only needs to deal with strings.

---

Write a case-sensitive function that returns the LCS of two strings. You don't need to show multiple LCS's.

### Tests

1. `lcs` should be a function.
2. `lcs("thisisatest", "testing123testing")` should return a string.
3. `lcs("thisisatest", "testing123testing")` should return `"tsitest"`.
4. `lcs("ABCDGH", "AEDFHR")` should return `"ADH"`.
5. `lcs("AGGTAB", "GXTXAYB")` should return `"GTAB"`.
6. `lcs("BDACDB", "BDCB")` should return `"BDCB"`.
7. `lcs("ABAZDC", "BACBAD")` should return `"ABAD"`.

### Solution:

```javascript
function lcs(str1, str2) {
    // Create a 2D array (table) to store lengths of LCS for each substring
    const dp = Array(str1.length + 1).fill(null).map(() => Array(str2.length + 1).fill(0));
    
    // Build the dp array from the bottom-up
    for (let i = 1; i <= str1.length; i++) {
        for (let j = 1; j <= str2.length; j++) {
            if (str1[i - 1] === str2[j - 1]) {
                dp[i][j] = dp[i - 1][j - 1] + 1;
            } else {
                dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
            }
        }
    }

    // Backtrack to find the LCS
    let lcs = "";
    let i = str1.length;
    let j = str2.length;
    while (i > 0 && j > 0) {
        if (str1[i - 1] === str2[j - 1]) {
            lcs = str1[i - 1] + lcs;
            i--;
            j--;
        } else if (dp[i - 1][j] > dp[i][j - 1]) {
            i--;
        } else {
            j--;
        }
    }

    return lcs;
}
```