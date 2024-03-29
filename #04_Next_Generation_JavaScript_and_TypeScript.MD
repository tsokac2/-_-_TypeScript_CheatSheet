<h1 align="center">Next Generation JavaScript & TypeScript</h1>

### Overview of the Section
* **["let" and "const"](#let-const)**
* **[Arrow Functions](#arrow-functions)**
* **[Default Function Parameters](#default-function-parameters)**
* **[The Spread Operator (...)](#spread)**
* **[Array & Object Destructuring](#destructuring)**


### <a name="let-const">"let" and "const"</a>

Because ``let`` and ``const`` introduced a new concept called block scope, which means a variable or constant is always available in the block in which you define it or in any lower blocks.

#### ``let`` & ``const``
```
const age = 20;
if( age > 15){
    let x = true;
}
console.log(x) //undefined - fails since let(or const) is outside the if block
console.log(age) //true since const is outside the if block
```
#### ``var``
```
var age = 20;
if( age > 20){
    var x = true;
}
console.log(x) //true since var is outside the if block
```
In JavaScript, variables declared with var are function-scoped, not block-scoped like variables declared with let or const since ES6.

**[Next JavaScript compat-table](https://compat-table.github.io/compat-table/es6/)**

#
**[Back To The Top](#Overview-of-the-Section)**

### Arrow Functions
```
const add = (a:number, b:number) => {
    return a + b;
};
console.log(add(2,5));
```
**Example with one expresion**
``const add = (a:number, b:number) => a + b;``

**Example with defining two types - 'number'|'string'**
``const printOutput: (a:number | string) => void = output => console.log(output)``

#
### Default Function Parameters

Default they need to be last in the list of arguments
```
const add  = (a: number, b:number = 1) => a + b
console.log(add(5); // Returns 6)
```
#
### <a name="spread">The Spread Operator (...)</a>
```
const person = {
  name: "Tom",
  age: 30
}
const newPerson = {...person}; // Perfect copy of a original object
console.log(newPerson);
```
#
###  Rest Parameters
Rest parameters, a really useful feature for accepting an unlimited amount of arguments.

```
const add  = (...numbers: number[]) => {
  return numbers.reduce((curResult, curValue) => {
    return curResult + curValue;
  }, 0);
};

const addNumbers = add(5, 10, 2, 3.7);
console.log(addNumbers);
```
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="destructuring">Array & Object Destructuring</a>
Array and Object destructuring are features in JavaScript that allow you to extract values from arrays or properties from objects into distinct variables with a more concise and readable syntax.

**Array Destructuring**:
```
const hobbies = ["Coding", "Movie", "Tom"];
const [hobbi1, hobbi2, ...remaningHobbies] = hobbies;
console.log(...remaningHobbies); // Returns "Tom"
```

**Object Destructuring**:
It lets you extract properties from an object and assign them to variables with the same name.
```
const person = { name: 'Tomislav', age: 30, location: 'Dublin' };
const { name, age, location } = person;

console.log(name);     // 'Tomislav'
console.log(age);      // 30
console.log(location); // 'Dublin'
```
**[Back To The Top](#Overview-of-the-Section)**