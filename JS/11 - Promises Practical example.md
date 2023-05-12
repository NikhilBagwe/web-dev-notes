## Ecommerce webiste example :

- We will create the 'createOrder' func from scratch which will return a promise.
- First we use Promise constructor to create a Promise.
- The constructor will take 2 parameters : resolve and reject
- resolve and reject are the 2 functions provided by JS to build promises. They were included in the design of Promise API.

```js
const cart = ["shoes", "pants", "kurta"]

function createOrder(cart) {
  const pr = new Promise(function (resolve, reject) {
    // Logic for createOrder api - includes validating cart, making calls to DB, etc.

    // If cart is not valid, reject the Promise by throwing error
    if (!validateCart(cart)) {
      const err = new Error("Cart is not valid")
      reject(err)
    }

    // Lets assume after making a DB call we get orderId
    const orderId = "12345"

    // If orderId is present than resolve() the promise
    if (orderId) {
      // Suppose if we make an API call which takes 5 seconds. So lets intriduce some fake delay
      setTimeout(function () {
        resolve(orderId)
      }, 5000)
    }
  })

  return pr
}

function validateCart(cart) {
  return true
}

const promise = createOrder(cart)
console.log(promise) // At this point it will show Promise as pending as it will take 5 seconds to resolve it.

promise.then(function (orderId) {
  console.log(orderId) // After 5 sec we get data into our promise obj and then orderId will be printed .
})
```
