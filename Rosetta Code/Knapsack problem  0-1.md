# Knapsack problem/0-1

### Description

The 0-1 knapsack problem is defined as follows:

You are given an array of objects representing items to be put in a knapsack. The objects have 3 attributes: name, weight, and value. The items need to be selected so that the total weight does not exceed the maximum weight and the value is maximized.

Write a function to solve the knapsack problem. The function is given the array of objects and the maximum weight as parameters. It should return the maximum total value possible.

### Tests

1. knapsack([{ name:'map', weight:9, value:150 }, { name:'compass', weight:13, value:35 }, { name:'water', weight:153, value:200 }, { name:'sandwich', weight:50, value:160 }, { name:'glucose', weight:15, value:60 }, { name:'tin', weight:68, value:45 }, { name:'banana', weight:27, value:60 }, { name:'apple', weight:39, value:40 }], 100) should return 405.

2. knapsack([{ name:'map', weight:9, value:150 }, { name:'compass', weight:13, value:35 }, { name:'water', weight:153, value:200 }, { name:'sandwich', weight:50, value:160 }, { name:'glucose', weight:15, value:60 }, { name:'tin', weight:68, value:45 }, { name:'banana', weight:27, value:60 }, { name:'apple', weight:39, value:40 }], 200) should return 510.

3. knapsack([{ name:'cheese', weight:23, value:30 }, { name:'beer', weight:52, value:10 }, { name:'suntan cream', weight:11, value:70 }, { name:'camera', weight:32, value:30 }, { name:'T-shirt', weight:24, value:15 }, { name:'trousers', weight:48, value:10 }, { name:'umbrella', weight:73, value:40 }], 100) should return 145.

4. knapsack([{ name:'cheese', weight:23, value:30 }, { name:'beer', weight:52, value:10 }, { name:'suntan cream', weight:11, value:70 }, { name:'camera', weight:32, value:30 }, { name:'T-shirt', weight:24, value:15 }, { name:'trousers', weight:48, value:10 }, { name:'umbrella', weight:73, value:40 }], 200) should return 185.

5. knapsack([{ name:'waterproof trousers', weight:42, value:70 }, { name:'waterproof overclothes', weight:43, value:75 }, { name:'note-case', weight:22, value:80 }, { name:'sunglasses', weight:7, value:20 }, { name:'towel', weight:18, value:12 }, { name:'socks', weight:4, value:50 }, { name:'book', weight:30, value:10 }], 100) should return 237.

6. knapsack([{ name:'waterproof trousers', weight:42, value:70 }, { name:'waterproof overclothes', weight:43, value:75 }, { name:'note-case', weight:22, value:80 }, { name:'sunglasses', weight:7, value:20 }, { name:'towel', weight:18, value:12 }, { name:'socks', weight:4, value:50 }, { name:'book', weight:30, value:10 }], 200) should return 317.'

### Answer:

```javascript
function knapsack(items, maxWeight) {
    const n = items.length;
    // Create a 2D array to store the maximum value at each n and w
    const dp = Array(n + 1).fill(null).map(() => Array(maxWeight + 1).fill(0));

    // Build the dp array in bottom-up manner
    for (let i = 1; i <= n; i++) {
        for (let w = 0; w <= maxWeight; w++) {
            const item = items[i - 1];
            if (item.weight <= w) {
                // Take the maximum of including the item or not
                dp[i][w] = Math.max(dp[i - 1][w], dp[i - 1][w - item.weight] + item.value);
            } else {
                // Can't include the item
                dp[i][w] = dp[i - 1][w];
            }
        }
    }

    // The maximum value is in the bottom right corner of the array
    return dp[n][maxWeight];
}

// Test cases
console.log(knapsack([
    { name: 'map', weight: 9, value: 150 },
    { name: 'compass', weight: 13, value: 35 },
    { name: 'water', weight: 153, value: 200 },
    { name: 'sandwich', weight: 50, value: 160 },
    { name: 'glucose', weight: 15, value: 60 },
    { name: 'tin', weight: 68, value: 45 },
    { name: 'banana', weight: 27, value: 60 },
    { name: 'apple', weight: 39, value: 40 }
], 100)); // should return 405

console.log(knapsack([
    { name: 'map', weight: 9, value: 150 },
    { name: 'compass', weight: 13, value: 35 },
    { name: 'water', weight: 153, value: 200 },
    { name: 'sandwich', weight: 50, value: 160 },
    { name: 'glucose', weight: 15, value: 60 },
    { name: 'tin', weight: 68, value: 45 },
    { name: 'banana', weight: 27, value: 60 },
    { name: 'apple', weight: 39, value: 40 }
], 200)); // should return 510

console.log(knapsack([
    { name: 'cheese', weight: 23, value: 30 },
    { name: 'beer', weight: 52, value: 10 },
    { name: 'suntan cream', weight: 11, value: 70 },
    { name: 'camera', weight: 32, value: 30 },
    { name: 'T-shirt', weight: 24, value: 15 },
    { name: 'trousers', weight: 48, value: 10 },
    { name: 'umbrella', weight: 73, value: 40 }
], 100)); // should return 145

console.log(knapsack([
    { name: 'cheese', weight: 23, value: 30 },
    { name: 'beer', weight: 52, value: 10 },
    { name: 'suntan cream', weight: 11, value: 70 },
    { name: 'camera', weight: 32, value: 30 },
    { name: 'T-shirt', weight: 24, value: 15 },
    { name: 'trousers', weight: 48, value: 10 },
    { name: 'umbrella', weight: 73, value: 40 }
], 200)); // should return 185

console.log(knapsack([
    { name: 'waterproof trousers', weight: 42, value: 70 },
    { name: 'waterproof overclothes', weight: 43, value: 75 },
    { name: 'note-case', weight: 22, value: 80 },
    { name: 'sunglasses', weight: 7, value: 20 },
    { name: 'towel', weight: 18, value: 12 },
    { name: 'socks', weight: 4, value: 50 },
    { name: 'book', weight: 30, value: 10 }
], 100)); // should return 237

console.log(knapsack([
    { name: 'waterproof trousers', weight: 42, value: 70 },
    { name: 'waterproof overclothes', weight: 43, value: 75 },
    { name: 'note-case', weight: 22, value: 80 },
    { name: 'sunglasses', weight: 7, value: 20 },
    { name: 'towel', weight: 18, value: 12 },
    { name: 'socks', weight: 4, value: 50 },
    { name: 'book', weight: 30, value: 10 }
], 200)); // should return 317
```