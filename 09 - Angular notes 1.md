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


---
## Angular Forms :
---

## Template Driven forms :

- In TDF, all data binding and Form validation will be performed in Template i.e .html file only.
- Import FormsModule in app.module.ts for using Template Driven forms.
- Important function of Forms is to : Grab data what user has typed i.e "Data binding" and "Validation".
- In the "form" tag we add a Global Form level coordination Directive whose job is to gather and validate data from all Form controls.
- We will also add Control-level directives which is responsible only for that Form Control
- This Directives will coordinate with each other thus allowing us to do automated Data binding and Form Validation.

## NgForm directive :

- It is implicitly/automatically added by Angular to every "form element" once we add FormsModule in our app.
- It produces an export which points to itself.
- The Angular directive exportAs defines a name that can be used in the template to assign this directive to a variable.

```html
<form class="login-form data-form" #loginForm="ngForm">
```
- So ngForm will grab the value exported by form and assign it to Template variable "loginForm".

## NgModel :

- Now to tell ngForm, what are the form controls present in the form we use "ngModel" directive.
- Thus, now Angular can grab value typed by user and keep a track of it. UI is now binded successfully.
- Also the form control must have a "name" attribute set.
- NgModel tracks value of each Form Control using Event handlers.

```html
<form class="login-form data-form" #loginForm="ngForm" >

  <mat-form-field>
    <input matInput type="email" name="email" placeholder="Email" ngModel #email="ngModel">
  </mat-form-field>

  <mat-form-field>
    <input matInput type="password" name="password" placeholder="Password" ngModel #password="ngModel">
  </mat-form-field>

  <button mat-raised-button color="primary" (click) = "login(loginForm)">
    Login
  </button>

</form>

<div class="form-val">
  {{loginForm.value | json}}
  {{email.value + ' ' + password.value}}
</div>
```

## Form Validation :

- Validation is done at Browser level when form gets submitted.
- We can simply add "required" attribute to the desired Form control.
- Check validity of a certain field :
  
```html
<div class="form-val">     
  {{email.valid | json}}
</div>
```

- Even if 1 of the Child Form control of a Form is invalid, the whole form becomes invalid.
- The NgModel directive automatically changes the CSS State classes(reflect state validity of Field value) applied to Form control if the value entered into it is invalid.
- CSS Class Eg: ng-untouched, ng-dirty, ng-pristine, etc.
- The instance of NgModel associated to each Form control tracking the validity state of field value produces an "Errors object" which contains the errors that are currently present in the form field.
- Below code displays error msg related to "required" validator when input field is invlaid using Errors object:
  
```html
<form class="login-form data-form" #loginForm="ngForm" >

  <mat-form-field>
    <input matInput type="email" name="email" placeholder="Email" ngModel #email="ngModel" required>
    <mat-error *ngIf="email.errors.required">The email is mandatory</mat-error>
  </mat-form-field>
.....
</form>

<div class="form-val">     
  {{email.errors | json}}
</div>
```

## Built-in Template Driven Form Validators :

1. required
2. minlength
3. maxlength
4. email
5. pattern - Regular expression

## ngSubmit :

- Normally when we add type="submit" to Submit button of an HTML form, it grabs all the values from Form Controls and sends it to Backend in a POST request.
- But we don't want this in an SPA. We want the form to send an HTTP AJAX request.
- So we use ngSubmit to prevent Default behaviour of forms i.e submitting the form as HTTP POST request.
- We can also used the [disabled] attribute to disable the Submit button until all fields of form have valid values.

```html
<form class="login-form data-form" #loginForm="ngForm" (ngSubmit)="login(loginForm)">

  <mat-form-field>
    <input matInput type="email" name="email" placeholder="Email" ngModel #email="ngModel" required>
    <mat-error *ngIf="email.errors?.required">The email is mandatory</mat-error>
  </mat-form-field>

  <mat-form-field>
    <input matInput type="password" name="password" placeholder="Password" ngModel #password="ngModel" required>
  </mat-form-field>

  <button mat-raised-button color="primary" type="submit" [disabled]="!loginForm.valid">
    Login
  </button>

</form>
```
### NOTE : Errors will not always be present. So use '?' operator.














  











