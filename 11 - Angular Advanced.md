# Reactive Forms :

### Why not use a normal HTML form ?

- 

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
