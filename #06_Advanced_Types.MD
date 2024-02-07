<h1 align="center">Advanced Types</h1>

### Overview of the Section
* **[Intersection Types](#intersection-types)**
* **[More on Type Guards](#more-on-type-guards)**
* **[Discriminated Unions](#discriminated-unions)**
* **[Type Casting](#type-casting)**
* **[Index Properties](#index-properties)**
* **[Function Overloads](#function-overloads)**
* **[Optional Chaining](#optional-chaining)**
* **[Nullish Coalescing](#nullish-coalescing)**

#
### Intersection Types
- Intersection types allow you to combine multiple types into a single new type.
- You can use the & symbol to combine types.
- Intersection types are useful for creating complex object types from existing types.
- They can be used with any type, not just object types.
- They are similar to interface inheritance, but can be more concise.

**Simple code example**:
```
// Define two types
type Admin = {
  name: string;
  privileges: string[];
};

type Employee = {
  name: string;
  startDate: Date;
};

// Combine the types to create a new type
type ElevatedEmployee = Admin & Employee;

// Create an object of the new type
const e1: ElevatedEmployee = {
  name: "John Doe",
  privileges: ["create server"],
  startDate: new Date(),
};

// Access properties of the object
console.log(e1.name); // Output: John Doe
console.log(e1.privileges); // Output: ["create server"]
console.log(e1.startDate); // Output: Date object
```
This code defines two types, ``Admin`` and ``Employee``, and then combines them to create a new type, ``ElevatedEmployee``. 

An object of this new type must have all the properties of both ``Admin`` and ``Employee``. 

Finally, the code creates an object of the ``ElevatedEmployee`` type and accesses its properties.
#
**[Back To The Top](#Overview-of-the-Section)**


### More on Type Guards
- **Intersection Types and Type Guards**: The transcript discusses intersection types and focuses more on type guards, a feature used with union types in TypeScript.
- **Example - Union Type and Type Guard with ``typeof``**: A code example demonstrates the use of a union type ``(Combinable)`` in a function ``(add)`` where type guards ``(typeof)`` are employed to handle different types (string or number).
- **Challenges with ``typeof`` in Type Guards**: The limitations of using typeof for type guards are discussed, particularly when dealing with custom object types where TypeScript cannot confirm property existence.
- **Alternative Type Guard with ``in`` Operator**: A workaround is presented using the in operator to check for property existence, overcoming the limitations of typeof in type guards.
- **Type Guards for Custom Classes**: The transcript explores type guards for classes, introducing the ``instanceof`` type guard to check if an object is an instance of a particular class, allowing conditional use of class-specific methods.
- **Comparison between ``in`` and ``instanceof``**: The discussion includes a comparison between using ``in`` and ``instanceof`` as type guards, emphasizing the suitability of ``instanceof`` for classes due to JavaScript's support for constructor functions.

**Simple Code Example**:
```
// Union Type and Type Guard with `typeof`
type Combinable = string | number;

function add(a: Combinable, b: Combinable): string | number {
  if (typeof a === 'string' || typeof b === 'string') {
    return a.toString() + b.toString();
  }
  return a + b;
}

// Type Guard with `in` Operator for Custom Object Types
type UnknownEmployee = Employee | Admin;

function printEmployeeInformation(emp: UnknownEmployee): void {
  console.log(emp.name);
  
  if ('privileges' in emp) {
    console.log(emp.privileges);
  }

  if ('startDate' in emp) {
    console.log(emp.startDate);
  }
}

// Type Guard with `instanceof` for Custom Classes
class Car {
  drive(): void {
    console.log('Driving');
  }
}

class Truck {
  drive(): void {
    console.log('Driving a truck');
  }

  loadCargo(amount: number): void {
    console.log('Loading cargo plus ' + amount);
  }
}

type Vehicle = Car | Truck;

function useVehicle(vehicle: Vehicle): void {
  vehicle.drive();

  if (vehicle instanceof Truck) {
    vehicle.loadCargo(100);
  }
}

// Example Usage
const car = new Car();
const truck = new Truck();

useVehicle(car);   // Outputs: "Driving"
useVehicle(truck); // Outputs: "Driving a truck" and "Loading cargo plus 100"
```
#
**[Back To The Top](#Overview-of-the-Section)**

### Discriminated Unions

- **Discriminated unions**: A pattern for type safety when working with object literals in union types.
- **Key idea**: Add a common "type" property to each object literal in the union, indicating its specific type (e.g., "bird" or "horse").
- **Benefits**:
    - **Type safety**: Ensures you access only valid properties based on the object's type.
    - **Autocompletion**: IDEs suggest valid properties based on the "type" value.
    - **No typos**: TypeScript catches typos in the "type" value preventing runtime errors.

**Simple Code Example**:
```
interface Bird {
  type: "bird";
  flyingSpeed: number;
}

interface Horse {
  type: "horse";
  runningSpeed: number;
}

type Animal = Bird | Horse;

function moveAnimal(animal: Animal): void {
  let speed: number;
  switch (animal.type) {
    case "bird":
      speed = animal.flyingSpeed;
      break;
    case "horse":
      speed = animal.runningSpeed;
      break;
    default:
      throw new Error("Invalid animal type");
  }
  console.log(`Moving at speed ${speed}`);
}

const bird: Bird = { type: "bird", flyingSpeed: 20 };
moveAnimal(bird); // Output: Moving at speed 20

const horse: Horse = { type: "horse", runningSpeed: 30 };
moveAnimal(horse); // Output: Moving at speed 30
```
This example demonstrates how a discriminated union ensures type safety and provides better developer experience while working with animal objects.

#
**[Back To The Top](#Overview-of-the-Section)**

### Type Casting

- **Discriminated Unions**: A powerful construct in TypeScript that allows representing values with different shapes based on a specific property that distinguishes them.

- **Type Casting**: A mechanism to manually tell TypeScript that a value has a specific type even if it can't be inferred automatically.

- **Use Cases**:
    - When TypeScript lacks enough information to infer the correct type (e.g., selecting elements from the DOM).
    - When working with external libraries or code that doesn't provide accurate type information.

- **Syntax**:
    - as ``<type>`` (before the expression)
    - ``<type>`` (angle brackets, often preferred in React due to JSX collision concerns)

- **Limitations**:
    - Not a substitute for sound type-based development.
    - Use it judiciously to avoid runtime errors and maintain type safety.
    - Ensure the cast is valid or TypeScript won't catch potential issues.

**Code Example**:
```
// DOM example using angle brackets syntax
const paragraph = document.querySelector<HTMLParagraphElement>('p');
// Now you can safely access paragraph-specific properties and methods:
paragraph.textContent = 'Hello, world!';

// Input element example using "as" syntax
const userInputElement = document.getElementById('user-input') as HTMLInputElement;
// TypeScript knows it's an input and allows accessing value:
const userValue = userInputElement.value;

// Remember to handle potential null values appropriately for safety.
```
#
**[Back To The Top](#Overview-of-the-Section)**

### Index Properties

- **Index Types**: TypeScript's index types empower you to create flexible objects where property names and their number are unknown beforehand. These properties must have the specified value type (e.g., string, number).

- **Benefits**:
    - Enable dynamic data structures that adapt to various input scenarios.
    - Simplify code for handling objects with uncertain property keys.
    - Provide type safety even in flexible scenarios.

- **Use Cases**:
    - Validating user input with different error messages for diverse fields.
    - Storing dynamic data retrieved from APIs or user interactions.
    - Creating collections where property names vary.

**Simple Code Example**:
```
interface ErrorContainer {
  [key: string]: string; // Index type: property names are strings, values are strings
}

// Create an error container
const errorBag: ErrorContainer = {};

// Add errors dynamically
errorBag.email = "Not a valid email";
errorBag.username = "Must start with a capital character";

// Use the error container
for (const [key, value] of Object.entries(errorBag)) {
  console.error(`Error in ${key}: ${value}`);
}
```
#
**[Back To The Top](#Overview-of-the-Section)**

### Function Overloads

- **Function Overload**: In TypeScript, function overloads allow defining multiple function signatures with the same name but different parameter types and return types. This enables the function to handle various parameter combinations and provide type-safe behavior.
- **Motivatio**: Function overloads address limitations in type inference when a function can return different types based on input. They clarify return types to TypeScript, prevent type errors, and improve code readability.
- **Synta**: Define overloads by writing function declarations with specific parameter types and return types above the main function implementation. Each overload must have a semicolon.
- **Flexibility**: You can have different numbers of parameters and types in each overload, as long as the function logic handles them correctly.
- **Example**: The ``add`` function demonstrates overloads for handling combinations of numbers and strings, ensuring proper type inference for various inputs.

**Code Example**:
```
function add(a: number, b: number): number;
function add(a: string, b: string): string;
function add(a: any, b: any): any {
  if (typeof a === 'number' && typeof b === 'number') {
    return a + b;
  } else if (typeof a === 'string' && typeof b === 'string') {
    return a + ' ' + b;
  } else {
    // Handle other combinations or throw an error if desired
    throw new Error('Unsupported argument types');
  }
}

const result1 = add(1, 2); // result1 is inferred as number (5)
const result2 = add('hello', 'world'); // result2 is inferred as string ("hello world")
// const result3 = add(1, 'hello'); // This call would throw an error if not handled

console.log(result1); // Output: 5
console.log(result2); // Output: hello world
// console.log(result3); // Would throw an error if not handled
```
#
**[Back To The Top](#Overview-of-the-Section)**

### Optional Chaining

- **Optional chaining operator ``(?.)``**: Introduced in TypeScript 3.7, it allows safe access to nested properties, even if intermediate ones are undefined or null.
- **Avoiding runtime errors**: When using optional chaining, if a property is undefined, the expression stops and returns undefined instead of throwing an error.
- **Use cases**: Ideal for working with data from external sources where you're unsure about its structure or completeness.
- **Example**: ``fetchedUserData?.job?.title`` accesses ``title`` only if ``fetchedUserData`` and ``job`` are defined.

**Simple Code Example**:
```
interface User {
  id: number;
  name: string;
  job?: {
    title: string;
    description: string;
  };
}

function getUserJobTitle(user: User): string | undefined {
  return user?.job?.title;
}

const userData: User = {
  id: 1,
  name: "John Doe",
};

const jobTitle = getUserJobTitle(userData); // undefined (no job property)

console.log(jobTitle); // Output: undefined

// Example with job property
userData.job = {
  title: "Software Engineer",
  description: "Building awesome things",
};

const newJobTitle = getUserJobTitle(userData); // "Software Engineer"

console.log(newJobTitle); // Output: "Software Engineer"
```
#
**[Back To The Top](#Overview-of-the-Section)**

### Nullish Coalescing

- **Nullish Coalescing Operator ``(??)``**: This operator provides a fallback value if the left operand is null or undefined.
- **Difference from Logical OR ``(||)``**: The ``||`` operator considers other falsy values like empty strings and 0 as false, while ``??`` only treats null and undefined as falsy.
- **Use Cases**: Use ``??`` to provide default values while preserving non-nullish falsy values like empty strings and zeros.

**Simple Code Example**:
```
let userInput: string | null = null; // Could be null or a string

let storedData = userInput ?? "DEFAULT"; // Use "DEFAULT" if userInput is nullish

console.log(storedData); // Output: DEFAULT

userInput = ""; // Now userInput is an empty string

storedData = userInput ?? "DEFAULT"; // No fallback, storedData keeps the empty string

console.log(storedData); // Output: ""
```
This code demonstrates how the ``??`` operator preserves the empty string input while providing a default value for ``null`` and ``undefined``.

**[Back To The Top](#Overview-of-the-Section)**