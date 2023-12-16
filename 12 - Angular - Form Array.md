## FormArray :

- FormArray is a way to manage a collection of FormControls in Angular.
- The Form Control can be a FormGroup, FormControl or another FormArray.

### Difference between FormArray and FormGroup :

- In Angular, we can group FormControls in 2 ways i.e. using FormArray and FormGroup.
- The difference between them is the way they create collections.
- FormGroup - Stores the form controls in the form of key-value pair in an object.
- FormArray - Stores the form control as an element of an array.

## Creating a FormArray :

- Declare FormArray in class file.
  
```js
export class AppComponent implements OnInit{
  title = 'template-driven-form';

  reactiveForm: FormGroup;

  ngOnInit() {
    this.reactiveForm = new FormGroup({
      firstname: new FormControl(null, Validators.required),
      lastname: new FormControl(null, Validators.required),
      email: new FormControl(null, [Validators.required, Validators.email]),
      username: new FormControl(null),
      dob: new FormControl(null),
      gender: new FormControl('male'),
      address: new FormGroup({
        street: new FormControl(null, Validators.required),
        country: new FormControl('India', Validators.required),
        city: new FormControl(null),
        region: new FormControl(null),
        postal: new FormControl(null, Validators.required),
      }),

      skills: new FormArray([     // FormArray
        new FormControl(null),
        new FormControl(null),
        new FormControl(null)
      ])
    })
  }
}
```
- In View template, we create a container inside which we create the form elements.
- In our code, we can simply use a FOR loop and loop over the skills FormArray.
- The FormControls which will be genrated by the FOR loop are not connected to the FormArray elements present in class file.
- So we need to use formContolName directive to bind them.
- Also we need to provide a dynamic name for each generated FormControl. So we will use the "index".

```html
<div class="input-box" formArrayName="skills">
  <input type="text" 
    placeholder="Add Skill..."
    *ngFor="let control of reactiveForm.get('skills')['controls']; let i=index"
    [formControlName]="i"
  >
</div>
```

## Adding and Deleting Form Controls dynamically using RF: 

- Here we will provide the user with an "Add" button by clicking on which a new Form control will be added dynamically and similarly a "Delete" button to delete it.
- In the ngFor loop, the "controls" property stores all the form controls of the "skills" form array as its element.
- variable "i" stores index of that curent Form control.
- Since we want to assign the value stored in "i" to "formControlName", we use Property binding.

```html
<div class="input-box" formArrayName="skills">
  <h4>Add Skills</h4>
  <div class="column" *ngFor="let control of reactiveForm.get('skills')['controls']; let i=index">
    <input type="text" 
      placeholder="Add Skill..."
      [formControlName]="i"
    >
    <button type="button" class="btn-add-delete" (click)="DeleteSkill(i)" >
      Delete
    </button>
  </div>
</div>

<button type="button" class="btn-add-delete" (click)="AddSkills()">
  Add Skills
</button>
```

```js
export class AppComponent implements OnInit{
  title = 'template-driven-form';

  reactiveForm: FormGroup;

  ngOnInit() {
    // Specify the form controls that our form needs
    this.reactiveForm = new FormGroup({
      .....

      skills: new FormArray([
        new FormControl(null, Validators.required),
        // new FormControl(null, Validators.required),
        // new FormControl(null, Validators.required),
        // new FormControl(null, Validators.required)
      ])
    })
  }

  OnFormSubmitted(){
    //alert(this.reactiveForm.valid)
    console.log(this.reactiveForm.value)
  }

  // Adds a new Form Control for Skills formArray
  AddSkills(){
    // push method is only avalilable on FormArray. Thus, we explicitly perform casting.
    (<FormArray>this.reactiveForm.get('skills')).push(new FormControl(null, Validators.required))
  }

  // Delete the skill form Control based on provided index
  DeleteSkill(index: number){
    const controls = <FormArray>this.reactiveForm.get('skills')
    controls.removeAt(index)
  }
} 
```

## Rendering Form Group Dynamically:

- It is similar to expereince section in a job portal where we can add multiple expereinces. 

```html
<div class="input-box" formArrayName="experience">
  <!-- Below FormGroup is present inside the "experience" FormArray and will be rendered dynamically -->
  <div class="experience" *ngFor="let exp of reactiveForm.get('experience')['controls']; let i=index" [formGroupName]="i">
      <label>Experience {{i+1}}</label>
      <input type="text" placeholder="Company Name" formControlName="company" />
      <div class="column">
        <div class="select-box">
          <select formControlName="position">
            <option hidden>Position</option>
            <option>Junior Developer</option>
            <option>Software Developer</option>
            <option>Senior Developer</option>
            <option>Team Lead</option>
          </select>
        </div>
        <input type="number" placeholder="Experience" formControlName="totalExp" />
      </div>

      <div class="column">
        <input type="date" placeholder="Start Date" formControlName="start" />
        <input type="date" placeholder="End Date" formControlName="end" />
      </div>

      <button type="button" class="btn-add-delete" (click)="DeleteExperience(i)">Delete Experience</button>
    </div>
</div>

<button type="button" class="btn-add-delete" (click)="AddExperience()">
  Add Experience
</button>
```

