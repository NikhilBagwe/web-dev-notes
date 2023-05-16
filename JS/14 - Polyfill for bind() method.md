## Polyfill :

- A polyfill is a piece of code used to provide modern functionality on older browsers that do not natively support it.
- Suppose if your old browser dosen't has bind() in it. So in this case we have to write our own bind() function.

## Polyfill for bind() :

- Our own implementation of bind().

### Working of traditional bind() :

```js
let name = {
  firstname: "Nikhil",
  lastname: "Bagwe",
}

let printFullName = function (hometown, country) {
  console.log(`${this.firstname} ${this.lastname} from ${hometown}, ${country}`)
}

let printMyName = printFullName.bind(name, "Tokyo", "Japan")

printMyName()
```

### My implementation of bind() :

- On observing bind(), we can see that every function in JS has access to bind(). 
- Thus we need to add our mybind() function to "Function.prototype".

```js
Function.prototype.mybind = function (){
  
}
```
- bind() returns a function which can be later invoked, so our mybind() should also return.

```js
Function.prototype.mybind = function (){
  return function (){
    
  }
}
```
- Inside the returned function, we want to call the same function on which mybind() was called i.e printFullName().
- So inside the mybind(), the 'this' points to the printFullName(). 
- Store 'this' in a variable and use call() on it and inside it pass the reference to obj on which printFullName() needs to be called.

```js
Function.prototype.mybind = function (...args) {
  let obj = this
  return function () {
    obj.call(args[0]) // out of the multiple arguments passed, the first one will be name of the obj.
  }
}
```

### Complete code : Basic implementation

```js
let name = {
  firstname: "Nikhil",
  lastname: "Bagwe",
}

let printFullName = function () {
  console.log(`${this.firstname} ${this.lastname}`)
}

Function.prototype.mybind = function (...args) {
  let obj = this
  return function () {
    obj.call(args[0]) // out of the multiple arguments passed, the first one will be name of the obj.
  }
}

let printName = printFullName.mybind(name)

printName()
```

## But there is still a problem with multiple arguments :

- When we pass multiple arguments, only one is passed.
- So we have to extract them and pass.
- Since now we are passing an array of args,  we have to use apply() instead of call()

```js
let printFullName = function (hometown) {
  console.log(`${this.firstname} ${this.lastname} from ${hometown}`)
}

Function.prototype.mybind = function (...args) {
  let obj = this,
    params = args.slice(1) // extracting the remaining arguments from args array and storing them in params array.

  return function () {
    // use apply() simce we pass array
    obj.apply(args[0], params)
  }
}

let printName = printFullName.mybind(name, "Mumbai")

printName()
```

## But now suppose an argument needs to be passed in printName() function, our solution won't work.

- Solution : Arguments passed in printName() function will be recived in the returned function inside mybind() as below.
- Also since we were already passing params array, now we will need to concatenate the params array with the 'args2' and send them together.

```js
Function.prototype.mybind = function (...args) {
  let obj = this,
    params = args.slice(1) 

  return function (...args2) {  // the args passed in printName() are received here.
    obj.apply(args[0], [...params, ...args2]) // here we create a larger array by concatenating 'params' and 'args2'
  }
}
```

## Final Code :

```js
let name = {
  firstname: "Nikhil",
  lastname: "Bagwe",
}

let printFullName = function (hometown, state, country) {
  console.log(
    `${this.firstname} ${this.lastname} from ${hometown}, ${state}, ${country}`
  )
}

Function.prototype.mybind = function (...args) {
  let obj = this,
    params = args.slice(1)

  return function (...args2) {
    obj.apply(args[0], [...params, ...args2]) 
  }
}

let printName = printFullName.mybind(name, "Mumbai")

printName("Maharashtra", "India") // Even works for multiple params

```









