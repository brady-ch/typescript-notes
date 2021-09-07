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

// Shorthand and also the best way to write the class
class Info {
	constructor(private name: string){}
  describe(){
    console.log(`Your name is  ${this.name}`);
  }
}
```

## Attributes

### public
This is the default, the property can be accessed outside of the class.

### private
The property cannot be accessed outside of the class. It's important to note that private fields will not be accessible in the classes that inherit from them, only in the class they are declared.

### readonly 
This can be used in conjunction with public or private, and it will mark that property as read only.

### protected
This will make the property accessible to any class that extends the class it is declared in.

### static
Static properties or methods are methods that can be called without an instance of a class. The Math class is a good example of this. You cannot access them with the this keyword because it is not related to the instance. 
```typescript
Math.rand(3); // static method

class Huhkay {
 contructor(private huh: type, public static arg: type){}
 
 get kay() {
    return this.huh;
 }
 
 get arg(){
	return Huhkay.arg; // needs to be accessed this way within the class
 }
 
 set kay(value: type) {
 this.huh = value;
 }
 
}

Huhkay.arg; // needs to be accessed this way outside of the class as well
const myInstance = new Huhkay("huh");
myInstance.kay; // using a getter, access like a property
myInstance.kay = "some text"; // using a setter, set like a property.
```

## Inheritance
Use the extends keyword to inherit from another class. Only one class can be inherited from. Inheriting means that you by default have access to everything the class you inherited from has. Super calls the constructor of the class you inherited from, this must be called before you use the `this` keyword in Typescript. 

```typescript
class huh extends kay{
constructor(){
super();
}
}
```

## Getters and Setters
Using getters and setters are considered best practice.

### Getters 
This can be used to access fields, usually private fields.
syntax
```typescript
class Huhkay {
 contructor(private huh: type){}
 
 get kay() {
    return this.huh;
 }
}

const myInstance = new Huhkay("huh");
myInstance.kay;
```

### setter
This can be used to modify fields.
syntax
```typescript
class Huhkay {
 contructor(private huh: type){}
 
 get kay() {
    return this.huh;
 }
 
 set kay(value: type) {
 this.huh = value;
 }
 
}

const myInstance = new Huhkay("huh");
myInstance.kay; // using a getter, access like a property
myInstance.kay = "some text"; // using a setter, set like a property.
```

## abstract classes
Forces all abstract methods to be overridden and implemented to be used. A class must be abstract to make abstract methods. An abstract class is made to be inherited from and cannot be implemented itself.

## Singletons and Private Constructors
This is used to set one and only one instantiation of a class.
syntax
```typescript
class MyClass
{
    private static _instance: MyClass;

    private constructor()
    {
        //...
    }

    public static get Instance()
    {
        // Do you need arguments? Make it a regular static method instead.
        return this._instance || (this._instance = new this());
    }
}

const myClassInstance = MyClass.Instance;
```

## Function Overloading
This is something that you can do, you do not need a keyword, you just need to change the parameter types.