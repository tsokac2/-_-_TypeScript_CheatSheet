<h1 align="center">TypeScript Basics & Basic Types</h1>

### Overview of the Section
* **[TypeScript Core Types](#TypeScript-Core-Types)**
* **[TypeScript Types vs JavaScript Types](#TypeScript-Types-vs-JavaScript-Types)**
* **[Difference between Runtime and Development](#Difference-between-Runtime-and-Development)**
* **[Working with Numbers Strings and Booleans](#Working-with-Numbers-Strings-and-Booleans)**
* **[Type Assignment and Type Inference](#Type-Assignment-and-Type-Inference)**
* **[Object Types](#Object-Types)**
* **[Arrays Types](#Arrays-Types)**
* **[Working with Tuples](#Working-with-Tuples)**
* **[Working with Enums](#Working-with-Enums)**
* **[Union Types](#Union-Types)**
* **[Literal Types](#Literal-Types)**
* **[Type Aliases Custom Types](#Type-Aliases-Custom-Types)**
* **[Function Return Types and "void"](#Function-Return-Types-and-%34void%34)**





#
### TypeScript Core Types

TypeScript, as a statically typed superset of JavaScript, provides a set of core types, including number, string, and boolean. Let's me describe each of them in detail:

#### 'number'

- The number type in TypeScript represents both integer and floating-point numbers.
- It can be used to define variables that store numeric values, such as age, price, or any kind of quantity.
- TypeScript ensures type safety by allowing only numeric values to be assigned to variables of this type.
- For example, you can declare a variable as follows:

```let age: number = 30;```

#### 'string'

- The string type represents textual data, such as words, sentences, or any sequence of characters.
- It's commonly used for storing and manipulating text in variables.
- TypeScript ensures that you can only assign string values to variables of this type.
- Here's an example:

``` let name: string = "Tomislav"; ```

#### 'boolean'

- The boolean type represents logical values - either true or false.
- It's often used for storing and working with conditions or states in code.
- Variables of type boolean can only hold true or false values.
- Example usage:

```let isRemoteJob: boolean = true;```

These core types are essential building blocks in TypeScript, helping developers ensure type safety and improve code readability and maintainability. 

They provide a strong foundation for creating more complex data structures and custom types as needed for your API integration work.

#### Note!
In TypeScript, you work with types like string or number all the times.

**Important:** It is ```string``` and ```number``` (etc.), NOT String, Number etc.

_The core primitive types in TypeScript are all lowercase!_

**[Back To The Top](#Overview-of-the-Section)**

#
### TypeScript Types vs JavaScript Types
The key difference is: JavaScript uses **“dynamic types”** (resolved at runtime), TypeScript uses **“static types”** (set **only** during development).

TypeScript and JavaScript are two closely related yet distinct programming languages, and their approach to types is a significant differentiator.

#### JavaScript Types

JavaScript is a dynamically typed language, which means that variable types are determined at runtime. This flexibility can be both an advantage and a potential source of errors. JavaScript types include:

- **Primitive Types:** These are simple data types like numbers, strings, booleans, null, undefined, and symbols. JavaScript infers the type dynamically based on the value assigned to the variable.

- **Reference Types:** These include objects, arrays, functions, and more complex data structures. The type is determined by the object's constructor function.

#### TypeScript Types

TypeScript, on the other hand, is a statically typed superset of JavaScript. 

It allows developers to specify types for variables, function parameters, and return values. TypeScript types offer several benefits:

- **Static Typing:** By defining types, you catch many potential errors at compile-time, reducing runtime issues.

- **Code Documentation:** Types serve as a form of self-documentation, making the code more readable and understandable.

- **Editor Assistance:** IDEs and code editors can provide intelligent auto-completions and suggestions based on the specified types.

- **Maintainability:** TypeScript helps in managing larger codebases by ensuring that the code adheres to the defined types.

#### Opinion

In my professional opinion, TypeScript's use of static types can be a game-changer for large-scale applications and complex projects. It provides enhanced code quality and maintainability. However, for smaller, simple scripts, JavaScript's dynamic typing might be more convenient and faster to write.

The choice between TypeScript and JavaScript often depends on the project's scale, team preferences, and the need for strong type checking. Many organizations have found TypeScript to be a valuable addition to their development stack, especially when working on mission-critical applications.

**[Back To The Top](#Overview-of-the-Section)**
#
### Difference between Runtime and Development

#### Development
Development, in the context of coding, refers to the phase where software is created, designed, and written by developers or engineers. 

It's the process of translating a concept or idea into actual code. During this phase, developers write, test, and debug their code to ensure it performs the desired functions. 

Key aspects of development include:

- **Coding:** Writing the actual code in a programming language.
- **Design:** Planning and structuring the software's architecture.
- **Testing:** Verifying that the code works as intended.
- **Debugging:** Identifying and fixing issues and errors in the code.

The development phase is primarily concerned with producing a working and reliable software application.

#### Runtime
Runtime, on the other hand, is the phase when the software is actually executed or run by end-users or on a target system. 

It's the period during which the software operates and performs its intended functions. Key aspects of runtime include:

- **Execution:** The software is used to perform tasks or provide services.
- **User Interaction:** End-users interact with the software.
- **Data Processing:** The software processes data and responds to inputs.

During runtime, the focus shifts from coding and development to the actual operation of the software in real-world scenarios. 
Any issues or errors that were not caught during development may become apparent during runtime and need to be addressed.

In summary, development is the phase where code is written, tested, and refined, while runtime is the phase where the software is actively used to fulfill its intended purpose.

These two phases are interconnected, with issues identified during runtime often requiring adjustments in the development phase. Therefore, a well-structured and thoroughly tested development phase is crucial for a smooth and reliable runtime experience.

**[Back To The Top](#Overview-of-the-Section)**
#

### Working with Numbers Strings and Booleans
In TypeScript, you can work with numbers, strings, and booleans just like in many other programming languages.

#### Working with Numbers:
```
// Declare a number variable
let age: number = 30;

// Perform arithmetic operations
let sum = age + 5;
let product = age * 2;
let division = age / 3;

// Increment and decrement
age++; // Increment age by 1
age--; // Decrement age by 1
```
#### Working with Strings:
```
// Declare a string variable
let name: string = "Tomislav";

// String concatenation
let greeting = "Hello, " + name;

// String interpolation using template literals
let message = `Welcome, ${name}!`;

// String length
let nameLength = name.length;

// Access characters in a string
let firstChar = name[0]; // Access the first character
```

#### Working with Booleans:
```
// Declare boolean variables
let isOnline: boolean = true;
let hasAccount: boolean = false;

// Conditional statements
if (isOnline) {
    console.log("User is online.");
} else {
    console.log("User is offline.");
}

// Logical operators
let result = isOnline && hasAccount; // AND operator
let oppositeResult = !isOnline; // NOT operator
```

These examples demonstrate how to work with numbers, strings, and booleans in TypeScript. 

TypeScript provides type checking and static analysis, which can help catch errors at compile time and make your code more robust and maintainable.

**[Back To The Top](#Overview-of-the-Section)**

#
### Type Assignment and Type Inference

#### Type Assignment in TypeScript
Type assignment in TypeScript refers to explicitly specifying the data type of a variable, parameter, or return value when you declare a variable or define a function. 

This is done using TypeScript's type annotations. 

For example: ```let age: number = 30;```

In the above code, age is explicitly assigned the number type. This means it can only store numeric values.

#### Type Inference in TypeScript:
Type inference, on the other hand, is TypeScript's ability to automatically determine the data type of a variable based on the value assigned to it. 
You don't need to explicitly specify the type; TypeScript infers it for you. 

For instance: ```let name = "Tomislav";```

Here, TypeScript infers that name is of type string because it is assigned a string value.

Type inference is a powerful feature in TypeScript that allows for more concise and readable code. It is especially handy when dealing with complex data structures and function return types. TypeScript's type inference is often based on the initial value assigned and how the variable or function is used in the code.

It's important to note that while type inference can make your code more concise, there are situations where explicitly specifying types (type assignment) can provide clarity and help catch errors early in development.

**[Back To The Top](#Overview-of-the-Section)**

#
### 

Object types in TypeScript refer to how you define and specify the structure of objects and their properties in your code. This is essential for achieving type safety and preventing runtime errors. TypeScript provides several ways to work with object types:

#### Nested Objects and Types
Of course object types can also be created for nested objects.

Let's say you have this JavaScript object:
```

const product = {
  id: 'abc1',
  price: 12.99,
  tags: ['great-offer', 'hot-and-new'],
  details: {
    title: 'Red Carpet',
    description: 'A great carpet - almost brand-new!'
  }
}
```

This would be the type of such an object:
```
{
  id: string;
  price: number;
  tags: string[];
  details: {
    title: string;
    description: string;
  }
}
```
So you have an object type in an object type so to say.

**[Back To The Top](#Overview-of-the-Section)**
#
### Object Types

Object types in TypeScript refer to how you define and specify the structure of objects and their properties in your code. This is essential for achieving type safety and preventing runtime errors. 

TypeScript provides several ways to work with object types:

#### Object Literal Types
You can define object types directly using object literals. For example:
```
let person: { name: string; age: number } = {
  name: "Tomislav",
  age: 30
};
```
In this example, we've defined an object type for a person with a name property of type string and an age property of type number.

#### Interface
Interfaces are a powerful tool in TypeScript for defining the shape of objects. 
They allow you to declare a contract that objects must adhere to. For instance:
```
interface Person {
  name: string;
  age: number;
}

let person: Person = {
  name: "Tomislav",
  age: 30
};
```
Interfaces make your code more maintainable and allow you to ensure that objects conform to a specific structure.

#### Class Types
You can use classes to define object types, which encapsulate both the structure and behavior of an object.
```
class Person {
  constructor(public name: string, public age: number) {}
}

let tomislav: Person = new Person("Tomislav", 30);
```
In this case, the Person class defines an object type, and you create instances of it.

#### Type Aliases
You can create custom type aliases using the type keyword to simplify complex type definitions. For example:
```
type Point = { x: number; y: number };

let origin: Point = { x: 0, y: 0 };
```
Type aliases make your code more readable by providing meaningful names for complex types.

#### Index Signatures

TypeScript allows you to define objects with dynamic property names using index signatures. 
This is useful when you don't know all property names in advance.
```
interface Dictionary {
  [key: string]: string;
}

let dict: Dictionary = {
  key1: "value1",
  key2: "value2"
};
```
In this case, the object can have any string keys with string values.

In summary, object types in TypeScript give you the flexibility to define and enforce the structure of objects in your code, making it more predictable and safer. The choice of which method to use depends on your specific use case and coding style.

**[Back To The Top](#Overview-of-the-Section)**
#
### Arrays Types

In TypeScript, arrays can be of various types, allowing you to work with data in a strongly typed manner. 
Here are some commonly used array types:

#### Typed Arrays
TypeScript allows you to create arrays with specific element types, ensuring type safety. For example, you can create an array of strings like this:
```
let names: string[] = ["Tomislav", "John", "Alice"];
```
This ensures that only strings can be stored in the names array.

#### Tuple Types
TypeScript introduces tuples, which are fixed-length arrays where each element can have a different type. Here's an example:
```
let employee: [string, number] = ["Tomislav", 30];
```
Tuples are useful when you need to represent a fixed structure, such as a pair of values.

#### Array Union Types
You can also create arrays that can hold multiple types using union types. For example:
```
let values: (string | number)[] = ["Tomislav", 42, "Alice"];
```

#### Array Type Inference
TypeScript can often infer the array type based on the values you initialize it with. For instance:
```
let colors = ["red", "green", "blue"];
// TypeScript infers `colors` as an array of strings: string[]
```
This type safety ensures that you don't accidentally insert the wrong type of data into your arrays, making your code more robust.

**[Back To The Top](#Overview-of-the-Section)**
#
### Working with Tuples

Tuples are a data structure that allows you to store a fixed number of elements with different data types in a specific order. 
 
They can be particularly handy when you need to work with collections of values where each element has a well-defined purpose.

#### Tuple Declaration
To create a tuple in TypeScript, you declare it using square brackets [] and specify the data types for each element within. For example:
```
let myTuple: [string, number] = ['Tomislav', 30];
```
#### Accessing Elements
You can access elements of a tuple using indexing, just like with arrays. 
TypeScript enforces that you access elements with the correct data types, which is helpful for maintaining type safety. For instance:
```
let name: string = myTuple[0]; // 'Tomislav'
let age: number = myTuple[1];  // 30
```
#### Fixed Length
Tuples have a fixed length, which means you cannot add or remove elements after the tuple is created. This constraint is beneficial when you need a strict structure for your data.
#### Array-like Operations
You can perform array-like operations on tuples, such as looping through them, iterating using for...of, or using the forEach method.
```
for (let item of myTuple) {
    console.log(item);
}
```
#### Tuple Unpacking
TypeScript allows you to use destructuring to assign tuple elements to individual variables
```
let [name, age] = myTuple;
```
This can make your code more readable and concise.
#### Optional and Rest Elements
TypeScript supports optional elements and rest elements in tuples. An optional element can be defined using the ? notation, and the rest element using the ... notation. For example:
```
let myOptionalTuple: [string, number?] = ['Tomislav'];
let myRestTuple: [string, number, ...string[]] = ['Tomislav', 30, 'Dublin', 'Ireland'];
```
**[Back To The Top](#Overview-of-the-Section)**

#
### Working with Enums
Working with Enums in TypeScript is an essential aspect of building type-safe and maintainable code. Enums, short for "enumerations," are a way to define a set of named constants. 
 
They allow you to assign symbolic names to a group of values, which can be more human-readable and self-explanatory than raw values. Here's a detailed explanation of working with Enums in TypeScript:

#### Enum Declaration
To define an Enum in TypeScript, you use the enum keyword followed by the name of the Enum, like this:
```
enum Days {
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday
}
```
In this example, Days is an Enum representing the days of the week, and the values are automatically assigned numeric indices starting from 0.
#### Accessing Enum Members
You can access Enum members using the dot notation:
```
let today: Days = Days.Wednesday;
```
#### Enum Values
By default, Enum members are assigned numeric values starting from 0. However, you can specify custom values:
```
enum Color {
    Red = 1,
    Green = 2,
    Blue = 4
}
```
In this case, Color.Red would be 1, Color.Green would be 2, and so on. This is particularly useful when dealing with bit flags.

**[Back To The Top](#Overview-of-the-Section)**

#
### Union Types

 Union types in TypeScript are a powerful feature that allows you to define a variable or parameter that can hold values of multiple types. 
 
 They provide flexibility in scenarios where a particular piece of data can be of different data types, such as strings, numbers, or custom objects. 
 
 By using union types, you can explicitly specify all the possible types that a variable can have.

 Here's an example to illustrate union types:

 ```
 function displayResult(value: number | string) {
    console.log(`Result: ${value}`);
}

displayResult(42);       // Valid, as it's a number
displayResult("Hello");  // Valid, as it's a string
displayResult(true);     // Error, as it's not part of the union type
```

In the above code, the value parameter can accept both number and string types, indicated by the union type number | string. 

This flexibility is beneficial because it allows you to handle different data types while maintaining type safety.

Union types are particularly useful in situations where you want to accept multiple types of inputs or when working with libraries that return different types based on certain conditions. They help in making your code more expressive and self-documenting. However, keep in mind that you need to handle the different possible types properly within your functions or methods to avoid runtime errors.

**[Back To The Top](#Overview-of-the-Section)**

#
### Literal Types

 Literal types in TypeScript are a fascinating feature that allows you to specify exact values that a variable can hold. 
 
 They are particularly useful when you want to restrict a variable to a fixed set of values, making your code more type-safe and self-explanatory.

 #### String Literal Types 
 These restrict a variable to only one specific string value. For example, you can define a variable like this:
 ```
 let direction: "up" | "down" | "left" | "right";
 ```
Here, 'direction' can only hold one of the four specified string values, making it very clear and strict in its usage.

#### Numeric Literal Types
These are similar to string literal types but for numeric values. For instance:
```
let diceRoll: 1 | 2 | 3 | 4 | 5 | 6;
```
'diceRoll' can only be assigned one of the six specified numeric values.

#### Boolean Literal Types
These restrict a variable to either true or false:
```
let isDone: true;
```
In this case, isDone can only be true.

Literal types are incredibly valuable because they provide compile-time checks, ensuring that your code is more reliable and less error-prone. 

They also enhance code readability, as anyone reading the code can immediately understand the allowed values for a variable.

Additionally, literal types are often used in conjunction with union types, allowing you to create complex type structures that represent various scenarios in your application.

**[Back To The Top](#Overview-of-the-Section)**
#
### Type Aliases Custom Types

Type aliases, also known as custom types in TypeScript, are a powerful feature that allows you to create your own custom data types by combining existing types. 
 
These custom types make your code more readable, maintainable, and provide strong typing, which helps catch errors at compile-time.

Type aliases are typically created using the type keyword, and they can be used to define various types of structures:

#### Basic Types
You can create an alias for basic types like strings, numbers, or booleans. For example:
```
type MyString = string;
type Age = number;
type IsEmployee = boolean;
```

#### Object Types
Type aliases are commonly used to describe complex object structures. For instance:
```
type Person = {
  name: string;
  age: number;
};

type Point = {
  x: number;
  y: number;
};
```
#### Union Types
You can combine multiple types using union (|) to create more flexible type definitions. For instance:
```
type Result = string | number;
type Status = "success" | "failure";
```

#### Intersection Types
With intersection (&), you can merge multiple types into one. This is useful for combining features from different types:
```
type Admin = {
  role: "admin";
  permissions: string[];
};

type Employee = {
  role: "employee";
  department: string;
};

type AdminEmployee = Admin & Employee;
```

**[Back To The Top](#Overview-of-the-Section)**
#

### Function Return Types and "void"