<h1 align="center">Advanced Types</h1>

### Overview of the Section
* **[Intersection Types](#intersection-types)**
* **[More on Type Guards](#more-on-type-guards)**


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



If you can do something with the type beofre you can use it.

### Discriminated Unions
Show me some examples of Discriminated Unions in Typescript with a code example?

### Type Casting
Explain me Type Casting in TypeScript with code example?

### Index Properties
Describe Index Properties in TypeScript with code example?

### Function Overloads
Show me an example of Function Overloads in TypeScript with a code example and explain me what it is?

### Optional Chaining
Explain me Optional Chaining in TypeScript with a code example and explain me what it is?

### Nullish Coalescing
Explain me a Nullish Coalescing in TypeScript with a code example and explain me what it is?




#
**[Back To The Top](#Overview-of-the-Section)**