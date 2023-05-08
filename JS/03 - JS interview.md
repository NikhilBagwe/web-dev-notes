## 1. Explain closure and Double Parenthesis example

- A function bundled with it's lexical scope.
- Each function in JS has access to its lexical environment.
- So even when 'inner()' function is executed in other scope, it still remains its lexical env where it was originally present in the code.

```js
function outer() {
  var a = 10
  function inner() {
    console.log(a)
  }

  return inner
}

outer()() // similar to "var z = outer(); z();"

```
- Even when 'var a = 10' is moved down, it will still work.

```js
function outer() {
  function inner() {
    console.log(a)
  }
  var a = 10

  return inner
}

outer()()
```

## 2. Can we use 'let' declarations to form a closure.

- Yes, it will still work the same way.
- inner() will still form a closure.

```js
function outer() {
  let a = 10
  function inner() {
    console.log(a)
  }

  return inner
}

outer()()

```

## 3. Does the parameter we pass in outer() func become part of closure.

- Yes, since inner() func forms a closer with its outer() env and param 'b' is also part of it.

```js
function outer(b) {
  let a = 10
  function inner() {
    console.log(a, b)
  }

  return inner
}

outer("Hello")() // 10 'Hello'
```























0
