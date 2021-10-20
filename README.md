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

## 4. Use tuples for fixed length arrays
In certian setuations you have to define an array with constant length. The problem here is: there is no way to give a length for an array
```javascrpt
const testNumArray: number[] = [5] // 5 here will we define as first element => testNumArray[1] = 5
```
To avoid this problem so you can pass more than enough data to your array, use Tuples

For example: you want to define an array with just two elements
```javascript
let testNumArray: number[number, number] = [1, 2]
testNumArray = [1, 2, 3] // error
```

## 5. Use type aliases in repetitive data types
If there is objects with the same types of data structure, define these types of data structure as one new Type

Example: we have two objects:
```javascript
const audi: {topSpeed: number, ps: number} = {topSpeed: 220, ps: 150}
const vw: {topSpeed: number, ps: number} = {topSpeed: 200, ps: 125}
```
Better way to write that code is to define a new CarDetails Type:
```javascript
type CarDetails = {topSpeed: number, ps: number}
const audi: CarDetails = {topSpeed: 220, ps: 150}
const vw: CarDetails = {topSpeed: 200, ps: 125}
```

# JavaScript tips in general

## 1. Avoid "await" inside loops
Try not to use await inside a loop

#### Bad
```javascript
for (const element of elements) {
    await this.dummyFunction(element)
}
```
#### Good
```javascript
const promisesArray = []
for (const element of elements) {
    promisesArray.push(this.dummyFunction(element))
}
await Promise.all(promisesArray)
```
