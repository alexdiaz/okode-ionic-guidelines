# Ionic project and code style guidelines
    
This is the style guide defined by Okode for the development of apps with Ionic / Angular.

### Table of contents
- [Project layout](#project-layout)
- [Modules and lazy load](#modules-and-lazy-load)
  * [App Module](#app-module)
  * [IonicPageModule](#ionicpagemodule)
  * [Rest of modules](#rest-of-modules)
- [Generator](#generator)
  * [Pages](#pages)
  * [Components](#components)
  * [Directives](#directives)
  * [Pipes](#pipes)
  * [Services](#services)
- [Models](#models)
- [Model-Forms (optional tool)](#model-forms-optional-tool)


# Project layout

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

# Modules and lazy load
TODO

### App Module
TODO

### IonicPageModule
TODO

### Rest of modules
TODO

# Generator
To use Okode Generator in a Ionic project, package.json needs `@okode/app-scripts` as `devDependencies` and define generator script alias:

```json
{

  "scripts": {
    "okode:generator": "okode-app-scripts generator",
    
  "devDependencies": {
    "@okode/app-scripts": "https://github.com/okode/okode-app-scripts#develop",
    
}
```

**Usage:**<br>
```
$ npm run okode:generator TYPE NAME`
       TYPE must be one of: page, component, directive, pipe, service
       NAME must be lowercase with - separating words: looks-like-this
```


### Pages
`@IonicPage`

```
$ npm run okode:generator page my-page
```
```
└── pages
    └── my-page
        ├── my-page.html
        ├── my-page.module.ts
        ├── my-page.scss
        └── my-page.ts
```

· [IonicPage Doc](https://ionicframework.com/docs/api/navigation/IonicPage/)<br>
· [IonicPageModule Doc](https://ionicframework.com/docs/api/IonicPageModule/)

### Components
`@Component`

```
$ npm run okode:generator component my-component
```
```
└── components
    └── my-component
        ├── my-component.html
        ├── my-component.module.ts
        ├── my-component.scss
        └── my-component.ts
```

· [Angular Component Doc](https://angular.io/api/core/Component)


### Directives
`@Directive`

```
$ npm run okode:generator directive my-directive
```
```
└── directives
    └── my-directive
        ├── my-directive.module.ts
        └── my-directive.ts
```

· [Angular Directive Doc](https://angular.io/api/core/Directive)

### Pipes
`@Pipe`

```
$ npm run okode:generator pipe my-pipe
```
```
└── pipes
    └── my-pipe
        ├── my-pipe.module.ts
        └── my-pipe.ts
```

· [Angular Pipe Doc](https://angular.io/api/core/Pipe)

### Services
`@Injectable`

```
$ npm run okode:generator services my-service
```
```
└── services
    └── my-service.ts
```
· [Angular Injectable Doc](https://angular.io/api/core/Injectable)<br>
· [Angular Dependency Injection Doc](https://angular.io/guide/dependency-injection)


# Models
TODO

# Model-Forms (optional tool)
TODO

