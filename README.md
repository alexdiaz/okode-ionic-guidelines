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
> `@IonicPage`
```
$ npm run okode:generator page new-page
```
```
└── pages
    └── new-page
        ├── new-page.html
        ├── new-page.module.ts
        ├── new-page.scss
        └── new-page.ts
```
· [IonicPage Doc](https://ionicframework.com/docs/api/navigation/IonicPage/)<br>
· [IonicPageModule Doc](https://ionicframework.com/docs/api/IonicPageModule/)

### Components
> `@Component`
```
$ npm run okode:generator component new-component
```
```
└── components
    └── new-component
        ├── new-component.html
        ├── new-component.module.ts
        ├── new-component.scss
        └── new-component.ts
```
· [Angular Component Doc](https://angular.io/api/core/Component)


### Directives
> `@Directive`

>```
$ npm run okode:generator component new-component
```
```
└── components
    └── new-component
        ├── new-component.html
        ├── new-component.module.ts
        ├── new-component.scss
        └── new-component.ts
```
· [Angular Directive Doc](https://angular.io/api/core/Directive)

### Pipes
TODO

### Services
TODO

## Models
TODO

## Model-Forms (extra tool)
TODO

