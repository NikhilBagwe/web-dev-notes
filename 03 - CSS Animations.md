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
