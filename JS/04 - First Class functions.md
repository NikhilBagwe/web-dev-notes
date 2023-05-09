## Function Statement :

```js
function a() {
  console.log("Function statement")
}
```

## Function Expression :

- In JS, a function acts like value.
- So we can initialize a function to a variable.

```js
var b = function () {
  console.log("Function Expression")
}
b()
```

## Major difference between Function Statement & Expression - Hoisting :

```js
a() // Function statement
b() // Uncaught TypeError: b is not a function

function a() {
  console.log("Function statement")
}

// Func exp

var b = function () {
  console.log("Function Expression")
}
```
- Here 'var b' is treated like another variable and undefined is assigned to it.
- So on trying to call b(), we get error.

## Function Declaration :

- Function Statement is also known as Function Declaration.
- Just another jargon word.

## Anonymous function :
 
- A function with no name/identity.
- Type of a function statement.
```js
function (){
    console.log('hi');
}
```
- If it is declared as above will give = Uncaught SyntaxError: Function statements require a function name
- Anonymous functions are used where functions are used as values to be assigned to a variable. Eg: Function expression

## Named Function expression :

- Instead of assigning an Anonymous func to a variable, a function with a name is assigned.

```js
var a = function b() {
  console.log("hi")
}

a()
```
### Corner case in Named Function expression :

- If I try calling the assigned function directly, then it will throw Referenece error.
```js
var a = function b() {
  console.log("hi")
}

b()  // uncaught ReferenceError: b is not defined
```

## Parameters and arguments :

```js
var a = function (param1, param2) {
  console.log(param1 + param2)
}

a("hello", " world")
```
- In above example, param1 and param2 are parameters. They act as local variables inside function scope i.e they can't be accesed outside.
- The values passed inside the function "a("hello", " world")" are called arguments.

## First Class functions :

- It is the ability of functions to be used as values, can be passed as arguments, assigned to a variable and a function returning a function all together is known as First class functions.
- In JS we can pass functions as arguments to a function i.e the function act as a value.

```js
var a = function (param1) {
  console.log(param1)
}

a(function () {})
```
- We can also return a function from a function.

```js
var a = function (param1) {
  return function () {}
}

console.log(a())
```

## First Class Functions are also called as First Class Citizens. Both mean the same thing.

### NOTE : If we use let and const intead of var, the let/const rules will be applied on functions.


















