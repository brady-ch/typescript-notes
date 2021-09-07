# Destructuring
## Array Destructuring
This will iterate through the array and store the corresponding elements of the array into the destructured array. Note that this does not mutate the original array.
```typescript
const numbers = [0, 1, 2, 3];
const [num1, num2, num3, ...nums] = numbers;
```


## Object Destructuring
Values are destructured by key name, you must use the same key to destructure. This is just javascript syntax.
```typescript
const huhkay = {huh: "kay", kay: "huh"};
const {huh: alias, kay} = huhkay;
```