# Ionic project and code style guidelines
    
## Introduction
This is the style guide defined by Okode for the development of apps with Ionic / Angular.

## Project layout

```
└── src
    ├── app
    │   ├── app.component.ts
    │   ├── app.html
    │   ├── app.module.ts
    │   └── main.ts
    │   
    ├── pages           |
    ├── components      |
    ├── directives      |    (Ionic/Angular pieces: create using generator)
    ├── pipes           |
    ├── services        |
    │
    ├── models
    ├── utils
    │
    ├── assets
    ├── theme
    └── index.html
```

## Lazy pages / modules
TODO

## Generator
TODO

### Pages
`@IonicPage`

>```
>$ npm run okode:generator page my-page
>```
>```
>└── pages
>    └── my-page
>        ├── my-page.html
>        ├── my-page.module.ts
>        ├── my-page.scss
>        └── my-page.ts
>```

· [IonicPage Doc](https://ionicframework.com/docs/api/navigation/IonicPage/)<br>
· [IonicPageModule Doc](https://ionicframework.com/docs/api/IonicPageModule/)

### Components
`@Component`

>```
>$ npm run okode:generator component my-component
>```
>```
>└── components
>    └── my-component
>        ├── my-component.html
>        ├── my-component.module.ts
>        ├── my-component.scss
>        └── my-component.ts
>```

· [Angular Component Doc](https://angular.io/api/core/Component)


### Directives
`@Directive`

>```
>$ npm run okode:generator directive my-directive
>```
>```
>└── directives
>    └── my-directive
>        ├── my-directive.module.ts
>        └── my-directive.ts
>```

· [Angular Directive Doc](https://angular.io/api/core/Directive)

### Pipes
`@Pipe`

>```
>$ npm run okode:generator pipe my-pipe
>```
>```
>└── pipes
>    └── my-pipe
>        ├── my-pipe.module.ts
>        └── my-pipe.ts
>```

· [Angular Pipe Doc](https://angular.io/api/core/Pipe)

### Services
`@Pipe`

>```
>$ npm run okode:generator services my-service
>```
>```
>└── services
>    └── my-service
>```

## Models
TODO

## Model-Forms (extra tool)
TODO

