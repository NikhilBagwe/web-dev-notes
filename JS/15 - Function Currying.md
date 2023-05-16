## Function Currying :

- Currying in JavaScript transforms a function with multiple arguments into a nested series of functions, each taking a single argument.

## Function Currying using bind() :

- In Function Currying using bind(), we first made the copy of multiply() function and then we created more methods out of it by presetting some arguments in them.

```js
let multiply = function (x, y) {
  console.log(x * y)
}

// multiplyByTwo() is exactly the copy of 'multilply()' made using bind().
// Here we have set the value of 'x' to 2.
let multiplyByTwo = multiply.bind(this, 2)

// Thus, now we have to just pass value of 'y' to multiplyByTwo() and it works.
multiplyByTwo(5)

let multiplyByThree = multiply.bind(this, 3)
multiplyByThree(5)
```

- Suppose if we passed both values for 'x' and 'y', anything passed in multiplyByTwo() will be ignored.

```js
let multiplyByTwo = multiply.bind(this, 2, 3)

multiplyByTwo(5) // 6
```

## Currying using Function Closures :

- Here we return a function forming closure as shown below.

```js
let multiply = function (x) {
  return function (y) {
    console.log(x * y)
  }
}

let multiplyByTwo = multiply(2)
multiplyByTwo(3)

multiply(2)(5)

```















0
