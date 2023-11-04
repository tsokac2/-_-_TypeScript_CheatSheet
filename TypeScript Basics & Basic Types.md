<h1 align="center">TypeScript Basics & Basic Types</h1>

### Overview of the Section
* **[TypeScript Core Types](#TypeScript-Core-Types)**
* **[TypeScript Types vs JavaScript Types](#TypeScript-Types-vs-JavaScript-Types)**
* **[Difference between Runtime and Development](#Difference-between-Runtime-and-Development)**

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