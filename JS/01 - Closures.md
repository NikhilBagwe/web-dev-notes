## Intro :

```js
function x() {
  var a = 7
  function y() {
    console.log(a)
  }
  y()
}

x()
```

- In above example, y() first tries to find 'a' inside it's local memory store. 
- Since it's not present their, it goes to find 'a' in it's lexical parent's memory where it finds 'a=7'.
- Thus it logs '7' as o/p.
- This is what a Closure is.
