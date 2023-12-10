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
  <div class="column" *ngFor="let control of reactiveForm.get('skills')['controls']; let i=index"
  [formControlName]="i">
    <input type="text" 
      placeholder="Add Skill..."
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






















