# Types
Type any is default.
Types are checked during compilation, in whereas in Javascript they are only checked during runtime.

## Core Types
| Type | Example |
|---|---|
| [[#string]] | "huhkay", 'huhkay', \`huhkay\`. |
| [[#number]] | 3, 3.14, -3|
| [[#boolean]] | true or false |
| [[#object]] | `{huh: "kay"}` | 
| [[#Array]] | [1, 2, 3] |
| [[#Tuple]]| [type1, type2] |
| [[#Enum]] | `enum { ZERO, ONE }` |
| [[#any]] | * |

## Special Types
| Type | Example |
|---|---|
| [[#Union]] | `huh: type1 | type2` |
| [[#Literal]] | `let huh = 'huh' | 'kay'` |
| [[#Alias/Custom]] | `type Huhkay = number | string` |
| [[#void]] | function specific |
| [[#Function]] | `let huh: (param1: type1, param2: type2) => returnType;` |
| [[#unknown]] | Similar to any, but it is a bit more restrictive |
| [[#never]] | function specific |

## Considerations

### Type Inference
If you declare a const as I have above, it will infer the type and ensure that it is of the same value as what you instantiated it at. 

Examples:
```typescript
// This set the type to the number 5
const huh = 5; // const huh: 5
// This will set the type to number, however it can be any number, the value can change
let kay = 5; // let kay: number
```

### Declaring types
```typescript
// below will assign the type number to the variable huhkay
let huhkay: number;
// number array 
let let huh: number[];
```

### Adding a Type to Function Arguments
```typescript
function huhkay(arg1: number, arg2: number){
console.log("Do stuff");
}

function huhkay(arg1: string, arg2: string){
console.log("Do stuff");
}
```

### Adding a Return Type to a Function
```typescript
// where type1, type2, and returnType are any type
function huhkay(huh: type1, kay: type2): returnType {
doStuff();
return stuff; // Where stuff is of type returnType
}
```

## Definitions

### string
Represents string values like "huhkay", 'huhkay', or `huhkay`. All text values.
```typescript
const huh: string;
```

### number
All numbers, no differentiation between int and float values.
```typescript
const huh: number;
```

### boolean
True or false values, truthy and falsy values do not exist in typescript.
```typescript
const huh: boolean;
```

### object
Any Javascript object, more specific types (type of object) are possible.
Object types in typescript are different than in Javascript, we have key type pairs in Typescript rather than key value pairs.

```typescript
// below will infer the objects type without stating it explicitly
const huhkay = {
huh: 'kay' 
}

// creating typscript representation of an object type
const huhkay: { 
huh: string 
} = {
huh: 'kay' // object values
}
```

### Array
Any Javascript array, type can be flexible or strict (regarding the element types).
```typescript 
const huh: [];
const kay: number[];
```

### Tuple
Array of fixed length. It will enforce types declared in the tuple and be more strictly typed.
```typescript
// creates an array of fixed length, expecting a number and a string
const huh: [number, string];

// Exceptions: this will not throw an error, it is an exception
huh.push("kay");
```

### Enum
Great when you want to make something human readable and they will have some map value.

Enums are a custom type, naming convention starts custom types like enum with an upper case letter. Here we are assigning labels to numbers, this basically allows us to make a list that we can access and check. You can use enums instead of magic numbers, this will make the code more understandable.
```typescript
// declaring an enum
// defaults to HUH = 0, KAY = 1, HUHKAY = 2 ...
enum Huhkay {HUH, KAY, HUHKAY};

// Changing the inital value
// HUH = 7, KAY = 8, HUHKAY = 9 ...
enum Huhkay {HUH = 7, KAY, HUHKAY};

// Custom values
enum Huhkay {HUH = "okay", KAY = 100, HUHKAY = 200}
```

### any 
Special type in Typescript, it will forgo type checking. Basically forgoes the advantages that you get from typescript. This will give you a similar experience to vanilla Javascript. Don't use this unless you have to.

### Union
This allows us to use multiple types. With this you can use runtime type checks, however it is usually best to avoid them.
```typescript
const huh: number | string;
```

### Literal
This is where the value assigned is set to the type. It is a specific version of a type. 
```typescript
// this will only take arguments of value 'huh' or 'kay'
function huhkay(arg: 'huh' | 'kay'){
doSomething();
}
```

### Alias/Custom
This allows us to make custom types and can improve readability. Naming convention start custom types with an upper case.
```typescript
type Huh = number | string;
type Kay = 'huh' | 'kay';
type User = {name: string, age: number}

// Which allows you to do this
const user: User = {name: 'Person', age: 65};
```

### void
The void keyword indicates that there will be no return value. Technically it returns undefined but the function does not require a return statement.
```typescript
function huhkay(arg: someType): void {
doStuff();
}
```

### Function
Function is a type provided by Typescript.
```typescript
// Technically you can do this, but it is better to be more specific
let huh: Function;

// This is generally considered better practice
let huh: (param1: paramType1, param2: paramType2) => returnType;
```

### unknown
Unknown is similar to any, but will have type checking, when it's used, therefore you will need to perform type checking during runtime. This is better than any, but it is best to avoid if possible.
```typscript
let huh: unknown;
let kay: string;

huh = 'kay';
huh = 5; 
if (typeof huh === 'string') { // this check is needed for compilation
kay = huh;
}
```

### never
This is similar to the void type, however this is used when the function will not return even undefined. This is newer than type void, so when a never type will be used typescript may infer a type void.
```typscript
function makeError(message: string, code: number): never {
throw {message: message, errorCode, code}
}
```
The above function will never return anything because it will terminate before returning type undefined.