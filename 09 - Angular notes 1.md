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
