## Absolute :

- After setting "position: absolute" of an element, the element gets removed from the entire document.
- So remaining elements behave as if that element never existed.
- top, bottom, left and right properties are unlocked after setting position prop.
- Using the above properties we can freely move the element on the screen.
- We can either use top or bottom prop at a time as setting them both at the same time dosen't makes sense. Same for left & right prop.
- We can use negative values to push items outside the page such as "top: -50px"

### Suppose if we want to position an item as absolute w.r.t to it's container, then we have to assign some position except static to the container.

## Static :

- By default position is set to static.
- They don't have access to top, left, right, bottom and z-index properties.

## Relative :

- Element remains in the normal flow of the document. It's assigned space is still preserved.
- Have access to top, left, right, bottom and z-index properties.

## Fixed :

- Element is removed from the flow of document. It gets fixed at the defined position.
- Even when we scroll page, it will follow us.
- Behaves very similarly to "absolute".

## Sticky :

- Only works when we set "top" property.
