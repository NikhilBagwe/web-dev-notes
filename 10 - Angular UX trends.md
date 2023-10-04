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

# Data Binding :

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

# Interpolation :

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
- For example :
```html
 <h1 class="{{heading}}">Calculations</h1>
```
- There is a better way to do that in Angular.

---
---

# Property Binding :

- Used to bind Dynamic data.
- Interpolation is used to DISPLAY dynamic data while Prop. Binding is used to bind a DYNAMIC value in HTML attribute.

### Example :

```html
<img [src]="myImage" alt="">
<br>
<input type="text" [value]='name'>
```

```js
export class PropBindingComponent {
  name: string = 'john';
  myImage: string =
    'data:image/jpeg;base64,/9j/4AA.. Image Address';
}
```

- The above example can also work using Interpolation but it is not a good practice to do.
- There are certain scenarios where Interpolation fails to work. Eg: [disabled], [hidden], [checked], etc.

## Attribute Binding :

- Used where the attribute is not a Standard HTML attribute.
- Eg: aria-label, data-name
- SYNTAX :

```html
<h1 [attr.aria-label] = "name">hi</h1>
```

## Another Syntax :

- Used very less times.

```html
<img bind-src="myImage" alt="">
```

---
---

# Event Binding :

- Used to send Data from "View => Component"

```html
<h1>{{count}}</h1>
<button (click) = "clickMethod()">+ Count +</button>
```

```js
export class PropBindingComponent {
  count: number = 0;

  clickMethod() {
    this.count++;
  }
}
```

### Pass data to events :

```html
<h1>{{value}}</h1>
<button (click) = "changeValue('Bagwe')">Change Value</button>
```

```js
export class PropBindingComponent {
  value: any = 'Nikhil';

  changeValue(val: string) {
    this.value = val;
  }
}
```

## $event :

- A reserved variable in Angular.
- We get all information about an event using it.
- We can use it with (scroll), (change), etc. Events.

```html
<input type="text" (input)="inputChange($event)" placeholder="Enter your name..">
<h1>Value: {{val2}}</h1>
```

```js
export class PropBindingComponent {
  val2: string = '';

  inputChange(event: any) {
    console.log(event);
    console.log(event.target.value);
    this.val2 = event.target.value;
  }
}
```

---
---

# Class Binding :

```html
<h1 [class.myClass]='true'>fhsdfhsd</h1>
```

- In dev tools we can see that the class is attached to the h1 element

```html
<h1 _ngcontent-ng-c1295339505="" class="myClass">fhsdfhsd</h1>
```

- Instead of passing just "true" we can also pass some object's property like "emp.isActive".

# Style Binding :

- Add CSS directly in the element.

```html
<h1 [style.padding]="'30px'">fhsdfhsd</h1>
```
- Similarly we can also use ternary operator logic and object properties.

### NOTE : Using above methods we can only bind one class or style at a time. For that we use ngClass & ngStyle

# ngClass :

- Bind multiple classes to element.

```html
<h1 [ngClass]="'class1 class2 class3'">Hello</h1>
```

- Another way: Based on true or false the class will be applied to element.
- Instead of boolean value we can also pass obj. prop.

```html
<h1 [ngClass]="{
    'class1': true,
    'class2': emp.isActive
}">Hello</h1>
```

# ngStyle :

```html
<h1 [ngStyle]="{
    'background': 'yellow',
    'padding': '40px',
    'width': '100px',
    'opacity': 0.5
}">Hello</h1>
```

- Similarly we can assign the above object to a variable in .ts file and then assign that variable in ngStyle. 
























