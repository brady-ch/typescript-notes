# Type Casting
Type casting allows you to treat something as a certain type, assuming you will know what it will be.You can type cast in Typescript using two different methods:

```typescript
userInputElement = <HTMLInputElement>document.getElementById('user-input');
userInputElement = document.getElementById('user-input')! as HTMLInputElement;
```