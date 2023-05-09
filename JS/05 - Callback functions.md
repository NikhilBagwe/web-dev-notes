## Callback functions :

- The function that we pass into another function as an argument is called as Callback function.
- Since functions in JS are First class citizens, it is possible.
- They give us access to the whole asynchronous world in a synchronous single-threaded language.

```js
function x(y){

}

x(function y() {})
```

- In above example, func y() is passed as callback func to x(). 
- Now it is upto x() when to call y(). It can call it later in the code also. Thus it is called as 'Callback function'.
- Callback functions are used in setTimeouts. Here JS calls the passed callback func asynchronously after the timer is finished.

## Callstack :

- JS has only one callstack also called as 'Main thread'.
- Everything which is executed on the page is executed only through callstack.
- The callstack must never be blocked.
- Since JS has callback/ first class funcs, we can perform asynchronous operations.
