## map() :

- It is used to transform an whole array.
- When we have to transform each and every value of array and get a new array we use map() on it. 
- It is a HOF.

```js
const arr = [5, 1, 3, 2, 6]

function double(x) {
  return x * 2
}

// const output = arr.map((num) => num * 2)
const output = arr.map(double)

console.log(arr)
console.log(output)
```

## filter() :

- It is used to filter values from an array.
- Eg: filter out all odd or even values out of array, values greater than 4, etc.

```js
const arr = [5, 1, 3, 2, 6]

// filter odd values
function isOdd(x) {
  return x % 2
}

const output = arr.filter(isOdd)
```

## reduce() :

- It is used when we want to reduce the array to single value eg (max, min, avg, sum, difference etc).
- reduce() takes 2 arguments : Callback function and Initial value of 'acc'
- reduce() takes 2 parameters in callback function : Accumulator and Current.
- Accumulator stores the final result like sum of all values or max element.
- Current is the current value the callback function is been called upon i.e arr[i] 

```js
const arr = [5, 1, 3, 2, 6]

const output = arr.reduce(function (acc, curr) {
  acc += curr
  return acc
}, 0)

console.log(output)
```












