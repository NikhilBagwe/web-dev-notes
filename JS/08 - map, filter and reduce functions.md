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
