# Decorator
A _Decorator_ is a special kind of declaration that can be attached to a [class declaration](https://www.typescriptlang.org/docs/handbook/decorators.html#class-decorators), [method](https://www.typescriptlang.org/docs/handbook/decorators.html#method-decorators), [accessor](https://www.typescriptlang.org/docs/handbook/decorators.html#accessor-decorators), [property](https://www.typescriptlang.org/docs/handbook/decorators.html#property-decorators), or [parameter](https://www.typescriptlang.org/docs/handbook/decorators.html#parameter-decorators). Decorators use the form `@expression`, where `expression` must evaluate to a function that will be called at runtime with information about the decorated declaration.

Decorators run when you define the class.

## Syntax
```typescript
tsfunction f() {
  console.log("f(): evaluated");
  return function(target, propertyKey: string, descriptor: PropertyDescriptor) {
    console.log("f(): called");
  };
}

function g() {
  console.log("g(): evaluated");
  return function(target, propertyKey: string, descriptor: PropertyDescriptor) {
    console.log("g(): called");
  };
}

class C {
  @f()
  @g()
  method() {}
}
```

```typescript
function Logger(logString: string) {
return function(constructor: Function) {
	console.log(logString);
	console.log(constructor);
  }
}

@Logger(`Logging - Person`)
class Person {
name = "huh";

  constructor() {
  	console.log('Creating person object...')
  }
}
```
