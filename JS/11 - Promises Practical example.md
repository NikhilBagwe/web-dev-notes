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

## Rejecting a Promise :

- Lets return 'false' in validateCart() and thus reject the promise.
- On doing so we get an error as follows :

```js
Uncaught (in promise) Error: Cart is not valid
    at index.js:9:19
    at new Promise (<anonymous>)
    at createOrder (index.js:4:14)
    at index.js:32:17

```
- So it shows that we have not handled our exception properly.
- So error handling must be performed.

## Error handling in Promise : catch()

- Similar to then(). 
- Using it we can attach a failure callback function to our Promise.
- then() is called when Promise is 'resolved' and catch() when it's 'rejected'.

```js
promise
  .then(function (orderId) {
    console.log(orderId)
  })
  .catch(function (err) {
    console.log(err.message)  // Cart is not valid
  })
```
- Even though there might be an error in any level of an promise chain, just one catch at the end will handle it.

## Promise chaining :

- After placing the order the customer must be directed to payment page.
- So now using the orderId we will proceed to payment.
- proceedToPayment() will return a Promise.

### NOTE : We must 'return' variables/promises for them to be accessable down the promise chain.

```js
createOrder(cart)
  .then(function (orderId) {
    console.log(orderId)
    return orderId // IMP! Whatever we return from here will be passed down to next then()
  })
  .then(function (orderId) {
    return proceedToPayment(orderId)
  })
  .then(function (paymentInfo) {
    console.log(paymentInfo)
  })
  .catch(function (err) {
    console.log(err.message)
  })
```
- Now when we returned the promsie proceedToPayment(orderId), instead of chaininhg the next .then() next to it, we wrote it on next line. We might have written it as follows:

```js
createOrder(cart)
  .then(function (orderId) {
    console.log(orderId)
    return orderId // IMP! Whatever we return from here will be passed down to next then()
  })
  .then(function (orderId) {
    return proceedToPayment(orderId).then(function (paymentInfo) {
      console.log(paymentInfo)
    })
  })

  .catch(function (err) {
    console.log(err.message)
  })
```
- But the code looks ugly. So promise api provides us the ability to return the promise from one then() and we can handle it in the next level of chain.

## Advanced Error handling :

- Up until now if any of the then() fails, everything after that fails.
- But what if we wanted to continue the execution from next then().
- Suppose in our example if createOrder() fails but we want to go to proceedToPayment().
- For that we will just move the catch() up the chain, next to the desired then().
- Now that catch() has only responsibility to check/handle the top of it.

```js
function validateCart(cart) {
  return false
}

createOrder(cart)
  .then(function (orderId) {
    console.log(orderId)
    return orderId // IMP! Whatever we return from here will be passed down to next then()
  })
  .catch(function (err) {
    console.log(err.message)
  })
  .then(function (orderId) {
    return proceedToPayment(orderId)
  })
  .then(function (paymentInfo) {
    console.log(paymentInfo)
  })
  .then(function () {
    console.log("No matter what, I will definitely be called")
  })
  
/* 
o/p :
 Cart is not valid
 Payment Successful
 No matter what, I will definitely be called
 */
```
- Now even if cart is not valid, still payment was successful.
- Using this, we can still continue execution of next then() methods after catch().















