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




















