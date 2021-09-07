# Generics
The idea behind generics are that they are a reusable component that will work with a number of different data types. Arrays are an example of an inbuilt generic type in Javascript.

## Syntax
```typescript
function merge<T, U>(objA: T, objB: U) {
 return Object.assign(abjA, objB);
}

const mergedObj = merge({name: 'huh'}, {age: 30});
// You can do what is shown below, but you don't need to because typescript infers the types
const anotherObj = merge<string, number>({{name: 'huh'}, {age: 30}})

function firstElement<Type>(arr: Type[]): Type {
  return arr[0];
}
// s is of type 'string'
const s = firstElement(["a", "b", "c"]);
// n is of type 'number'
const n = firstElement([1, 2, 3]);


function identity<T>(arg: T): T {
  return arg;
}Try
```

## Constraints
Constraints are a way of forcing the type to be what we want so we can ensure functionality.
example:
```typescript
function merge<T extends object, U extends object>(objA: T, objB: U) {
 return Object.assign(abjA, objB);
}

const mergedObj = merge({name: 'huh'}, {age: 30});

interface lenthy {
  length: number;
}
// you can then extend the interface which will ensure that something has
// a length property

// ensures U is a key of T using the keyof keyword
function extractAndConvert<T extends object, U extends keyof T>(
  obj: T,
  key: U
) {
  return "Value: " + obj[key]
}

extractAndConvert({name: "Me"}, "name");

```
by extending the object we force the parameters to be of type object of some kind. You can also use union types.

## Generic Classes
```typescript
class Person<T, U, C> {
  name: T
  age: U
  hobby: C[]

  constructor(name: T, age: U, hobby: C[]) {
    this.name = name
    this.age = age
    this.hobby = hobby
  }
}

const output = new Person<string, number, string>('john doe', 23, ['swimming', 'traveling', 'badminton'])
console.log(output)
```

## Utility Types
[Utility Types Documentation](https://www.typescriptlang.org/docs/handbook/utility-types.html)

### Partial\<Type\>
Constructs a type with all properties of `Type` set to optional. This utility will return a type that represents all subsets of a given type.
```typescript
interface Todo {
  title: string;
  description: string;
}
 
function updateTodo(todo: Todo, fieldsToUpdate: Partial<Todo>) {
  return { ...todo, ...fieldsToUpdate };
}
 
const todo1 = {
  title: "organize desk",
  description: "clear clutter",
};
 
const todo2 = updateTodo(todo1, {
  description: "throw out trash",
});

function createCourseGoal(
title: string,
description: string,
date: Date
): CourseGoal {

let courseGoal: Partial<CourseGoal> = {}
courseGoal.title = title;
courseGoal.description = description;
courseGoal.completeUntil = date;
return courseGoal as CourseGoal; // here we type cast because the other properties have been added
}
```

### Readonly
Constructs a type with all properties of `Type` set to `readonly`, meaning the properties of the constructed type cannot be reassigned.
```typescript
const names Readonly<string[]> = ['Max', 'Anna'];
```