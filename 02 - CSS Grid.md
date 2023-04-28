## Grid :

- After setting "display: grid" nothing will happen. We need to define no. of rows and cols.

## grid-template rows & grid-template columns :

- To define no. of rows and columns our grid will have.
- Grid with 5 rows, 5 columns :
```css
.container {
  display: grid;
  grid-template-rows: 100px 100px 100px 100px 100px;
  grid-template-columns: 100px 100px 100px 100px 100px;
}
```
- A grid starts with (1, 1) not (0, 0)

## grid-row-start, grid-row-end, grid-column-start, grid-column-end :

- Position a grid element anywhere in the grid by explicitly defining it's position.
- Eg: 
```css
.item-1 {
  grid-row-start: 1;
  grid-row-end: 3;
  grid-column-start: 1;
  grid-column-end: 4;
}
```

## Shorthand property : grid-row, grid-column

- Shorthand property to above 4 properties to position grid element.
```css
.item-1 {
  grid-row: 1 / 3;  /* start line / end line */
  grid-column: 1/ 4;
}
```

## span :

- It basically says, from wherever you are span yourself by the no. of times value mentioned.
- Better than above properties and more readable.
- Disadvantage: Cannot explicitly mention the starting and ending point of element.
```css
.item-2 {
  grid-row: span 2;
  grid-column: span 2;
}
```

## Follow along starter code :

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <link rel="stylesheet" href="style.css" />
    <link rel="stylesheet" href="style2.css" />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Roboto:wght@100;400;700&display=swap"
      rel="stylesheet"
    />
    <title>CSS Grid</title>
  </head>
  <body>
    <div class="container">
      <div class="item item-1">1</div>
      <div class="item item-2">2</div>
      <div class="item item-3">3</div>
      <div class="item item-4">4</div>
    </div>
  </body>
</html>
```

```css
:root {
  --clr-dark: #0f172a;
  --clr-light: #f1f5f9;
  --clr-accent: #e11d48;
}

*,
*::before,
*::after {
  box-sizing: border-box;
}

body {
  margin: 5em 0 0 0;
  padding: 0;
  line-height: 1.6;
  word-spacing: 1.4px;
  font-family: "Roboto", sans-serif;
  color: var(--clr-dark);
  background-color: var(--clr-light);
}

.container {
  width: 80%;
  margin: 0 auto;
  border: 10px solid var(--clr-dark);
}

.item {
  padding: 0.5em;
  background-color: #fb7185;
  font-weight: 700;
  color: var(--clr-light);
  border: 10px solid var(--clr-accent);
}
```

