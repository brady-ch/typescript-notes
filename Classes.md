# Classes

## Definition
A class is a block of code that holds various functions. Because they are located inside a class they are named methods but mean the same thing. In addition variables that are stored inside a class are named attributes. The point of a class is to call the class later allowing you to access as many functions or (methods) as you would like with the same class name. These methods are grouped together under one class name due to them working in association with each other in some way.

Class is a blueprint or template which you can create as many objects as you like. Object is a member or instance of a class. Class is declared using class keyword, Object is created through new keyword mainly. A class is a template for objects. A class defines object properties including a valid range of values, and a default value. A class also describes object behavior.

## Syntax
```typescript
class Info {
  private name: string;
  constructor(n:string){
    this.name = n ;
  };
  describe(){
    console.log(`Your name is  ${this.name}`);
  }
}

const a = new Info('joyous');
a.describe();
```
