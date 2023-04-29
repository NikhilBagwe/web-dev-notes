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

## grid-row, grid-column

- Shorthand property to above 4 properties to position grid element.
```css
.item-1 {
  grid-row: 1 / 3;  /* start line / end line */
  grid-column: 1/ 4;
}
```

## grid-area :

- Even faster Shorthand property than grid-row and grid-column is grid-area.
- grid-area: row-start col-start row-end col-end;
```css
.item-3 {
  grid-area: 3 / 1 / 5 / 6;  /* row-start col-start row-end col-end */
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

## Layering elements on top of each other :

- Using grid we can simply position elements on top of each other.
- Simply set the z-index higher than others.

```css
.item-2 {
  /* grid-area: row-start col-start row-end col-end */
  grid-area: 2 / 3 / 4 / 6;
  z-index: 1;
}
```

## grid-auto-rows & grid-auto-columns :

- Suppose if the whole grid is filled/ occupied by our elements and then we add another element into our grid container, it is called an "Implicit grid".
- That element dosen't inherit the values we set for grid-template-rows and columns.
- "grid-auto-rows" sets the size of any implicit rows that gets created.
- "grid-auto-columns" sets the size of any implicit columns that gets created.

```css
.container {
  display: grid;
  grid-template-rows: 100px 100px 100px 100px 100px;
  grid-template-columns: 100px 100px 100px 100px 100px;
  grid-auto-rows: 100px;
  grid-auto-columns: 100px;
}
```

## grid-auto-flow :

- By default, our grid container added a new row to contain the newly added element as an implicit row.
- But we can change that and make it as an implicit column using "grid-auto-flow: column".

```css
.container {
  display: grid;
  grid-auto-rows: 100px;
  grid-auto-flow: column;
}
```

## Fractional units :

- 1 fr unit represents a fractional value of the available space.
- It fills out the space equally.

```css
.container {
  display: grid;
  grid-template-rows: 100px 100px;
  grid-template-columns: 1fr 1fr 1fr;
}
```

- If I set the second fr 2 or 3, it will accordingly acquire more space.
- We can also mix them with other units. Eg: grid-template-columns: 100px 1fr 2fr;

## minmax(min width, max width) :

- When we resize the page, some elements get way thin.
- So to set the minimum width we use minmax() function.

## repeat() :

- Repeats the row/column given no. of times.
- It takes 2 arguments : No. of times to be repeated, Size of it.

```css
.container {
  display: grid;
  grid-template-rows: repeat(2, 100px);
  grid-template-columns: 1fr minmax(100px, 3fr) 1fr;
}
```

## grid-gap :

- Adds gap in between elements.
- Shorthand property for grid-row-gap and grid-column-gap.

## grid-template-area :

- A way of positioning elements in grid without keeping track of rows and columns.

```css
.container {
  display: grid;
  grid-template-rows: 100px 300px 100px;
  grid-template-columns: 1fr 3fr;
  grid-template-areas:
    "header header"
    "main aside"
    "footer footer";
}
```

- Each set of double/single quotes represent the row and each value inside of them represent a column.
- Defines areas within a grid container. These areas can then be referenced when placing a grid item.

## justify-items :

- Aligns all grid items according to the column axis within their defined grid block area.

## align-items :

- Aligns all grid items according to the row axis within their defined grid block area.

```css
.container {
  display: grid;
  grid-template-rows: repeat(4, 100px);
  grid-template-columns: repeat(4, 1fr);
  justify-items: center;
  align-items: end;
}
```

## justify-self & align-self :

- If we want to align/justify grid items individually, we can use this properties.
- This will overwrite the justify-items/align-items properties.

```css
.item-1 {
  /* width: 200px; */
  justify-self: start;
}
```

## justify-content & align-content :

- Now if you want to move all the grid items w.r.t to their container, use this props.
- justify-content : align items along the "row-axis"
- align-content : align items along the "column-axis"

```css
.container {
  display: grid;
  height: 600px;
  grid-template-rows: repeat(2, 100px);
  grid-template-columns: repeat(2, 100px);
  justify-content: space-between;
  align-content: space-between;
}
```

## auto-fit : Create a Responsive grid that requires 0 media queries :

- auto-fit keyword will make items autofit and wrap onto next row creating a responsive grid.

```css
.container {
  display: grid;
  grid-template-rows: repeat(4, 100px);
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
}
```


---

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

