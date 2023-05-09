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

## Event Listeners :

- An Event Listener, takes the event type and an callback function as params.
- The callback function is stored somewhere in the memory.
- When the event is triggered, the callback function automatically comes into the call stack and is executed.

## Forming closure with event listener :

- Attached click event listener to a button and keeping a track of how many times it is been pressed.

```js
function attachEventListener() {
  let count = 0
  document.getElementById("clickme").addEventListener("click", function xyz() {
    console.log("Button clicked", ++count)
  })
}

attachEventListener()
```

### NOTE : We must remove event listeners. They are very heavy as they consume lot of memory. As in  boave example we formed a closure with event listener. So even when the callstack is free, the memory to store 'count' value is still not garbage collected. Thus we must free them up so the variables can be garbage collected.
















