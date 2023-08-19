1. npm install -g @angular/cli

2. ng new todo-list
   If it gives error then use : Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned

3. ng serve : to run your app

4. To create a new component use command: ng generate component comp_name
1.28.42 min

https://www.youtube.com/watch?v=CGLdH5ORX-Y&ab_channel=OctAcademy 44 min

== 2 ===========================

- To check version of angular cli : ng version 

- Create new project : ng new project_name

- To run your app : ng serve

- Generate component : ng generate component Home

==> Install lower version of Angular : 

- First 'npm uninstall' the current one.
- Install CLI of that version : npm i -g @angular/cli@10.0.0


== 3 ===========================


main.ts : it loads the whole angular app into index.html i.e bootstraps it.

angular.json : Angualr app configuration like Set default loading page.

tsconfig.json : Manages Typescript configuration at global level.

tsconfig.app.json : Manages Typescript configuration at app level.

tsconfig.spec.json : Manages Typescript configuration for testing.


== 5 =========== Interpolation ====================================

==> Interpolation :

- Used to display dynamic data from app.component.ts on HTML page i.e app.component.html.
- We can also call functions.

<div class="content" role="main">
  <h1>Welcome to {{title}}!</h1>
  <h2>{{data}}</h2>
</div>

export class AppComponent {
  title = 'Hello0 world';
  data = 'nikhil';
}

- Assign class : <h2 class="{{title}}">{{data}}</h2>

=> What we can't do using Interpolation ?

- We cannot change the value or assign new value to the data being displayed.
- eg :<h2>{{data = 90}}</h2>
- Can't check type of var, increment , decrement operator on var.


==== 6 =======================================================

=> Generate component : "ng generate component Home" OR "ng g c home"

By deault 'app' is root component. So new components are added inside it.

=> Modules : 

- is a logical grouping of related components, services, directives, and other application artifacts
- modules provide a way to organize and manage the different parts of an Angular application.
- while components represent individual UI elements and encapsulate their logic and behavior. 

- Making module and adding components inside it:

ng g m user-auth
ng g c user-auth/login

==== 7 =======================================================

==> Components :

- Components are building blocks of a website.
- Each of them provide a specific functionality.

- After creating a component 'user-list' in 'app',  goto .ts file of 'user-list'.
- Copy the name of selector.
- Use that name as HTML tag in app.html file to render 'user-list' component.

- We can also change the name of selector.

==== 8 =======================================================

==> Component with Inline Style :

- Instead writing CSS styles in a separate app.css file, you can write it directly in 'styles' section
  of @Component in app.ts file.
- CSS file is not generated.

- CMD : ng g c user-list --inline-style


==> Component with Inline Template :

- Here HTML file is not generated for the component and you can write the HTML code in 
  app.ts file -> @Component -> template section.

- CMD : ng g c user-list --inline-template


==> Component with Inline Template and style :

- Both HTML and CSS files are not generated. Only app.ts file is present in which we write both html and css

- CMD : ng g c user-list --inline-style --inline-template


==== 9 - Module  =======================================================

- Module in itself is like a complete feature. 
- eg: User Authentication - consisting of login, logout, signup, etc. components

- Modules are not reusable like components bcoz we might end up dupliacting services,etc.

- CMD : ng g module user-auth

- Generates only one file.

== Why do we need to make Module? We can simply make Login,logout, etc as different components.
Ans: 
- Code is more structured. 
- If all components are present inside 'app' instead of using modules, unnecessarily all components are loaded.




==== 10 - Function call =======================================================

- Since we declare the function inside a JS class, we don't use the keyword 'function' while defining it.

=> Binding function to a button :

<div class="content" role="main">
  <button (click)="getName()">Click Me</button>
</div>

export class AppComponent {
  title = 'Helloworld';
  data = 'nikhil';
  getName() {
    alert('function called');
}

- When parameters need to be passed use 'any': 

export class AppComponent {
  title = 'Helloworld';
  data = 'nikhil';
  getName(name: any) {
    alert(name);
  }
}

- In Angular 9,10,11 there was no need to assign data type to parameters. But now the "strict: true" in tsconfig.json


===> Style priority :

- Suppose if you add CSS in different files i.e at global level, comp. level, etc. then below priority is followed:

1. Internal CSS - Highest priority : CSS written in the HTML file itself in <style> tag or inline.
2. Component style - CSS written in Component's CSS file.
3. Global style 


=== Property Binding ==========================================

- helps you set values for properties of HTML elements or directives
- Works with Boolean values efficiently 
- While as Interpolation works with numeric and string values.
- Interpolation considers 'true' as string not boolean



=== Passing Data from PARENT compponent to CHILD component =======================================

1. Declaring data to be passed in app.ts :


@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css'],
})
export class AppComponent {
  title = 'CodeSandbox';
  data = 10;
}

-------------------------------------------------------------------

2. Using @Input in child.ts :

import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css'],
})
export class ChildComponent {
  @Input() item = 0;
}

-------------------------------------------------------------------

3. Sending data from Parent to child by binding it in app.html :

<div class="content" role="main">
  <h1>{{title}}!</h1>
  <app-child [item]="data"></app-child>
</div>

-------------------------------------------------------------------

4. Displaying it in child.html :

<p>child : {{item}}</p>

-------------------------------------------------------------------


== Passing Data from CHILD to PARENT :

1. Create a function in app.ts file.

export class AppComponent {
  title = 'CodeSandbox';

  updateData(item: string) {
    console.log(item);
  }
}


2. Use the child comp. in Parent comp. and pass the function created in app.ts into child component. app.html

// === We can name the event anything but we have to pass "$event" inside it only.

<div class="content" role="main">
  <h1>{{title}}!</h1>
  <app-child (updateDataEvent)="updateData($event)"></app-child>  
</div>

3. Create Output decorator in CHILD component child.ts

export class ChildComponent {
  @Output() updateDataEvent = new EventEmitter<string>();
}

4. Call that function in child.html

<input type='text' #box>
<br> <br>
<button (click)="updateDataEvent.emit(box.value)">Update value</button>


--=============== Template Reference Variable ======================================

- The way we assign "id" to html elements in Angular.
- We can access all attributes of that element using it.



AICID000000000000072 RIGT1713


--=============== Custom Pipes ======================================

- CMD : ng generate pipe usdInr


--=============== Forms ======================================

- Forms are used to store any kind of data into DB.
- Angular cannot connect directly to DB.
- We have to use API to store data into DB.

=> Types:

1. Template-driven form - Most of code/validation is written in "app.html" template/file.

2. Reactive form - Most of code/validation is written in "app.ts" file.

- We use "ngModel" to bind the input fields with form. Thus the Angular form knows how many fields are there.




--=============== Directives ======================================

- *ngIf, *ngFor are directives.
- They are classes which gives extra features/properties to our HTML elements. Like hide element.



--=============== Services ======================================

- Service is a class which contains some functions, data, etc. which can be shared with multiple components throughout the app.







