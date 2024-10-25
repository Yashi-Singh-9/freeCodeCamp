# Knapsack problem/Continuous

### Description

A thief burgles a butcher's shop, where he can select from some items.

The thief knows the weights and prices of each items. Because he has a knapsack with a limit on the maximum weight that it can carry, he wants to select the items such that he would have his profit maximized. He may cut the items; the item has a reduced price after cutting that is proportional to the original price by the ratio of masses. That means: half of an item has half the price of the original.

---

Write a function that takes an array of objects representing the items available in the shop. Each object has 3 attributes: name, weight, and value. The function also takes the maximum weight as a parameter. The function should return the maximum value possible, and the total weight of the selected items should not exceed the maximum weight.

### Tests

1. `knapContinuous([{ "weight":3.8, "value":36, name:"beef" }, { "weight":5.4, "value":43, name:"pork" }, { "weight":3.6, "value":90, name:"ham" }, { "weight":2.4, "value":45, name:"greaves" }, { "weight":4.0, "value":30, name:"flitch" }, { "weight":2.5, "value":56, name:"brawn" }, { "weight":3.7, "value":67, name:"welt" }, { "weight":3.0, "value":95, name:"salami" }, { "weight":5.9, "value":98, name:"sausage" }], 10)` should return `257.875`.

2. `knapContinuous([{ "weight":3.8, "value":36, name:"beef" }, { "weight":5.4, "value":43, name:"pork" }, { "weight":3.6, "value":90, name:"ham" }, { "weight":2.4, "value":45, name:"greaves" }, { "weight":4.0, "value":30, name:"flitch" }, { "weight":2.5, "value":56, name:"brawn" }, { "weight":3.7, "value":67, name:"welt" }, { "weight":3.0, "value":95, name:"salami" }, { "weight":5.9, "value":98, name:"sausage" }], 12)` should return `295.05405405405406`.

3. `knapContinuous([{ "weight":3.8, "value":36, name:"beef" }, { "weight":5.4, "value":43, name:"pork" }, { "weight":3.6, "value":90, name:"ham" }, { "weight":2.4, "value":45, name:"greaves" }, { "weight":4.0, "value":30, name:"flitch" }, { "weight":2.5, "value":56, name:"brawn" }, { "weight":3.7, "value":67, name:"welt" }, { "weight":3.0, "value":95, name:"salami" }, { "weight":5.9, "value":98, name:"sausage" }], 15)` should return `349.3783783783784`.

4. `knapContinuous([{ "weight":3.8, "value":36, name:"beef" }, { "weight":5.4, "value":43, name:"pork" }, { "weight":3.6, "value":90, name:"ham" }, { "weight":2.4, "value":45, name:"greaves" }, { "weight":4.0, "value":30, name:"flitch" }, { "weight":2.5, "value":56, name:"brawn" }, { "weight":3.7, "value":67, name:"welt" }, { "weight":3.0, "value":95, name:"salami" }, { "weight":5.9, "value":98, name:"sausage" }], 22)` should return `459.5263157894737`.

5. `knapContinuous([{ "weight":3.8, "value":36, name:"beef" }, { "weight":5.4, "value":43, name:"pork" }, { "weight":3.6, "value":90, name:"ham" }, { "weight":2.4, "value":45, name:"greaves" }, { "weight":4.0, "value":30, name:"flitch" }, { "weight":2.5, "value":56, name:"brawn" }, { "weight":3.7, "value":67, name:"welt" }, { "weight":3.0, "value":95, name:"salami" }, { "weight":5.9, "value":98, name:"sausage" }], 24)` should return `478.4736842105263`.

### Answer:

```javascript
function knapContinuous(items, maxWeight) {
    // Calculate the value-to-weight ratio and store it with the item
    const itemsWithRatio = items.map(item => ({
        ...item,
        ratio: item.value / item.weight
    }));

    // Sort the items by value-to-weight ratio in descending order
    itemsWithRatio.sort((a, b) => b.ratio - a.ratio);

    let totalValue = 0;
    let remainingWeight = maxWeight;

    for (const item of itemsWithRatio) {
        if (remainingWeight <= 0) {
            break; // Stop if we reach the max weight
        }

        if (item.weight <= remainingWeight) {
            // Take the whole item
            totalValue += item.value;
            remainingWeight -= item.weight;
        } else {
            // Take the fractional part of the item
            totalValue += item.ratio * remainingWeight; // value proportional to the weight taken
            remainingWeight = 0; // Knapsack is full
        }
    }

    return totalValue; // Return the maximum value
}

// Test cases
console.log(knapContinuous([
    { weight: 3.8, value: 36, name: "beef" },
    { weight: 5.4, value: 43, name: "pork" },
    { weight: 3.6, value: 90, name: "ham" },
    { weight: 2.4, value: 45, name: "greaves" },
    { weight: 4.0, value: 30, name: "flitch" },
    { weight: 2.5, value: 56, name: "brawn" },
    { weight: 3.7, value: 67, name: "welt" },
    { weight: 3.0, value: 95, name: "salami" },
    { weight: 5.9, value: 98, name: "sausage" }
], 10)); // Should return 257.875

console.log(knapContinuous([
    { weight: 3.8, value: 36, name: "beef" },
    { weight: 5.4, value: 43, name: "pork" },
    { weight: 3.6, value: 90, name: "ham" },
    { weight: 2.4, value: 45, name: "greaves" },
    { weight: 4.0, value: 30, name: "flitch" },
    { weight: 2.5, value: 56, name: "brawn" },
    { weight: 3.7, value: 67, name: "welt" },
    { weight: 3.0, value: 95, name: "salami" },
    { weight: 5.9, value: 98, name: "sausage" }
], 12)); // Should return 295.05405405405406

console.log(knapContinuous([
    { weight: 3.8, value: 36, name: "beef" },
    { weight: 5.4, value: 43, name: "pork" },
    { weight: 3.6, value: 90, name: "ham" },
    { weight: 2.4, value: 45, name: "greaves" },
    { weight: 4.0, value: 30, name: "flitch" },
    { weight: 2.5, value: 56, name: "brawn" },
    { weight: 3.7, value: 67, name: "welt" },
    { weight: 3.0, value: 95, name: "salami" },
    { weight: 5.9, value: 98, name: "sausage" }
], 15)); // Should return 349.3783783783784

console.log(knapContinuous([
    { weight: 3.8, value: 36, name: "beef" },
    { weight: 5.4, value: 43, name: "pork" },
    { weight: 3.6, value: 90, name: "ham" },
    { weight: 2.4, value: 45, name: "greaves" },
    { weight: 4.0, value: 30, name: "flitch" },
    { weight: 2.5, value: 56, name: "brawn" },
    { weight: 3.7, value: 67, name: "welt" },
    { weight: 3.0, value: 95, name: "salami" },
    { weight: 5.9, value: 98, name: "sausage" }
], 22)); // Should return 459.5263157894737

console.log(knapContinuous([
    { weight: 3.8, value: 36, name: "beef" },
    { weight: 5.4, value: 43, name: "pork" },
    { weight: 3.6, value: 90, name: "ham" },
    { weight: 2.4, value: 45, name: "greaves" },
    { weight: 4.0, value: 30, name: "flitch" },
    { weight: 2.5, value: 56, name: "brawn" },
    { weight: 3.7, value: 67, name: "welt" },
    { weight: 3.0, value: 95, name: "salami" },
    { weight: 5.9, value: 98, name: "sausage" }
], 24)); // Should return 478.4736842105263
```