```js
export class AppComponent implements OnInit{
  title = 'template-driven-form';

  reactiveForm: FormGroup;

  ngOnInit() {
    // Specify the form controls that our form needs
    this.reactiveForm = new FormGroup({
      // ..........
      skills: new FormArray([
        new FormControl(null, Validators.required)
        // new FormControl(null, Validators.required),
        // new FormControl(null, Validators.required),
        // new FormControl(null, Validators.required)
      ]),

      // Below FormArray will contain FormGroups
      experience: new FormArray([
        // must be displayed empty until user clicks "add experience" button
      ])
    })
  }

  // ............

  AddExperience(){
    const formGroup = new FormGroup({
      company: new FormControl(null),
      position: new FormControl(null),
      totalExp: new FormControl(null),
      start: new FormControl(null),
      end: new FormControl(null)
    });

    (<FormArray>this.reactiveForm.get('experience')).push(formGroup)
  }

  DeleteExperience(index: number){
    const frmArray = <FormArray>this.reactiveForm.get('experience');
    frmArray.removeAt(index)
  }
} 
```

---

## User-defined Custom Validator :

- Custom validator is used to validate input data in a form control.
- Error code : Remove the logic to enable submit form button only when all required fields are filled with correct data. In console, we can see the "error" property under the "control" whose validation was set to "required".

  ![image](https://github.com/NikhilBagwe/web-dev-notes/assets/67143015/00acf5a1-a69f-426d-a55c-0d6f6a02ab74)

- Basically, if the "errors" property is null, there is no error on that form control.

---

### Validator to check if a "space" has been entered by the user in the text input form control:

- Only can be used on a Form Control. Not on a FormGroup, etc.
- Create below file.

![image](https://github.com/NikhilBagwe/web-dev-notes/assets/67143015/f6c49bac-5800-49d1-beee-2c7813fbf21c)


```js
import { FormControl } from "@angular/forms";

// export const noSpaceAllowed = (control: FormControl) => {
//     if(control.value != null && control.value.indexOf(' ') != -1){
//         // whatever value we return from here will be assigned to "errors" property of form control
//         return {noSpaceAllowed: true}
//     }
//     return null
// }

export class CustomValidators{
    static noSpaceAllowed(control: FormControl) {
        if(control.value != null && control.value.indexOf(' ') != -1){
            // whatever value we return from here will be assigned to "errors" property of form control
            return {noSpaceAllowed: true}
        }
        return null
    }
}
```

```js
// app.component.ts

import { CustomValidators } from './Validators/noSpaceAllowed.validator';

export class AppComponent implements OnInit{
  title = 'template-driven-form';

  reactiveForm: FormGroup;

  ngOnInit() {
    // Specify the form controls that our form needs
    this.reactiveForm = new FormGroup({
      firstname: new FormControl(null, [Validators.required, CustomValidators.noSpaceAllowed]),
      lastname: new FormControl(null, [Validators.required, CustomValidators.noSpaceAllowed]),
      // ....
  }
```

![image](https://github.com/NikhilBagwe/web-dev-notes/assets/67143015/ebbfa4b5-9300-4779-b51f-2497698c2b32)

---

## Displaying custom error message for a particular validation :

- Also done Null handling using Optional chaining "?." so that if  "reactiveForm.get('firstname').errors" expression returns null than further expression won't be evaluated.

```html
<form class="form" [formGroup]="reactiveForm" (ngSubmit)="OnFormSubmitted()">
    <div class="column">
      <div class="input-box">
        <input type="text" placeholder="First Name" formControlName="firstname" />

        <small *ngIf="reactiveForm.get('firstname').errors?.['required'] && reactiveForm.get('firstname').touched">
          *First name is a required field.
        </small>

        <small *ngIf="reactiveForm.get('firstname').errors?.['noSpaceAllowed'] && reactiveForm.get('firstname').touched">
          *No space is allowed for First name.
        </small>
      </div>
      .....
</form>
```

---

## Async Validator - Custom :

- Used when we need to send an HTTP request to the server to check if the data entered in a form element is valid or not.
- Eg: When a user is creating a username, it must be unique. Hence, we need to use async validator here to check if that username already exists in the DB or not.
- Returns either a Promise or Observable.
- Angular dosen't provide any built-in async validator. It only provides sync validators such as required, min, max, etc.
- "ng-pending" class is added when the async validation is being performed.

```js
// file_name.validator.ts

export class CustomValidators{
    // .....

    // This Async validator can be used on FormGroup, Form Control or FormArray
    static checkUserName(control: AbstractControl): Promise<any>{
        return userNameAllowed(control.value)
    }
}

// Mock API to test async validator
function userNameAllowed(username: string){
    const takenUserNames = ['johnsmith', 'manojjha', 'nikhil']

    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if(takenUserNames.includes(username)){
                resolve({checkUsername: true})
            }
            else{
                resolve(null)
            }
        }, 5000);
    })
}
```

![image](https://github.com/NikhilBagwe/web-dev-notes/assets/67143015/2103f0cd-4b7e-457c-b168-5380b860b90c)

- Add a YELLOW border to show validation is been performed.

```css
input.ng-pending{
  border: yellow 2px solid;
}
```

---
---

## valueChanges() event:

- It is an event raised by Angular forms whenever the value of FormControl, FormGroup or FormArray changes.

### Listening to FormControl:

```js
export class AppComponent implements OnInit{
  reactiveForm: FormGroup;

  ngOnInit() {
    // Specify the form controls that our form needs
    this.reactiveForm = new FormGroup({
      firstname: new FormControl(null, [Validators.required, CustomValidators.noSpaceAllowed]),
      // .....
    })

    // CODE -------------
    this.reactiveForm.get('firstname').valueChanges.subscribe((value) => {
      console.log(value)
    })
  }

  // ...
} 
```

### Listening to FormGroup:

```js
export class AppComponent implements OnInit{
  reactiveForm: FormGroup;

  ngOnInit() {
    // Specify the form controls that our form needs
    this.reactiveForm = new FormGroup({
      firstname: new FormControl(null, [Validators.required, CustomValidators.noSpaceAllowed]),
      // .....
    })

    // CODE -------------
    this.reactiveForm.valueChanges.subscribe((data) => {
      console.log(data)
    })
  }

  // ...
} 
```

---
---

## statusChange() event:

- An event which is raised by Angular whenever Angular calculates the validation status of a FormControl,etc. changes.
- Emits a string value which corresponds to "valid", invalid or pending.
- Returns an observable.
- Used to check valid/invalid status of form.
- In below example we are using statusChange() event to know the status of FormGroup and accordingly applying border around the form.

```js
export class AppComponent implements OnInit{
  reactiveForm: FormGroup;
  formStatus: string = ''

  ngOnInit() {
    // Specify the form controls that our form needs
    this.reactiveForm = new FormGroup({
      firstname: new FormControl(null, [Validators.required, CustomValidators.noSpaceAllowed]),
      // .....
    })

    // CODE -------------
    this.reactiveForm.get('email').statusChanges.subscribe((status) => {
      console.log(status)
      this.formStatus = status
    })
  }

  // ...
} 
```

- Apply CSS class on form.
  
```html
<section class="container" [ngClass]="formStatus">
  ....
</section>
```

```css
.container.VALID{
  border: green 3px solid;
}
.container.INVALID{
  border: red 3px solid;
}
.container.PENDING{
  border: orange 3px solid;
}
```

---
---

## setValue() method:

- Used to update the value of a FC, FG or FA.
- We must pass an object in setValue() to update the value and that object must MATCH the structure of FC, FG or FA which we are trying to update.
- Eg: In below code on clicking the "Create username" button, an username will be auto-generated using the firstname and lastname. The button will be disabled until the user enters the required data to generate username.

```html
<div class="column">
    <div class="input-box">
      <input type="text" placeholder="username" formControlName="username"/>
      <button class="btn-gen-username" type="button" (click)="GenerateUserName()"
      [disabled]="!(reactiveForm.get('firstname').value 
                  && reactiveForm.get('lastname').value 
                  && reactiveForm.get('dob').value)"
      >
        Create a Username
      </button>
    </div>
    <div class="input-box">
      <input type="date" placeholder="Date of Birth" formControlName="dob" />
    </div>
</div>
```

```js
GenerateUserName(){
    let username = '';
    const fName: string= this.reactiveForm.get('firstname').value;
    const lName: string= this.reactiveForm.get('lastname').value;
    const dob: string= this.reactiveForm.get('dob').value;

    if(fName.length >= 3){
      username += fName.slice(0, 3);
    }
    else {
      username += fName;
    }

    if(lName.length >= 3){
      username += lName.slice(0, 3);
    }
    else {
      username += lName;
    }

    let datetime = new Date(dob);
    username += datetime.getFullYear();
    username = username.toLowerCase();

    console.log(username)

    // structure similar to FormGroup ---------------------------
    this.reactiveForm.setValue({
      firstname: this.reactiveForm.get('firstname').value,
      lastname: this.reactiveForm.get('lastname').value,
      email: this.reactiveForm.get('email').value,

      // setting username value ---------------------------------
      username: username,

      dob: this.reactiveForm.get('dob').value,
      gender: this.reactiveForm.get('gender').value,
      address: {
        street: this.reactiveForm.get('address.street').value,
        country: this.reactiveForm.get('address.country').value,
        city: this.reactiveForm.get('address.city').value,
        region: this.reactiveForm.get('address.region').value,
        postal: this.reactiveForm.get('address.postal').value,
      },
      skills: this.reactiveForm.get('skills').value,
      experience: this.reactiveForm.get('experience').value
    })
  }
```



























