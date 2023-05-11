## Intro :

- Promises are used in JS to handle async operations.
- As we seen the problem of Inversion of control exists while using Callbacks.
- So to solve this problem we use Promise.

# Promise :

- Instead of passing a callback function, now our function will return a promise.
- We can assume Promise to be an empty object with some data value in it. 
- The data value will hold whatever the function returns to us.

## Promise Example:

```js
const cart = ["shoes", "pants", "kurta"]

// creates an order and returns the order ID
const promise = createOrder(cart)
.
.
.
```
- In above example, when JS engine executes it, createOrder() returns a promise, basically an empty object. 
- Now the createOrder() api might take 5-6 seconds to execute. Until that point of time the promise object is empty.
- The code after that line will be continued to be executed.
- After 5-6 seconds, the empty obj will be filled with data automatically and thus, we will have the 'orderDetails' in it.

## then() :

- After we got the promise obj populated with 'orderDetails' data, we can append a callback function to it using '.then()'
- The callback func in then() will be automatically called once promise data is available.

```js
const promise = createOrder(cart)

promise.then(function (orderId) {
  proceedToPayment(orderId)
})
```

## What improvement we got on using Promise ? : Callbacks vs Promises

- Previously we were blindly trusting createOrder() to call the passed callback function whenever it wants.
- But in case of Promise, we are atttaching the callback function to it. When promise data is available in it's promise obj, then only the callback func is called automatically. This way we have the control of pgm with us.
- then() will call the callback func just once with 100% gurantee.
- Promise provides us with high level of Trust as it either can be in pending, fulfilled or rejected state.

## Promise example in Browser :

- fetch() is an API provided by browser to make external calls.
- By design, fetch() returns a Promise.
- There are 2 imp things in a Promise obj : 'State of a Promise : [[PromiseState]]' and 'Result of the Promise : [[PromiseResult]]'
- [[PromiseResult]] : Stores data that promise returns.
- [[PromiseState]] : Initially the promise is in 'pending' state. Once it gets the data, it's state changes to 'fulfilled' or 'rejected'

```js
const GITHUB_API = "https://api.github.com/users/akshaymarch7"

const user = fetch(GITHUB_API)

console.log(user)
```
- When you run the above code, you get a weird output as below :

```js
> Promise {<pending>}
    [[Prototype]]: Promise
    [[PromiseState]]: "fulfilled"
    [[PromiseResult]]: Response
```

- It shows the promise is 'pending' and on expanding the obj it shows PromiseState is 'fulfilled'.
- It is because at the time when 'console.log(user)' line is executed, the promise obj is in pending state as JS engine quickly executes everything and logs 
```js
Promise {<pending>}
```
- But eventually data comes back to promise obj after sometime and Google chrome thus shows you the current state of Promise as fulfilled.
- So when JS engine logs the Promise, it is in pending state and by the time you view it in console, it shows fulfilled state.
- Now you can get the received data using then()

```js
// Whatever needs to be done once we receive data in promise obj is wriiten inside then()
user.then((data) => console.log(data))
```

### NOTE : Promise objects are immutable. So we can pass them around the code, but no one can modify them.













