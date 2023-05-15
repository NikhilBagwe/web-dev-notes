## Intro :

- OOP is a programming paradigm or style.
- Using OOP we can hide all the important data and complex logic from end user and only expose the required functionalities.
- Also provides modularity to code.

## Constructor function :

- Name of this function should start with Capital letter.

```js
function BankAccount(customerName, balance) {
  // defining properties
  this.customerName = customerName
  this.accountNumber = Date.now()
  this.balance = balance

  // methods - public interface to access private data
  this.deposit = function (amount) {
    this.balance += amount
  }
}
```
## Creating Object :

```js
const johnAccount = new BankAccount("John", 1000)

console.log(johnAccount)
```
- Every object will be stored in different memory space.
- Thus any changes we make in one object wont affect the rest of objects.

## Accessing and changing properties :

```js
johnAccount.balance = 40000

console.log(johnAccount)
```
- But we should avoid what we did above by using Encapsulation feature of OOPs.
- If anyone can access bank data easily, it will be a problem.


















