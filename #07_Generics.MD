<h1 align="center">Generics</h1>

### Overview of the Section
* **[Built-in Generics & What are Generics](#generics)**
* **[Generic Function](#generic-function)**
* **[Generic Function](#constraints)**
* **[The "keyof" Constraints](#keyof)**
* **[Generics Classess](#generics-classes)**
* **[Generics Classess](#generics-classes)**

# 
### <a name="generics">Built-in Generics & What are Generics</a>

- The transcript discusses working with a dummy project setup using NPM and TypeScript (TSC) for development.
- It introduces the concept of generics in TypeScript, starting with the example of an array as a generic type.
- Generic types in TypeScript allow for flexibility in specifying the type of data a certain type (like an array or promise) will work with.
- The array type is a generic type that can store different types of data, and you can specify the type using square brackets or the Array keyword with angle brackets.
- The importance of generics is highlighted in improving TypeScript support by providing additional information about the type of data a generic type works with.
- The example extends to the built-in generic type Promise, showing how generics help define the type of data a promise will eventually yield.
- Generic types enhance type safety and provide better support from TypeScript when working with complex classes or functions that involve various data types.

**Simple Code Example**:
```
// Generic Array Type
let names: Array<string> = ["Max", "Manual"];

// Generic Promise Type
let myPromise: Promise<string> = new Promise((resolve) => {
    setTimeout(() => resolve("Data resolved"), 1000);
});

// Custom Generic Type
class MyGenericClass<T> {
    private data: T;

    constructor(initialData: T) {
        this.data = initialData;
    }

    getData(): T {
        return this.data;
    }
}

// Usage of Custom Generic Type
let myStringInstance = new MyGenericClass<string>("Hello, Generics!");
let myNumberInstance = new MyGenericClass<number>(42);

console.log(myStringInstance.getData()); // Outputs: Hello, Generics!
console.log(myNumberInstance.getData()); // Outputs: 42
```
#
**[Back To The Top](#Overview-of-the-Section)**

### Generic Function

- The transcript discusses the use of generics in TypeScript, focusing on creating a generic function for merging two objects.
- The initial example shows a non-generic function using the 'object' type, but it lacks specificity and causes issues with accessing properties later.
- Generics are introduced by adding angled brackets after the function name, defining generic identifiers (T and U in this case).
- With generics, TypeScript infers the types dynamically based on the arguments passed when the function is called.
- The generic function, 'merge,' takes two parameters of types T and U, and TypeScript infers that it returns the intersection of T and U.
- The use of generics allows for more flexibility and avoids the need for explicit type casting.
- The example demonstrates how TypeScript infers the types when calling the 'merge' function and how it enables working with specific data types without being overly restrictive.

**Simple Code Example**:
```
function merge<T, U>(objA: T, objB: U): T & U {
  return Object.assign({}, objA, objB);
}

const mergedObject = merge({ name: 'Max', hobbies: ['Reading', 'Coding'] }, { age: 30 });

console.log(mergedObject.age); // Accessing 'age' property without errors
```

In this example, the ``'merge'`` function takes two objects of ``types T`` and ``U``, and TypeScript infers the types dynamically. 

The result is an object that is an intersection of ``T`` and ``U``, allowing for flexible and type-safe merging of objects.
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="constraints">Working with Constraints</a>
Explain me working with Constraints in TypeScript with a code example?

### <a name="keyof">The "keyof" Constraints</a>
Show me an example of "keyof" with a code example and when is good pratice to use "keyof"?

### Generics Classes
Explain me generic classes in TypeScript with a code example and point out all important details in connection with generic classes?

### Generic Utility Types
Explain me some generic utility types in TypeScript with code examples and tell me where we can use them?

### Generic Types vs Union Types
Explain me a key difference between Generic Types vs Union Types in TypeScript and some use cases?

#
**[Back To The Top](#Overview-of-the-Section)**