## Intro :

- A special syntax to work with promises in a more comfortable fashion.
- async : The word “async” before a function means one simple thing: a function always returns a promise.
- await : The keyword await makes JavaScript wait until that promise settles and returns its result.
- It is a more elegant syntax of getting the promise result than "promise.then". And, it’s easier to read and write.

## Code example :

- From below example it is clear, that using async/await we can write more readable and clean code.

```js
function getData() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve('done')
    }, 1000)
  })
}

// New way using async/await
async function start() {
  const result = await getData() // ***
  console.log(result)
}

// Old way
function start2() {
  getData().then((result) => console.log(result))
}

start()
start2()
```
- In above example, the execution of function 'start()' pauses at *** line and resumes when the promise settles,
 with result becoming its result. So the code above shows “done” in one second.
 
 ## Points to remember :
 
 1. Any function can be converted to async.

```js
const me = {
  async hello() {
    console.log("hi")
  },
}

me.hello() // hi
```

2. All async functions return a Promise.

```js
const me = {
  async hello() {
    console.log("hi")
  },
}

console.log(me.hello())  // Promise {<fulfilled>: undefined}
```
 
3. async and await must be used together but "JS modules and Chrome DevTools are an Exception for that".
 
 
 
 
 
 
 
 
