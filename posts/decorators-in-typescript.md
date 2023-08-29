---
title: "Decorators in TypeScript"
date: "2023-08-29"
---

Decorators allow you to attach metadata or side behaviors to classes, class members, properties, methods, accessors, and function parameters. Decorators are executed during the definition of the decorated element, not during its execution. They provide a way to augment the behavior of various code constructs without changing their source code.

## Class decorators

```ts
function classDecorator(constructor: Function) {
  // Modify or extend the class behavior here
}

@classDecorator
class ExampleClass {
  // Class definition
}
```

## Property decorators

```ts
function propertyDecorator(target: any, propertyName: string) {
  // Modify or extend the property behavior here
}

class ExampleClass {
  @propertyDecorator
  propertyName: string;
}
```

## Accessor decorators

```ts
function accessorDecorator(
  target: any,
  propertyName: string,
  descriptor: PropertyDescriptor
) {
  // Modify or extend the accessor behavior here
}

class ExampleClass {
  @accessorDecorator
  get myProperty(): string {
    return this._myProperty;
  }
}
```

## Method decorators

```ts
function methodDecorator(
  target: any,
  methodName: string,
  descriptor: PropertyDescriptor
) {
  // Modify or extend the method behavior here
}

class ExampleClass {
  @methodDecorator
  myMethod() {
    // Method implementation
  }
}
```

## Parameter decorators

```ts
function parameterDecorator(
  target: any,
  methodName: string | undefined,
  parameterIndex: number
) {
  // Modify or extend the parameter behavior here
}

class ExampleClass {
  myMethod(@parameterDecorator param: string) {
    // Method implementation
  }
}
```

## Chaining decorators

When multiple decorators are applied to a single element, they are executed in **reverse order**. This reverse execution order provides a way for decorators to build upon each other's effects in a more intuitive way.

## Decorator factories

Decorators can also take parameters by using a pattern known as a _decorator factory_. This allows you to customize the behavior of a decorator when applying it to a specific element.
