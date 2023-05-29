## 1. Why is JS weakly/dynamically typed language ?

- We don't declare the data type while declaring variable. Thus, JS is weakly typed.
- JS dosen't run on a system like C, C++, etc. , it is built to run on the browser. So it dosen't directly interacts with the system hardware.
- JavaScript is a dynamically typed language, meaning that variable types can change during runtime. 
- This flexibility enables JavaScript to handle a wide range of scenarios and simplifies certain programming tasks.

## 2. Why is JS single-threaded ?

- Single-threaded means code is executed line by line, one line at a time.
- Javascript is single-threaded because, originally, it was only a web browser scripting language created to serve the needs of a single user
 on a single window of the browser, eliminating the need for multithreading
 
 ## 3. What are closures and their Real use cases ?
 
 - A function having access to lexical enivironment of outer function is called a closure.
 - Use case : Fuction Currying, Tracking DOM State / Styles, Higher-Order Functions

## 4. Advantages of React over VanillaJS

- Reconcilation : the process by which React updates the UI to reflect changes in the component state
- We get pre-built features such as State management, Context API in React
- Component based architecture

## 5. Diff. between class and function component.

## 6. What is JSX? advantage of using it over HTML

## 7. What is interpreated language ?

- An interpreted language is one that does not require compiling into machine language. 
- It is executed by an interpreter who reads the source code and converts it into a form that is directly executed. 
- The interpreter executes code line by line which makes JavaScript synchronous in nature.

## 8. What is Promise and promise.all ?

- Promise helps us to perform asyncrohnous tasks in JS such an API call......
- promise.all() helps us to perform 2-3 asynchronous tasks concurrently.
- Explain how it works and is executed BTS ?
- Parallel concurrency - Suppose there are 3 promises to be executed concurrently. Then concurrency dosen't mean that all 3 are executed at same time. First promise is sent for exec., then second one and so on. Once all are sent then the execution happens parallely. Sending them parallely at the same time is not possible.
- Why parallel is not possible ? : Since JS is single-threaded. At a time only 1 process can be executed.

## 9. Why is Event Loop necessary/importance ?

- Gives JS the power to perform asynchronous tasks....

## 10. Suppose there are 3 statments - 1st and 3rd are console.log() and 2nd is an setTimeout() for 3 sec. Explain with event loop how this are executed.

- As JS is synchronous it will execute 1st stmt console.log().
- Then it sees a setTimeout which is async task, so it pushes it in the macro task queue and then execute the 3rd stmt console.log().
- After 3 sec Event loop will check if the main thread is empty or not and then push code inside of setTimeout into it.

## 11. In promise.all there has to be a process that is waiting for all the promises to get resolved and then club them into 1 array and return it. So were exactly this waiting process happens in Event loop ?

## 12. Any point where you think React is slower than HTML and Vanilla JS.

## 13. Higher Order Component in React with example/use case.

- Takes an component as parameter and returns an updated component.

## 14. Why hooks are necessary in React Functional components ?

- Gives it the power of class based components had, such as state (Functional components were stateless).
- Given life cycle methods to Functional components.

## 15. When to use a Custom hook ?

- Whenever there is a requirement of reusability of logic and in it you also need React capabilities such as State. That time we use hooks.

## 16. In a project made using Functional components, every function is returning some JSX. So where is the mechanism to render/re-render that JSX onto the screen present ?

- 









#
