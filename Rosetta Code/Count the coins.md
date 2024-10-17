# Count the coins

There are four types of common coins in US currency:

- quarters (25 cents)
- dimes (10 cents)
- nickels (5 cents), and
- pennies (1 cent)

There are six ways to make change for 15 cents:

- A dime and a nickel
- A dime and 5 pennies
- 3 nickels
- 2 nickels and 5 pennies
- A nickel and 10 pennies
- 15 pennies

---

Implement a function to determine how many ways there are to make change for a given input, `cents`, that represents an amount of US pennies using these common coins.

---

### Tests

1. `countCoins` should be a function.
2. `countCoins(15)` should return `6`.
3. `countCoins(85)` should return `163`.
4. `countCoins(100)` should return `242`.

### Answer:
```javascript
function countCoins(cents) {
    // Define the types of coins in cents
    const coins = [25, 10, 5, 1];

    // Memoization cache to store the results for subproblems
    const memo = {};

    // Helper function to count ways to make change
    function countWays(amount, index) {
        // Base case: when amount is zero, there is one way to make change (using no coins)
        if (amount === 0) return 1;
        // Base case: if amount is less than zero, there is no valid way to make change
        if (amount < 0) return 0;
        // Base case: if no more coins are available but amount is still > 0
        if (index >= coins.length) return 0;

        // Check if the result is already computed and stored in memo
        const key = `${amount}-${index}`;
        if (memo[key] !== undefined) return memo[key];

        // Recursive case: count ways with and without the current coin
        const waysWithCoin = countWays(amount - coins[index], index);
        const waysWithoutCoin = countWays(amount, index + 1);

        // Store the result in memo and return the sum
        memo[key] = waysWithCoin + waysWithoutCoin;
        return memo[key];
    }

    // Start the recursion with the full amount and starting from the first coin type
    return countWays(cents, 0);
}

// Test cases
console.log(countCoins(15)); // Output should be 6
console.log(countCoins(85)); // Output should be 163
console.log(countCoins(100)); // Output should be 242
```