# typescript-best-practice
In this documentaion i will try to give the best practice to write typescript clean code

## 1. Use correct data type annotation ( avoid ‘any’ )
Try to avoid any type, insted of that try to use the right type.

example:
```javascript
const name: string = 'Max'
const age: number = 30
```

## 2. Use ‘let’ instead of ‘var’
let has been added in ES6. The main deferent between var and let is:

'var' initilized a global variable like that:

```javascript
var name = "John"; // global scope variable 

function getName() {
    var name = "Anne"; // local scope variable
    console.log(name) // Anne
}
console.log(name) // Anne
```
Here an error will be thown 
> 'name' was also declared here.

Using let give the user the ability to diferent between global variable and block variable

```javascript
let name = "John";
if (true) {
    let name = "Anne";
    console.log(name); // "Anne"
}
console.log(name); // "John"
```

## 3. Use ‘const’ for constants
Use always const to define constants variables. The constants variables are the variables that cannot be updated. They still always constants

```javascript
const age = 30
const age = 31 // error, age cannot be updated
```

