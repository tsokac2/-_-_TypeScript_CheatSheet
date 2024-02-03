<h1 align="center">Next Generation JavaScript & TypeScript</h1>

### Overview of the Section
* **["let" and "const"](#let-const)**


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