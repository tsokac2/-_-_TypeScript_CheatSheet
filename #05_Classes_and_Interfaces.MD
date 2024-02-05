<h1 align="center">Classes & Interfaces</h1>

### Overview of the Section
* **[What are Classes?](#classes)**
* **[Constructor Functions & The "this" Keyword](#this)**
* **["private" and "public" Access Modifiers](#privat)**
* **["readonly" Properties](#readonly)**


### <a name="classes">What are Classes?</a>

What's Object-oriented Programming (OOP)?

![OOP](https://github.com/tsokac2/-_-_TypeScript_CheatSheet/blob/main/src/02.JPG)

### Classes & Instances

![classes](https://github.com/tsokac2/-_-_TypeScript_CheatSheet/blob/main/src/03.JPG)

**Classes**:
- Think of them as blueprints or templates. They define the properties and methods (functions) that objects of that type will have.
- Classes themselves are not objects. They serve as a reference for creating objects.

**Instances**:
- These are the actual objects created from a class. They each have their own set of properties and methods inherited from the class.
- You create an instance using the new keyword followed by the class name.
- Each instance has its own unique identity and data. Even though they share the same blueprint, their properties and method calls can have different results.

Here are some resources for further learning:

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
**Output in the console**:
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

### <a name="privat">"private" and "public" Access Modifiers</a>

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

### <a name="readonly">"readonly" Properties</a>


#
**[Back To The Top](#Overview-of-the-Section)**