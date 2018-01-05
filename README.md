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

### Components
TODO

### Directives
TODO

### Pipes
TODO

### Services
TODO

## Models
TODO

## Model-Forms (extra tool)
TODO

