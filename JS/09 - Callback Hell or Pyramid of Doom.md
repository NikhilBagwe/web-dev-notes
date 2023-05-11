## Intro :

- JS is a synchronous, single-threaded language and thus it can do only one thing at a time.
- But if we want a certain part of our code to be executed later, we use CALLBACK function.

```js
console.log("start")

setTimeout(() => console.log("Inside settimeout"), 2000)

console.log("end")
```
- Thus, in above example we successfully made our code Asynchronous.
- Asynchronous programming in JS exists because of Callbacks.

## Callback hell : Pyramid of Doom

- Lets take an example of Ecommerce website.
- For an order to be placed, there are 3 important steps to be followed : Create order, Make payment, then show order summary and so on.
- Suppose we have API for them and they are called accordingly.

```js
// Now it is responsibility of createOrder api to create a new order and call the passed callback function
api.createOrder(cart, function () {
  // It is responsibility of proceedToPayment api to complete the payment and call the callback function
  api.proceedToPayment(function () {

    api.showOrderSummary(function () {
      
      api.updateWallet()
    })
  })
})
```

- So we can see one callback func is present inside another callback and so on leading to callback hell.
- In large codebases, it becomes a big problem.

## Inversion of Control :

- Another problem we face while using callbacks is we lose our control on our code.

```js
api.createOrder(cart, function () {
  
  api.proceedToPayment()
})
```
- So in above example we gave the reponsibility of calling the payment api to createOrder. This is where we lost our control to call an important api such as payment api.
- We are blindly trusting createOrder api with it.
- Suppose if there was a bug in 'createOrder' api and our payment api was never called or it was called twice. 
- This is a big problem.














