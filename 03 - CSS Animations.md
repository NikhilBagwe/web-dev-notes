## CSS Animations :

- There are 2 ways of creating animations in CSS : Transitions and Animations.

---

## Transitions :

- They wait until changes in the property occurs and then allows those changes to take place over time.
- Without a transition prop, any changes in a property will take place immediately.
- Must be used when props are changed interactively by user when hovered or focused on the part of page.

### Transition properties :

```css
.btn {
  font-size: 2rem;
  font-weight: 700;
  padding: 0.5em 1em;
  color: var(--clr-accent);
  background-color: var(--clr-rgba);
  border: 10px solid var(--clr-accent);
  border-radius: 5px;

  transition-property: transform;
  transition-duration: 0.3s;
  transition-timing-function: ease;
  transition-delay: 0s;
}
```

### Shorthand Transition property :

```css
.btn {
  font-size: 2rem;
  font-weight: 700;
  padding: 0.5em 1em;
  color: var(--clr-accent);
  background-color: var(--clr-rgba);
  border: 10px solid var(--clr-accent);
  border-radius: 5px;

  transition: transform 1s ease 0s;
}

.btn:hover {
  transform: translateY(-100px);
}
```

- Suppose I wamted to chnge the background color and font-color of button also. 
- The above transition prop won't have effect on them and they will instantly change.
- So we have to add each prop into transition prop and mention its time duration.

```css
.btn {
  transition: transform 1s ease 0s, backgroun-color 1s, color 1s;
}

.btn:hover {
  transform: translateY(-10px);
  background-color: var(--clr-accent);
  color: var(--clr-light);
}
```

- If you don't want to mention each property name individually in transition prop, just use "all" keyword.

```css
.btn{
  transition: all 1s ease 0s;
}
```

### Starter code :

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://fonts.googleapis.com/css2?family=Roboto:wght@100;400;700&display=swap"
      rel="stylesheet"
    />
    <link rel="stylesheet" href="../normalize.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Transitions</title>
  </head>
  <body>
    <button class="btn">learn more</button>
  </body>
</html>

```

```css
:root {
  --clr-dark: #070a12;
  --clr-light: #f9f9fb;
  --clr-accent: #f43f70;
  --clr-rgba: rgba(244, 63, 112, 0.2);
}

*,
*::before,
*::after {
  box-sizing: border-box;
}

* {
  font-family: "Roboto", sans-serif;
}

body {
  margin: 0;
  padding: 0;
  line-height: 1.5;
  word-spacing: 1.4px;
  color: var(--clr-dark);
  background-color: var(--clr-light);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.btn {
  font-size: 2rem;
  font-weight: 700;
  padding: 0.5em 1em;
  color: var(--clr-accent);
  background-color: var(--clr-rgba);
  border: 10px solid var(--clr-accent);
  border-radius: 5px;
}

.btn:hover {
  transform: translateY(-10px);
}
```

---

## Animations :

- Provide keyframes for more control on the animation 
- Allows us to create more complex animations on a frame by frame basis.

## Defining an keyframe animation :

```css
/* heading is initially present in left side of screen and then slides into its original position */

@keyframes slideInLeft {
  /* represents the start of animation i.e 0% */
  from {
    transform: translateX(-300px);
  }

  /* represents the end of animation i.e 100% */
  to {
    transform: translateX(0);
  }
}
```

## animation properties :

```css
.heading-1 {
  animation-name: slideInLeft;

  /* defines how long it takes to animate from 0% to 100% */
  animation-duration: 1s;

  animation-timing-function: ease-in;

  /* animation will run right on page is loaded */
  animation-delay: 0s;

  /* defines how many times/laps the animation should run */
  animation-iteration-count: 1;

  /* defines whether animation should run normal or reverse */
  animation-direction: normal;

  /* refer docs */
  animation-fill-mode: none;

  transform: translateX(-150px);
}
```

## shorthand prop : animation :

```css
.heading-1 {
  animation: slideInLeft 1s ease-in 0s 1 normal both;
}
```
- Lets keep rest of the props at default value. Now it looks cleaner.

```css
.heading-1 {
  animation: slideInLeft 1s ease-in;
}
```

## rotate animation :

```html
<body>
    <section>
      <h1 class="heading-1">Hello, World!</h1>
      <h3 class="animate rotate">Hello, World!</h3>
    </section>
  </body>
```

```css
.animate {
  animation-duration: 1s;
  animation-fill-mode: both;
  animation-iteration-count: infinite;
}

@keyframes rotate {
  from {
    transform: rotate(0);
  }
  to {
    transform: rotate(360deg);
  }
}

.rotate {
  animation-name: rotate;
  animation-timing-function: linear;

  /* rotates the element from the top left corner */
  transform-origin: top left;
}

```







i

