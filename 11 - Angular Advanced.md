# Reactive Forms :

### Why not use a normal HTML form ?

- When a normal HTML form is submitted, it reloads the page by making an HTTP request to server.
- Thus, it kills the whole purpose of creating an SPA as by reloading the page it will restart the Angular SPA.
- Hence, we need Angular's help to stop this default behaviour which can be acheived using Template driven or Reactive forms.

## Reactive Forms :

- In RF, we create the Form group and Form control in the component class and then we somehow synchronize it with the HTML form we have defined in our View template.
- Creating dynamic controls is easier.
- Must import ReactiveFormsModule from @angular/forms in App module file.

### Why we use FormGroup while creating a Reactive form as in Template-driven form we use an onject on "ngForm" ?

- ngForm is also a type of FormGroup.
- When we import FormsModule from angular/forms, then whenever it finds a form in angular app it will automatically make it as Template-driven form. Thus, we don't need to explicitly use ngForm on it.
- Since, ngForm is storing a collection of FormControls thus it is a type of FormGroup.

## Creating a Reactive form :

```js
import { Component, OnInit } from '@angular/core';
import { FormControl, FormGroup } from '@angular/forms';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})

export class AppComponent implements OnInit{
  title = 'template-driven-form';

  reactiveForm: FormGroup;

  ngOnInit() {
    // Specify the form controls that our form needs
    this.reactiveForm = new FormGroup({
      firstname: new FormControl(null),
      lastname: new FormControl(null),
      email: new FormControl(null),
      username: new FormControl(null),
      dob: new FormControl(null),
      gender: new FormControl(null),
      street: new FormControl(null),
      country: new FormControl(null),
      city: new FormControl(null),
      region: new FormControl(null),
      postal: new FormControl(null),
    })
  }
} 

```

## Connecting RF to HTML form in View template :

- Bind the FormGroup and FormControl as below
  
```html
<form class="form" [formGroup]="reactiveForm">
    <div class="column">
      <div class="input-box">
        <input type="text" placeholder="First Name" formControlName="firstname" />
      </div>

      <div class="input-box">
        <input type="text" placeholder="Last Name" formControlName="lastname"/>
      </div>
    </div>

    .....
    .....
</form>
```

## ngSubmit :

- When a form is submitted, Angular raises an event called ngSubmit.
- We can listen to that event.

```html
<form class="form" [formGroup]="reactiveForm" (ngSubmit)="OnFormSubmitted()">
  .
  .
  <input type="submit" value="Submit" class="submit-btn">
</form>
```

## Adding Validation :

- By default if we don't add any validation, the "valid" property of FormGroup and FormControl will be true.
- In TDF, we used to use HTML attributes to add validation to HTML form such as "required,email,etc." in the View page itself.
- But in RF, we will define the validation in FormControl itself.

```js
export class AppComponent implements OnInit{
  title = 'template-driven-form';

  reactiveForm: FormGroup;

  ngOnInit() {
    this.reactiveForm = new FormGroup({
      firstname: new FormControl(null, Validators.required),
      lastname: new FormControl(null, Validators.required),
      email: new FormControl(null, Validators.required),
      ....
    })
  }
} 
```

## Passing Multiple validators :

- We have to pass an array of Validators.
```js
ngOnInit() {
    this.reactiveForm = new FormGroup({
      ....
      email: new FormControl(null, [Validators.required, Validators.email]),
      ....
    })
  }
```

## Adding RED border for invalid input fields :

- In "app.component.css" file add below code:
```css
input.ng-invalid{
  border: red 2px solid;
}
```
- When Angular automatically adds the "ng-invalid" class to an input form control when it becomes invalid based on the validations provided in class file, the border changes to RED.
- On page load we must not show red border around the form controls. Only when user TOUCHES the Form control and dosen't enter a valid value, then only show RED border. Use "ng-touched"
- Make below changes in code.
```css
input.ng-invalid.ng-touched{
  border: red 2px solid;
}
```

## Showing Validation Error messages :

- To display validation message for a particular FormControl we have to access the "invalid" and "touched" property of that FormControl through FormGroup using "get('name of formcontrol')" method.

```html
<form class="form" [formGroup]="reactiveForm" (ngSubmit)="OnFormSubmitted()">
    <div class="column">
      <div class="input-box">
        <input type="text" placeholder="First Name" formControlName="firstname" />
        <small *ngIf="reactiveForm.get('firstname').invalid && reactiveForm.get('firstname').touched">
          *First name is a required field.
        </small>
      </div>
```

## Disable SUBMIT button until valid data is entered into the form :

- We will use "valid or invalid" property of the FormGroup.
- Using Property binding :

```html
<form>
    ....
    <input type="submit" value="Submit" class="submit-btn" [disabled]="!reactiveForm.valid">
    ....
</form>
```

## Grouping of Form Controls :

- We can find all the form controls present in the FormGroup under "controls" property.
- There are 3 ways to 
---
---

# Angular Router :

- A separate module in Angular.
- Provides necessary service providers and directives for navigating through application views.

## Components of AR :

1. Router - A service (Angular Router API) that enables navigation from one component to the next component. Provides methods like navigate() or navigateByUrl(), to navigate to a route
2. Route - Tells the Angular Router which view to display when a user clicks a link or pastes a URL into the browser. Every Route consists of a path and a component it is mapped to.
3. Routes - an array of Route objects our application supports.
4. RouterOutlet - a directive (<router-outlet>) that serves as a placeholder, where the Router should display the view.
5. RouterLink - a directive that binds the HTML element to a Route.
6. RouterLinkActive - a directive for adding or removing classes from an HTML element that is bound to a RouterLink.
7. ActivatedRoute - an object that represents the currently activated route associated with the loaded Component.
