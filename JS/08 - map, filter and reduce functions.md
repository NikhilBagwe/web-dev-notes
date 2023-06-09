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

### Find sum of values :

```js
const arr = [5, 1, 3, 2, 6]

const output = arr.reduce(function (acc, curr) {
  acc += curr
  return acc
}, 0)

console.log(output)
```

### Find max value :

```js
const output = arr.reduce(function (max, curr) {
  if (curr > max) max = curr
  return max
}, 0)
```

## Tricky map() example : Print fullnames of users

```js
const users = [
  { firstName: "Akshay", lastName: "Saini", age: 26 },
  { firstName: "Donald", lastName: "Trump", age: 75 },
  { firstName: "Elon", lastName: "Musk", age: 50 },
  { firstName: "Deepika", lastName: "Padukone", age: 26 },
]

const fullNames = users.map((user) => `${user.firstName} ${user.lastName}`)

console.log(fullNames)
```

## Tricky reduce() example : Create an obj which keeps track of no. of people with different ages

- Desired o/p : {26 : 2, 75 : 1, 50 : 1}

```js
const output = users.reduce((acc, curr) => {
  // check if entry for the 'curr' age exists in 'acc'
  if (acc[curr.age]) {
    acc[curr.age] = ++acc[curr.age]
  }
  // if not present, create a new entry
  else {
    acc[curr.age] = 1
  }

  return acc
}, {})

console.log(output)
```

## Chaining filter() and map() :

- Create an array of first name of all people whose age is < 30 :

```js
const output = users
  .filter((user) => user.age < 30)
  .map((user) => user.firstName)
  
console.log(output)
```
- Similarly we can also use just 'reduce()' to acheive the same :

```js
const output = users.reduce((acc, user) => {
  if (user.age < 30) acc.push(user.firstName)
  return acc
}, [])
```

# NOTE : Study polyfills of map. filter, reduce








