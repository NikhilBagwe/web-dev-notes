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
- Here b() is treated like another variable and undefined is assigned to it.
- So on trying to call it we get error.

















0
