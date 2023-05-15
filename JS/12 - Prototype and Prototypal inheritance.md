## Intro :

- The concept of inheritance is a bit different in JS as compared to other languages.
- Let us create an array :

```js
let arr = ["nikhil", "raj", "yash"]
```
- Now when you write 'arr.' , you get to access a lot of different properties and built-in functions.
- But we never defined them.
- Similarly, we can experience the same in case of JS object.
- Thus, this where Prototypes come into picture.

## Prototype :

- When we create a JS object, JS engine automatically without even letting you know attaches your object with some hidden properties and functions.
- Similarly in case of a Function and Variable we get access to lots of built-in funcs and props automatically.

```js
function fun(){

}
```
- So what happens is that when we create a JS object, JS engine automatically puts the hidden properties/methods into an object and attaches to your original object.
- So to access that hidden object we can do : 

```js
console.log(arr.__proto__)
```
- "__proto__" is the obj where JS is putting all the functions and methods.
- Whatever we create in JS gets attached with this "__proto__" obj.
- 'arr.__proto__' is similar to  'Array.prototype'. If you log them, you will see both of them are same i.e contain same values, functions,etc.
- It is because even 'arr.__proto__' is an object and each and every obj in JS has prototype.
- So prototype of 'arr.__proto__' is Object prototype.

### In case of array  :

```js
let arr = ["nikhil", "raj", "yash"]

// Both are Similar
console.log(arr.__proto__)
console.log(Array.prototype)

// prototype of 'arr.__proto__' is Object prototype
console.log(arr.__proto__.__proto__)
console.log(Object.prototype)

// prototype of 'Object prototype' is null
console.log(arr.__proto__.__proto__.__proto__)
```
- This is what we call Prototype chain.
- Whenever we create an array, it has it's prototype 'Array.prototype'. Then 'Array.prototype' obj has it's own prototype i.e 'Object.prototype'. Then prototype of 'Object.prototype' is null which is end of the chain.

### In case of function  :

```js
function fun() {}

console.log(fun.__proto__)
console.log(Function.prototype)

console.log(fun.__proto__.__proto__) // Object prototype

console.log(fun.__proto__.__proto__.__proto__)  // null
```

## NOTE : Now we can understand that everything in JS is an object.

## NOTE : Never modify the '__proto__' prototype of an object directly like assign new obj to it. It causes a huge performance issue.

## Adding new function to Function prototype :

```js
Function.prototype.myFunc = function (){
  console.log('New func');
}
```
- Now all the functions that we define in our code will have access to above 'myFunc' as now it's part of 'Function prototype'.

## NOTE : __proto__ is written as the way it is, to diffferentiate it from others, a sort of naming convention.





















