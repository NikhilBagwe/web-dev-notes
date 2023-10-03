## Intro :

- Angular is a framework maitained by Google used for building Reactive SPAs using HTML and TypeScript.
- TypeScript is superset of JS.
- v1. released in 2010 as AngularJS.
- Complete rewrite was performed in 2016 which used TS.

## Why use Angular ?

- Component based structure
- Maintainable and Scalable structure.
- Modularity

## What is SPA ?

- A SPA consists of only 1 page i.e index.html which contains all the code required for rendering the page.
- It eliminates the need for reloading the page.
- A Multi-page application reloads each time the user opens a new page in the browser.

---
---

## Data Binding :

- Data binding is basically the communication between Component (.ts) and View (.html).

### 1-way Data binding :

- Used for only displaying Dynamic data.
- In Angular, we use "String Interpolation" or "Interpolation" to acheive it. Here we use CURLY brackets.
- Another way is "Property Binding". Here we use SQUARE brackets in HTML attributes.
- Data goes from " Component => View " in case of Interpolation and Prop. Binding
- We use EVENT BINDING to send data from " View => Component ".

### 2-way Data binding :

- Data is shared between Comp. and View in real-time.

---
---

## Interpolation :

### 1. String Interpolation :

```html
<div class="content" role="main">
  <h1>Welcome {{name}}!</h1>
  <h1>Employee: Name = {{emp.name}}, Job = {{emp.job}}</h1>
</div>
```

```js
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css'],
})
export class AppComponent {
  name: string = 'Nikhil';

  emp = {
    name: 'Mike',
    job: 'Devloper',
  };
}
```
### 2. String Concatenation :

```html
<div class="content" role="main">
  <h1>String Concatenation</h1>
  <h2>{{"My name is " + emp.name}}</h2>
</div>
```

### 3. Calculations :

```html
<div class="content" role="main">
  <h1>Calculations</h1>
  <h2>{{ 5 + 5}}</h2>
</div>
```

### 4. Using Built-in JS methods :

```html
<div class="content" role="main">
  <h2>{{ name.length}}</h2>
  <h2>{{ name.toUpperCase()}}</h2>
  <h2>{{ name.includes('k')}}</h2>
</div>
```

## Where we shouldn't use Interpolation ?

- While defining dynamic HTML attributes values.
```html
 <h1 class="{{heading}}">Calculations</h1>
```
- There is a better way to do that in Angular.
















