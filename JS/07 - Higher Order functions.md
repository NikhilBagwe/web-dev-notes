## Higher Order functions :

- A function that takes another function as argument or returns a function is called Higher Order function.

```js
function x(){
  console.log('hi');
}

// y() is Higher order function and x() is the callback function
function y(x){
  x()
}
```

## How to optimize code : DRY principle

- Normal code : Calculate Area of circle

```js
const calulateArea = function (radius) {
  const output = []
  for (let i = 0; i < radius.length; i++) {
    output.push(Math.PI * radius[i] * radius[i])
  }
  return output
}

console.log(calulateArea(radius))
```

- Optimized code : Now even if we have to calculate Circumference, we simply have to write a new logic function and reuse the same calculate() function.

```js
const radius = [3, 1, 2, 4]

const area = function (radius) {
  return Math.PI * radius * radius
}

const calulate = function (radius, logic) {
  const output = []
  for (let i = 0; i < radius.length; i++) {
    output.push(logic(radius[i]))
  }
  return output
}

console.log(calulate(radius, area))
```

- We have abstracted our code into smaller functions and each function has it's responsobility.
- What we did is part of Functional programming. Reusability, modularity, using function into another function is part of it.
- So now 'calculate()' is a HOF and 'area()' is callback function.















