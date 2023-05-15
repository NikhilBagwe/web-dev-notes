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

```js
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





















4
