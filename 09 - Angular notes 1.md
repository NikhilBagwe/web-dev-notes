[Course link](https://www.youtube.com/watch?v=VTEDh2pNSBQ&ab_channel=BoualiAli)

## Commands :

1. npm i -g @angular/cli@16.2.1
2. ng version
3. ng serve --host 0.0.0.0 --disable-host-check  = (When ypu get Invalid Host error - Gitpod)
4. ng new project_name --skip-tests

## Create a Custom script command :

- In package.json, "scripts" section add your custom command.

```js
"scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "watch": "ng build --watch --configuration development",
    "test": "ng test",
    "custom" : "echo hello world"
  }
```
- Then run it using "npm run custom"

---

## Components :

- Fundamental building blocks of an Angular app.
- They encapsulate UI and logic(behaviour of application).
- Modular, Reusable and self-contained.
- A component consists of 3 parts :

### 1. Template :

- Defines UI and structure of component.
- Uses HTML and Angular-specific syntax to bind data, handle events and render dynamic events.


### 2. Class :

- Contains component's logic and data.
- Written in TS includes properties, methods and Lifecycle hooks.

### 3. Metadata : CSS files

---

## Component Lifecycle hooks :

- This hooks allow us to tap into different stages of Component's lifecycle.
- Provides methods that are automatically called by Angular at a specific point while component's Creation, Updation and Destruction.
- ngOnInit() - Can contain code to fetch data from DB using API
- ngOnChanges() - Called when 1 or more input properties of Component are changed. It receives a object containing previous and current value of input properties.
- ngOnDestroy() - Called just before the component is destroyed. Used to cleanup resources.


















