<h1 align="center">Generics</h1>

### Overview of the Section
* **[First Class Decorator](#first-class-decorator)**
* **[Building More Useful Decorators](#building-more-useful-decorators)**
* **[Property Decorator](#property-decorator)**
* **[Accessor & Parameter Decorators](#accessor)**
* **[Other Decorator Return Types](#other)**
* **[NPM Class-Validator NPM](https://www.npmjs.com/package/typescript-class-validator)**
* **[GitHub Class-Validator](https://github.com/typestack/class-validator)**

#
### First Class Decorator

- Decorators in TypeScript:
    - Experimental feature requiring ``experimentalDecorators`` in ``tsconfig.json``.
    - Functions applied to classes, methods, properties, or parameters.
    - Execute when the definition is encountered, not during instantiation.

- Example Decorator:
    - ``@Logger`` logs a message and the constructor function when a class is defined.
    - Decorator receives the target (e.g., constructor function) as an argument.

- Code Example:
```
// tsconfig.json
{
  "compilerOptions": {
    "target": "es6",
    "experimentalDecorators": true
  }
}

// app.ts
function Logger(target: Function) {
  console.log("Logging:", target.name);
}

@Logger
class Person {
  name: string;

  constructor(name: string) {
    this.name = name;
    console.log("Creating person object");
  }
}

const person = new Person("Max");
console.log(person);
```
This code defines a ``Logger`` decorator that logs a message and the constructor function name when a class is decorated. The ``Person`` class is decorated with ``@Logger``, demonstrating its usage.

#
**[Back To The Top](#Overview-of-the-Section)**

### Building More Useful Decorators

- **Decorator Factories**: They enable creating decorators that accept configuration parameters, making them more versatile and reusable.
- **Template Rendering with Decorators**: You can write a decorator that takes a template string and a DOM hook ID, then renders the template into the specified element during component creation.
- **Metaprogramming**: Decorators create new functionality at compile time, allowing you to modify classes and their behavior dynamically.
- **Angular's Component Decorator**: It's a practical example of a decorator that accepts a template and selector to define component behavior and rendering.

```
// Decorator factory
function withTemplate(template: string, hookId: string) {
  return (target: any) => {
    const original = target.prototype.constructor; // Store original constructor
    target.prototype.constructor = function(...args) {
      // Call original constructor
      const instance = original.call(this, ...args);

      // Find hook element and render template
      const hookEl = document.getElementById(hookId);
      if (hookEl) {
        hookEl.innerHTML = template;
      }

      return instance;
    };
  };
}

// Class with decorator
@withTemplate(`<h1>My Person Object: {{ name }}</h1>`, 'app')
class Person {
  constructor(public name: string) {}
}

// Usage
const p = new Person('Alice');
```
#
**[Back To The Top](#Overview-of-the-Section)**
### Property Decorator

- **Decorators**: Functions that add metadata or behavior to classes, methods, properties, or parameters.
- **Placement**: Can be applied to various code elements.
- **Arguments**: Decorators receive different arguments depending on where they're used.
- **Logging Decorator**: Logs information when a property is defined.
- **Execution Timing**: Executes for property decorators when the class definition is registered, not during object instantiation.

**Code Example**:
```
class Product {
  constructor(title, price) {
    this._title = title;
    this._price = price;
  }

  get priceWithTax(taxRate = 0.1) {
    return this._price * (1 + taxRate);
  }

  set price(value) {
    if (value > 0) {
      this._price = value;
    } else {
      throw new Error("Invalid price: must be positive");
    }
  }

  get title() {
    return this._title;
  }
}

function logProperty(target, propertyName) {
  console.log("Property decorator:", target, propertyName);
}

class WithLogging extends Product {
  @logProperty // Decorates the title property
  set title(value) {
    super.title = value;
  }
}

const product = new WithLogging("My Product", 10);
product.title = "Updated Title"; // Triggers the log decorator
console.log(product.priceWithTax()); // Logs information when the method is defined
```
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="accessor">Accessor & Parameter Decorators</a>

- Decorators are special functions in TypeScript that allow you to add metadata or modify the behavior of classes, properties, methods, and parameters.
- There are four types of decorators:
    - **Property decorators**: Applied to properties to add functionality like logging or validation.
    - **Accessor decorators**: Applied to getters and setters to observe or modify their behavior.
    - **Method decorators**: Applied to methods to log invocations, modify arguments, or change behavior.
    - **Parameter decorators**: Applied to function parameters to validate input or perform actions based on the parameter value.
- Each decorator receives arguments based on what it decorates:
    - **Target**: The class prototype (instance member) or constructor function (static member).
    - **Name**: The name of the decorated member.
    - **Descriptor**: Property descriptor for properties and accessors, method descriptor for methods.
    - **Position**: Index of the parameter for parameter decorators.

**Code Example**:
```
class Product {
  @logPrice // Property decorator
  price: number;

  constructor(price: number) {
    this.price = price;
  }

  @logMethod // Method decorator
  getPriceWithText(text: string) {
    return `Price of ${text}: ${this.price}`;
  }
}

function logPrice(target: any, name: string): void {
  console.log(`Property "${name}" decorated with logPrice`);
}

function logMethod(target: any, name: string, descriptor: PropertyDescriptor): void {
  const originalMethod = descriptor.value;
  descriptor.value = function(...args: any[]) {
    console.log(`Calling method "${name}" with arguments:`, args);
    return originalMethod.apply(this, args);
  };
}

const product = new Product(10);
console.log(product.getPriceWithText("Product A"));
```
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="other">Other Decorator Return Types</a>

- Decorators can modify the behavior of classes, methods, and properties in JavaScript.
- Decorators applied to methods and accessors can return a new property descriptor object.
- This object allows modifying properties like ``configurable``, ``enumerable``, ``writable``, ``get``, and ``set``.
- This enables advanced functionality like changing how methods/accessors are defined and behave.

**Code Example**:
```
function logExecutionTime(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
  const originalMethod = descriptor.value;
  descriptor.value = function (...args: any[]) {
    const startTime = performance.now();
    const result = originalMethod.apply(this, args);
    const endTime = performance.now();
    console.log(`${propertyKey} execution time: ${endTime - startTime}ms`);
    return result;
  };
  return descriptor;
}

class MyClass {
  @logExecutionTime
  multiply(a: number, b: number) {
    return a * b;
  }
}

const myClass = new MyClass();
const result = myClass.multiply(2, 5); // Logs execution time and returns 10
```
This example defines a ``logExecutionTime`` decorator that wraps a method and logs its execution time. 

It achieves this by returning a new property descriptor with a modified ``value`` property (the actual method function). 

This is a very basic example, but it demonstrates how decorators can alter methods' behavior by returning new property descriptors.
**[Back To The Top](#Overview-of-the-Section)**