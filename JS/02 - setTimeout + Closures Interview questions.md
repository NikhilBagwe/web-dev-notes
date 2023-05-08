## Q.1 : How below code is executed ?

```js
function x() {
  var i = 1
  setTimeout(function () {
    console.log(i)
  }, 2000)

  console.log("Hello")
}

x()
```

- JS dosen't wait for anyone.
- Thus, 'Hello' is logged first and then after 2 sec value of 'i' is printed.
- Here setTimeout takes the callback function and attaches a timer of 2000 ms to it and stores it somewhere and JS proceeds with further execution.
- Once the timer expires, the function is put into the callstack and then executed.

## Q.2 : Print 1,2,3... so on after 1s,2s,3s... respectively using setTimeout and closure

- Below code using 'let' and w/o closure will work fine.

```js
for (let i = 1; i < 5; i++) {
  setTimeout(function () {
    console.log(i)
  }, i * 1000)
}
```

- On using Closure with 'var', code behaves strangely:

```js
function x() {
  for (var i = 1; i < 5; i++) {
    setTimeout(function () {
      console.log(i)
    }, i * 1000)
  }
}

x()

// o/p : 5 5 5 5
```
- So all the setTimeouts reference to the same 'i' variable whose value currently is '5'.
- Since JS dosen't wait, the loop runs for 5 times and value of 'i' becomes '5'. Thus '5' gets printed 4 times.
- So to solve this problem use 'let' ans it has block scope.
- So for every loop a new copy of 'i' will be created. So a new closure is formed with new copy of 'i'

## Q.3: For above Q.2, you have to solve problem only using 'var'

- Solution : We have to create a new copy of 'i' using closure.

```js
function x() {
  for (let i = 1; i < 5; i++) {
    function close(x) {
      setTimeout(function () {
        console.log(x)
      }, x * 1000)
    }

    close(i)
  }
}

x()
```

- So everytime the close() func is called a new copy of 'i' is made
- Previously the problem was we were referring the same memory space. 
- But now, thanks to closure we are creating a new copy of 'i' everytime setTimeout was called.














5
