# Interfaces
Interfaces can be used to type check an object. We can use an interface as a type, it allows us to define the structure of an object and the object created must have the same structure as the interface. Interfaces are not compiled.

## syntax
```typescript
interface IEmployee {
    empCode: number;
    empName: string;
    getSalary: (number) => number; // arrow function
    getManagerName(number): string; 
}

interface customFunctionType {
		(num: number): number; 
}
// implementation for the above
let add: customFunctionType;
add = (num: number) => {
return num + 5;
}

type ErrorHandler = (error: IError) => void // type for only one function
// or
interface IErrorHandler {
  ErrorHander: (error: IError) => void
}
    
// IError Interface if interest
interface IError {
  error: string;
  status: number;
  message: string;
}
```

## Interface vs Custom Type
Interface is more clear, however Custom Type is more flexible. You can also implement an interface in a class.


## implements
You can implement multiple interfaces, and it will force you to implement everything found in the interface. This is different from an abstract class because an abstract class can have some implementation, whereas an interface will have none.
syntax
```typescript
interface Task{
    name: String; //property
    run(arg: any):void; //method
}

class MyTask implements Task{
    name: String;
    constructor(name: String) {
        this.name = name;
    }
	run(arg: any): void {
        console.log(`running: ${this.name}, arg: ${arg}`);
    }
}

let myTask: Task = new MyTask('someTask');
myTask.run("test");
```

## extends
Interfaces can extend one another, so they will form a new interface with all of the properties of both. You can extend more than one, which is different than classes.

## Optional Property
You can make a property optional by adding a ?.
syntax
```typescript
interface Task{
    name?: String; //optional property
    run(arg: any):void; //method
}
```

Credit goes to Gone Coding from stack overflow for below.

There are currently three syntaxes that TypeScript allows for function declarations in interfaces:

Using your example of a `validation` function taking 1 parameter (of `any` type) and a `boolean` return value:

```typescript
validation: {(flag: any): boolean};
```

or in the newer syntax:

```typescript
validation(flag: any) : boolean;
```

or an alternative is:

```typescript
validation: (flag: any) => boolean;
```

**Solution:**

so to make it optional with the old syntax is easy:

```typescript
validation?: {(flag: any): boolean};
```

with the second syntax (recent addition - thanks to `@toothbrush`)

```typescript
validation?(flag: any) : boolean;
```

or in the third syntax (as you found):

```typescript
validation?: (flag: any) => boolean;
```
