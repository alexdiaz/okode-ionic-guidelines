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
- [FormModels (optional tool)](#formmodels-optional-tool)


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
· **App module**: Using IonicModule to bootstraps Ionic App.<br>
· **IonicPageModule**: Lazy modules.<br>
· **Rest of modules**: For each component, directive or pipe, the generator will create its module to be imported into the modules of the pages that need them.<br>

### App Module
`IonicModule` is an `NgModule` that bootstraps an Ionic App. By passing a root component, IonicModule will make sure that all of the components, directives, and providers from the framework are imported.

```typescript
@NgModule({
  declarations: [MyApp],
  bootstrap: [IonicApp],
  entryComponents: [MyApp],
  imports: [
    IonicModule.forRoot(MyApp)
  ],
  providers: []
})
export class AppModule { }
```

### IonicPageModule
`IonicPageModule` is an `NgModule` that bootstraps a child IonicPage in order to set up routing. Load of this module is lazy

```typescript
@NgModule({
  declarations: [ MyPagePage ],
  imports: [
    IonicPageModule.forChild(MyPagePage),
    // Components, directives or pipes modules can be imported here
  ],
})
export class MyPageModule {}
```

### Rest of modules
For each component, directive or pipe, the generator will create its module to be imported into the modules of the pages that need them. These modules can be imported into the `IonicPageModule` (in one or several of them), or only in App Module (if it's going to be used for a large number of pages).

# Generator
To use Okode Generator in a Ionic project, package.json needs `@okode/app-scripts` as `devDependencies` and define generator script alias:

```json
  "scripts": {
    "okode:generator": "okode-app-scripts generator",
  },
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
All models will be interfaces and will be placed in the models folder (see layout). Some model files can have exportable utility functions to transform data.

Example of `models\person.ts`:
```typescript
export interface Person {
  name: string;
  lastname: string;
  email?: string;
  phone?: number;
}

export function getFullName(person: Person) {
  return person.name + ' ' + person.lastname;
}
```

# FormModels (optional tool)
***Strategy used to generate dynamic forms (Angular Form Builder) based on models.*** Used in `iMediador` project.<br>

The objective is not to have to re-map models when building a FormGroup with the Angular FormBuilder and to do it automatically with the use of decorators in the model.<br>

We need:<br>
· [FormModels](https://github.com/okode/imediador/blob/master/app/src/utils/form-models.ts)<br>
· [FormProp decorator](https://github.com/okode/imediador/blob/master/app/src/utils/decorators.ts)


To make this, we need to change model interface to model class, and add decorator to form fields:
```typescript
import { FormProp } from '../utils/decorators';
export class Person {
  id: number;
  @FormProp() name: string;
  @FormProp() lastname: string;
  
  @FormProp([Validators.required, Validators.pattern('[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,3}$')])
  email?: string;
}
```
> A validator or list of validators can be passed to `@FormProp` decorator (like Angular Form Builder). Example:

And to get the `FormGroup` from a page or component:

```typescript
import { FormGroup } from '@angular/forms';
import { Person } from '../../models/person';
import { FormModels } from '../../utils/form-models';

let data = { 'name': 'John', 'lastname': 'Mock' } as Person; // data param to set initial value (optional)
let personForm: FormGroup = FormModels.buildForm(Person, data);
```
```html
  <form [formGroup]="personForm">
    <ion-item>
      <ion-label floating>Name</ion-label>
      <ion-input type="text" formControlName="name"></ion-input>
    </ion-item>
    ...
```


