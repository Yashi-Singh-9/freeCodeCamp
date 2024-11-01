# Search a list of records

### Description

A record consists of attributes that describe an entity. Each attribute has a name and a value. For example, a person can have an attribute `age` with a value of 25. An important operation on a list of records is to find a record with a particular attribute value.

---

Write a function that takes a string as a parameter. The function should return the index of the item in `list` for which the value of the `name` attribute matches the given string.

### Tests

1. `searchCity` should be a function.
2. `searchCity("Dar Es Salaam")` should return a number.
3. `searchCity("Dar Es Salaam")` should return `6`.
4. `searchCity("Casablanca")` should return `9`.
5. `searchCity("Cairo")` should return `1`.
6. `searchCity("Mogadishu")` should return `4`.
7. `searchCity("Lagos")` should return `0`.

### Solution

```javascript
// Sample list of records
const cities = [
    { name: "Lagos", population: 14500000 },
    { name: "Cairo", population: 20000000 },
    { name: "Nairobi", population: 4700000 },
    { name: "Addis Ababa", population: 4000000 },
    { name: "Mogadishu", population: 2000000 },
    { name: "Khartoum", population: 5000000 },
    { name: "Dar Es Salaam", population: 7000000 },
    { name: "Kinshasa", population: 14000000 },
    { name: "Abuja", population: 3000000 },
    { name: "Casablanca", population: 3200000 }
];

// Function to search for a city by name
function searchCity(cityName) {
    // Iterate through the cities array
    for (let i = 0; i < cities.length; i++) {
        // Check if the name matches the given city name
        if (cities[i].name === cityName) {
            return i; // Return the index if found
        }
    }
    return -1; // Return -1 if not found
}

// Example usage:
console.log(searchCity("Dar Es Salaam")); // should return 6
console.log(searchCity("Casablanca")); // should return 9
console.log(searchCity("Cairo")); // should return 1
console.log(searchCity("Mogadishu")); // should return 4
console.log(searchCity("Lagos")); // should return 0
```