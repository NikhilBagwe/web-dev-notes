## Intro :

- Promises are used in JS to handle async operations.
- As we seen the problem of Inversion of control exists while using Callbacks.
- So to solve this problem we use Promise.

## Promise :

- Instead of passing a callback function, now our function will return a promise.
- We can assume Promise to be an empty object with some data value in it. 
- The data value will hold whatever the function returns to us.

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



























