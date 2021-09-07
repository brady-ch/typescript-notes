# Rest Parameters
Allows you to accept a comma separated list of parameters, which will then be converted to an array and you can handle it within the function.

syntax 
```typescript
const huh = (...kay: number[]) => {
kay.reduce((acc, cur) => {
return acc + cur;
}, 0);
}
```