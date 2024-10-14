# 100 doors

### Problem Statement:

There are 100 doors in a row that are all initially closed. You make 100 passes by the doors. The first time through, visit every door and 'toggle' the door (if the door is closed, open it; if it is open, close it). The second time, only visit every 2nd door (i.e., door #2, #4, #6, ...) and toggle it. The third time, visit every 3rd door (i.e., door #3, #6, #9, ...), etc., until you only visit the 100th door.

---

Implement a function to determine the state of the doors after the last pass. Return the final result in an array, with only the door number included in the array if it is open.

### Tests:

1. `getFinalOpenedDoors` should be a function.
2. `getFinalOpenedDoors` should return an array.
3. `getFinalOpenedDoors` should produce the correct result.

### Answers: 

```javascript
function getFinalOpenedDoors(numDoors) {
    // Initialize an array to represent the doors, all initially closed (false)
    const doors = new Array(numDoors).fill(false);
    
    // Loop through each pass from 1 to numDoors
    for (let pass = 1; pass <= numDoors; pass++) {
        // Toggle every pass-th door
        for (let door = pass - 1; door < numDoors; door += pass) {
            doors[door] = !doors[door]; // Toggle the door
        }
    }
    
    // Collect the indices of the doors that are open (true)
    const openedDoors = [];
    for (let i = 0; i < numDoors; i++) {
        if (doors[i]) {
            openedDoors.push(i + 1); // Convert from 0-based index to 1-based
        }
    }
    
    return openedDoors;
}

// Example usage:
const finalOpenedDoors = getFinalOpenedDoors(100);
console.log(finalOpenedDoors);
```