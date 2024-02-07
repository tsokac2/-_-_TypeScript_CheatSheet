<h1 align="center">Generics</h1>

### Overview of the Section
* **[Built-in Generics & What are Generics](#generics)**
* **[Generic Function](#generic-function)**
* **[Working with Constraints](#constraints)**
* **[The "keyof" Constraints](#keyof)**
* **[Generics Classess](#generics-classes)**
* **[Generic Utility Types](#generic-utility-types)**
* **[Generic Types vs Union Types](#generic-types-vs-union-types)**

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

- Generics enhance code reusability by working with various data types.
- Type constraints restrict generic types to ensure type safety and prevent unexpected behavior.
- ``extends object`` constraint enforces that generic types must be objects.
- Error handling in generic functions catches type mismatches and provides informative messages.
- TypeScript compiler throws errors for type violations during development, preventing runtime issues.

**Simple Code Example**:
```
function merge<T extends object, U extends object>(obj1: T, obj2: U): T & U {
  // ... (implementation merging properties from obj1 and obj2)
}

const person1 = { name: 'Alice', age: 30 };
const person2 = { hobbies: ['coding', 'reading'] };

const mergedPerson = merge(person1, person2); // Type: { name: string; age: number; hobbies: string[] }

console.log(mergedPerson); // Output: { name: 'Alice', age: 30, hobbies: ['coding', 'reading'] }
```
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="keyof">The "keyof" Constraints</a>
- Generics allow creating reusable code that works with different data types.
- Constraints can be added to generics to enforce specific requirements on the data types used.
- The ``keyof`` operator can be used with generics to ensure a key exists in an object of a specific type.
- This improves type safety and prevents runtime errors.

**Code Example**:
```
function extractAndConvert<T extends object, U extends keyof T>(obj: T, key: U): T[U] {
  return obj[key];
}

const person = { name: "Alice", age: 30 };

const name = extractAndConvert(person, "name"); // type: string
// const age = extractAndConvert(person, "age"); // Error: "age" is not a key of type "Person"

console.log(name); // Output: "Alice"
```
#
**[Back To The Top](#Overview-of-the-Section)**

### Generics Classes

- **Generic Classes**: Allow you to create flexible, reusable classes that can work with different data types without sacrificing type safety.

- **Benefits**:
    - Increased code reusability
    - Reduced code duplication
    - Enhanced type safety
    - Improved code maintainability

- **Creation**: Use angle brackets < > after the class name and specify a placeholder type parameter (e.g., T).

- **Example**: DataStorage<T> can store different data types depending on the generic type specified (e.g., DataStorage<string>, DataStorage<number>).

- **Constraints**: Can be applied to generic types using extends to limit valid data types (e.g., DataStorage<T extends string | number>).

- **Considerations**:
    - Not all scenarios require generic classes.
    - Overusing generics can add complexity.
    - Carefully consider constraints to maintain type safety.

**Code Example**:
```
class DataStorage<T extends string | number> {
    private data: T[] = [];

    addItem(item: T): void {
        this.data.push(item);
    }

    removeItem(item: T): void {
        const index = this.data.findIndex(obj => obj === item); // Correctly handles object comparison
        if (index !== -1) {
            this.data.splice(index, 1);
        }
    }

    getItems(): T[] {
        return [...this.data]; // Returns a copy using spread operator
    }
}

// Usage:
const textStorage = new DataStorage<string>();
textStorage.addItem("Max");
textStorage.addItem("Manu");
console.log(textStorage.getItems()); // Output: ["Max", "Manu"]

const numberStorage = new DataStorage<number>();
numberStorage.addItem(10);
numberStorage.addItem(20);
console.log(numberStorage.getItems()); // Output: [10, 20]

// Attempting to add an object to numberStorage results in a type error (as expected)
// numberStorage.addItem({ name: "Object" });

// ... further usage demonstrating different generic types and constraints
```
#
**[Back To The Top](#Overview-of-the-Section)**

### Generic Utility Types

- **Generics enhance code reusability and type safety**: By defining components that work with various types instead of just one, you write adaptable code with built-in type checks.

- **TypeScript offers built-in utility types for common scenarios**: partial makes all properties in a type optional, and readonly prevents modifications to the type (arrays, objects).

- **Apply utility types selectively based on use cases**: Choose partial when temporarily setting up objects with optional properties, and readonly to enforce immutability.

**Simple Code Example**:
```
interface CourseGoal {
  title: string;
  description: string;
  completeUntil: Date;
}

// Using partial for flexible object creation:
function createCourseGoal(title: string, description: string, completeUntil: Date): CourseGoal {
  const partialGoal: Partial<CourseGoal> = {};
  partialGoal.title = title;
  partialGoal.description = description;
  partialGoal.completeUntil = completeUntil;
  return partialGoal as CourseGoal; // Type assertion as we know it's complete
}

// Using readonly for immutable arrays:
const names: readonly string[] = ["Max", "Anna"];
// names.push("Alice"); // Error: cannot add to readonly array

console.log(createCourseGoal("TypeScript Deep Dive", "Learn advanced concepts", new Date()));
console.log(names); // Output: ["Max", "Anna"]
```

**Explanation**:
- ``CourseGoal interface``: Defines the expected properties and their types.
- ``createCourseGoal function``: Demonstrates using partial to create an object with optional properties initially. It adds properties step-by-step and converts to CourseGoal using type assertion.
- ``names`` array: Declared as readonly string[] to prevent modifications like push or pop.
#
**[Back To The Top](#Overview-of-the-Section)**

### Generic Types vs Union Types
- Generics allow you to define a type placeholder that can be later specified when using the code. They ensure consistency and type safety throughout the code.
- Union types allow a variable to hold one of several specific types. They offer flexibility but can lead to type mismatch issues if not used carefully.

**Simple code example**:
```
class DataStorage<T> {
  private data: T[] = [];

  addItem(item: T) {
    this.data.push(item);
  }

  getItem(index: number): T {
    return this.data[index];
  }
}

// Usage:
const stringStorage = new DataStorage<string>();
stringStorage.addItem("hello"); // OK
stringStorage.addItem(10); // Error: cannot add number to string storage

const numberStorage = new DataStorage<number>();
numberStorage.addItem(10); // OK
numberStorage.addItem("hi"); // Error: cannot add string to number storage
```
**[Back To The Top](#Overview-of-the-Section)**