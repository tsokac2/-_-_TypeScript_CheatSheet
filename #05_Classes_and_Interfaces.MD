<h1 align="center">Classes & Interfaces</h1>

### Overview of the Section
* **[What are Classes?](#classes)**
* **[Creating a First Class](#creating-a-first-class)**
* **[Constructor Functions & The "this" Keyword](#this)**
* **["private" and "public" Access Modifiers](#privat-public)**
* **[Inheritance](#inheritance)**
* **[Overriding Properties & The "protected" Modifier](#protected)**
* **[Getters "get" and  Setters "set"](#get-set)**
* **[Interface](#interface)**
* **[Using Interfaces with Classes](#interface-classes)**
* **[More on TS Interfaces](https://www.typescriptlang.org/docs/handbook/2/objects.html)**

### <a name="classes">What are Classes?</a>
What's Object-oriented Programming (OOP)?

![OOP](https://github.com/tsokac2/-_-_TypeScript_CheatSheet/blob/main/src/02.JPG)

#### Classes & Instances

![Classes](https://github.com/tsokac2/-_-_TypeScript_CheatSheet/blob/main/src/03.JPG)

#### Classes:

- Think of them as blueprints or templates. They define the properties and methods (functions) that objects of that type will have.
- Classes themselves are not objects. They serve as a reference for creating objects.

#### Instances:

- These are the actual objects created from a class. They each have their own set of properties and methods inherited from the class.
- You create an instance using the new keyword followed by the class name.
- Each instance has its own unique identity and data. Even though they share the same blueprint, their properties and method calls can have different results.

#### Here are some resources for further learning:

- MDN Web Docs: **[Link](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/class)**
- A brief introduction to Classes and Instances in JavaScript: **[Link](https://tutorial.techaltum.com/javascript-class.html)**
- The Complete Guide to JavaScript Classes: **[Link](https://dmitripavlutin.com/tag/javascript/)**

#
**[Back To The Top](#Overview-of-the-Section)**

### Creating a First Class
```
class Department {
    name: string;

    constructor(n: string) {
        this.name = n;
    }
}
const accounting = new Department("Accounting");
console.log(accounting);
```

**Output in the console:**

```
Department {name: 'Accounting'}
name: "Accounting"
[[Prototype]]: Object
```
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="this">Constructor Functions & The "this" Keyword</a>
```
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.greet = function() {
    console.log("Hello, my name is " + this.name);
  };
}

const person1 = new Person("Alice", 30);
person1.greet(); // Output: "Hello, my name is Alice"

const person2 = new Person("Bob", 25);
person2.greet(); // Output: "Hello, my name is Bob"
```
In this example, the ``Person`` constructor function creates objects with ``name`` and ``age`` properties, and a ``greet`` method. Each object (``person1`` and ``person2``) has its own ``name`` and ``age`` values, and calling ``greet`` on them prints their unique names.
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="privat-public">"private" and "public" Access Modifiers</a>
```
class Department {

    name: string;
    private employees: string[] = []; // not accessible outside the calss scope

    constructor(n:string){
        this.name = n;
    }
}
```
- The ``private`` keyword before ``employees`` ensures that the list of employees can only be accessed and modified within the class itself, promoting data protection.
- This class structure helps organize employee information within departments and enforces data privacy.

#
**[Back To The Top](#Overview-of-the-Section)**

### Inheritance
Inheritance in JavaScript classes allows a new class (called a subclass or child class) to inherit properties and methods from an existing class (called a superclass or parent class).
This promotes code reusability and establishes hierarchical relationships between classes.

**Key concepts**:
- ``extends`` keyword: Used to create a subclass that inherits from a superclass.
- **Superclass**: The class being inherited from.
- **Subclass**: The class that inherits from the superclass.
- **Prototype chain**: A mechanism that JavaScript uses to look for properties and methods in inherited classes.

```
class Animal {
  constructor(name) {
    this.name = name;
  }

  eat() {
    console.log(`${this.name} is eating.`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Calls the constructor of the superclass
    this.breed = breed;
  }

  bark() {
    console.log(`${this.name} the ${this.breed} barks!`);
  }
}

const myDog = new Dog("Fido", "Labrador");
myDog.eat();   // Output: Fido is eating. (Inherited from Animal)
myDog.bark();  // Output: Fido the Labrador barks! (Specific to Dog)
```

**Key points**:
- The subclass inherits all properties and methods from the superclass.
- The subclass can add its own properties and methods.
- The subclass can override inherited methods by defining methods with the same name.
- The ``super`` keyword is used to call superclass methods or access superclass properties from within the subclass.
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="protected">Overriding Properties & The "protected" Modifier</a>

TypeScript's ``protected`` modifier limits a property's accessibility to the class that defines it and its subclasses.

```
class Person {
  protected age: number;

  constructor(age: number) {
    this.age = age;
  }
}

class Employee extends Person {
  getInfo() {
    return `Employee's age: ${this.age}`; // Can access protected property
  }
}
```
**Key Points**:
- Overriding properties in TypeScript involves redefining them in subclasses.
- The ``protected`` modifier restricts access to members within a class and its subclasses.
- These features are primarily for type checking and language features within TypeScript; transpiled JavaScript relies on prototype-based inheritance.
- Consider using TypeScript's private fields for stronger encapsulation within classes.
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="get-set">"get" and "set"</a>

#### Getters:
- Defined using the ``get`` keyword within a class definition.
- Act as functions that are called automatically when you try to read a property.

#### Setters:
- Defined using the ``set`` keyword within a class definition.
- Act as functions that are called automatically when you try to assign a value to a property.

#### Here's an example:
```
class Person {
  constructor(name) {
    this._name = name;
  }

  get name() {
    return this._name.toUpperCase(); // Customize returned value
  }

  set name(newName) {
    if (newName.length < 3) {
      throw new Error("Name must be at least 3 characters long"); // Validation
    }
    this._name = newName;
  }
}

const person = new Person("john");
console.log(person.name); // Outputs "JOHN" (using getter)
person.name = "Mary"; // Triggers setter for validation
console.log(person.name); // Outputs "Mary"
```
#
**[Back To The Top](#Overview-of-the-Section)**

### Interface

In TypeScript, an interface is a way to define a contract or a shape for an object. 

It allows you to specify the structure of an object, including the types of its properties and methods. 

#### Declaration:
You declare an interface using the ``interface`` keyword, followed by the interface name.
```
interface Person {
    name: string;
    age: number;
    greet(): void;
}
```

#### Implementing an Interface:
Once an interface is defined, you can implement it in a class. The class must adhere to the structure specified by the interface.
```
class Employee implements Person {
    name: string;
    age: number;

    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }

    greet() {
        console.log(`Hello, my name is ${this.name}.`);
    }
}
```
In summary, interfaces in TypeScript provide a way to define and enforce the structure of objects, ensuring that your code is more predictable and less error-prone. 
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="interface-classes">Using Interfaces with Classes</a>

In TypeScript, interfaces play a crucial role in defining contracts for classes. 
 
When you use interfaces with classes, you essentially establish a blueprint for the structure that a class must adhere to. 

```
interface Greetable {
  name:string;
  greet(phrase:string):void;
}

class Person implements Greetable {
  name: string; // every calass has to have "name"
  age = 30;

  constructor(n:string) {
    this.name = n;
  }

  greet(phrase: string): void { // every calass has to have greet() method
  console.log(phrase + ' ' + this.name)
  }
}

const res = new Person("Tomislav");
res.greet("Hi there: ");
```
**[Back To The Top](#Overview-of-the-Section)**