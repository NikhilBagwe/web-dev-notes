## Service:

- Suppose we have an SAAS application and we have provided "Subscribe" button (which calls the subscription logic and subscribes the user) in multiple components present on the page. Like in header, footer and hero-section. 
- Thus, now we would be required to write the same subscription logic multiple times for multiple components.

![image](https://github.com/NikhilBagwe/web-dev-notes/assets/67143015/a5983721-f74f-4694-81eb-232c84c2da95)

- Following are some Disadvantages of above method: 
1. It violates the DRY principle.
2. Component class should only be responsible for showing UI to the user. It must not contain subscription logic as it is a part of Business logic.

- The solution to above problem is to write the subscription logic in a different centralized file which can be accessed by all components. This can be acheived by using SERVICE in angular.
- A Service is a re-usable TypeScript class that can be used in multiple components across an Angular app.

## Advantages of Service:

- Service allows us to reuse a piece of code in multiple components.
- Helps us to separate UI logic from Business logic.
- Separation of concern is acheived.

---
---

## Creating a Service:

- Create below file

![image](https://github.com/NikhilBagwe/web-dev-notes/assets/67143015/d89c1649-e38c-4e96-8385-3f21c718f291)

### subscribe.service.ts

```js
export class SubscribeService{
    OnSubscribeClicked(type: string){
        alert('Thank you for your '+ type +' subscription. You can access the services now.')
    }
}
```
- Calling the service in multiple components.

```js
import { SubscribeService } from 'src/app/Services/subscribe.service';

export class HeaderComponent {
  //......

  OnSubscribe(){
    //alert("Thank you for subscribing the services.")
  
    // Calling a Service
    let subService = new SubscribeService()
    subService.OnSubscribeClicked('weekly')
  }
}
```

### Note:

- Now here for using the service in a component, we are required to create an instance of the service everytime.
- Thus we have made the component class dependent on service class resulting into TIGHT COUPLING.
- So if service class is removed or modified, it will have an effect on component class.
- Not a good practice.
- Thus, we can ask Angular to inject an instance of this service class into component class i.e DEPENDECY INJECTION. 


















