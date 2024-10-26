# Levenshtein distance

### Descrption

In information theory and computer science, the Levenshtein distance is a metric for measuring the amount of difference between two sequences (i.e. an edit distance). The Levenshtein distance between two strings is defined as the minimum number of edits needed to transform one string into the other, with the allowable edit operations being insertion, deletion, or substitution of a single character.

Example:

The Levenshtein distance between "`kitten`" and "`sitting`" is 3, since the following three edits change one into the other, and there isn't a way to do it with fewer than three edits:

- kitten   sitten    (substitution of 'k' with 's')
- sitten   sittin    (substitution of 'e' with 'i')
- sittin   sitting    (insert 'g' at the end).

The Levenshtein distance between "`rosettacode`", "`raisethysword`" is **8**.

The distance between two strings is same as that when both strings are reversed.

---

Write a function that returns the Levenshtein distance between two strings given as parameters.

### Tests

1. `levenshtein` should be a function.
2. `levenshtein("mist", "dist")` should return a number.
3. `levenshtein("mist", "dist")` should return `1`.
4. `levenshtein("tier", "tor")` should return `2`.
5. `levenshtein("kitten", "sitting")` should return `3`.
6. `levenshtein("stop", "tops")` should return `2`.
7. `levenshtein("rosettacode", "raisethysword")` should return `8`.
8. `levenshtein("mississippi", "swiss miss")` should return `8`.

### Answer:

```javascript
function levenshtein(str1, str2) {
    // Create a 2D array to store distances
    const dp = Array.from({ length: str1.length + 1 }, () => Array(str2.length + 1).fill(0));

    // Initialize the first row and column
    for (let i = 0; i <= str1.length; i++) {
        dp[i][0] = i; // Cost of deletions
    }
    for (let j = 0; j <= str2.length; j++) {
        dp[0][j] = j; // Cost of insertions
    }

    // Fill in the dp array
    for (let i = 1; i <= str1.length; i++) {
        for (let j = 1; j <= str2.length; j++) {
            const cost = str1[i - 1] === str2[j - 1] ? 0 : 1; // 0 if characters are the same, else 1
            dp[i][j] = Math.min(
                dp[i - 1][j] + 1,   // Deletion
                dp[i][j - 1] + 1,   // Insertion
                dp[i - 1][j - 1] + cost // Substitution
            );
        }
    }

    // The Levenshtein distance is in the bottom-right cell
    return dp[str1.length][str2.length];
}

// Test cases
console.log(levenshtein("mist", "dist")); // Should return 1
console.log(levenshtein("tier", "tor")); // Should return 2
console.log(levenshtein("kitten", "sitting")); // Should return 3
console.log(levenshtein("stop", "tops")); // Should return 2
console.log(levenshtein("rosettacode", "raisethysword")); // Should return 8
console.log(levenshtein("mississippi", "swiss miss")); // Should return 8
