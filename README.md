
# Opinionated naming conventions for angular (< 2.x) application development

### Application namespace
> NOTE: Angular 2.0 drops angular#module() syntax and replaces it with [ES6 modules](http://exploringjs.com/es6/ch_modules.html). Using namespaces as you know them from other languages (concepts often ported from java) will be therefore obsolete.

- Per the above use simple name unique in your application portfolio. _If you are forced by guidelines, use enterprise domain namespace_
- Example: `lowtatras`
- Use as: 
    - Module namespace.  
- Do not use:
    - As namespace for services.    


### Application prefix
- Derived from your application namespace.
- Keep it short.
- Do not use `ng`, `$`, `ui`, `uib`.
- Example: `lt` (derived from `low tatras`).
- Use as:
    - Controller prefix `LtHomeCtrl` (PascalCase).
    - Service prefix `ltModel`.
    - Directive prefix `ltCard`.
    - Filter prefix `ltValue`.
    - Constant prefix `LT_HIGHEST_POINT`.
- Do not use:
    - In directory or file names.    


### Annotated structure    
- Example application prefix (long form): `lowtatras`
- Derived prefix for directives, filters and services (short form): `lt`
- Derived prefix for controllers and object constructors: (short form first character uppercase)`Lt`

```
.
├── app/
│   ├── main/                           -- logical grouping
│   │   ├── controllers/
│   │   │   ├── LtMainCtrl.js           -- controller names always use PascalCase with Ctrl postfix
│   │   │   └── LtHeaderCtrl.js
│   │   ├── services/
│   │   │   ├── ltServiceName.js        -- service names cammelCase
│   │   │   │                           -- angular.module('lowtatras.main').service('ltServiceName', ...)
│   │   │   └── LtModel.js              -- except if they are object constructors - PascalCase
│   │   ├── directives/
│   │   │   └── ltFoo/                  -- folder names cammelCase
│   │   │       ├── ltFoo.js
│   │   │       └── ltFoo.html          -- directive templates carry the same name as coresponding js file
│   │   │                               -- keep them close to the directives
│   │   ├── filters/
│   │   ├── templates/                  -- module templates
│   │   │   ├── partials/
│   │   │   └── main.html               -- entry route view
│   │   └── index.js                    -- angular.module('lowtatras.main', []);
│   │               
│   ├── common/                         -- contains common reusable stuff on application level
│   │   ├── services/   
│   │   ├── filters/    
│   │   │   └── ltFilterName.js         -- angular.module('lowtatras.common').filter('ltFilterName', ...)
│   │   │                               -- filters use cammelCase names
│   │   └── index.js                    -- angular.module('lt.common', []);
│   │   
│   ├── panoramaView/                   -- long name cammelCase
│   │   ├── controllers/    
│   │   │   └── LtLongNameCtrl.js       -- controller with long name
│   |   └── index.js                    -- angular.module('lowtatras.panoramaView', ['lowtatras.common']);
│   │           
│   ├── search/                 
│   │   ├── controllers/    
│   │   │   └── LtSearchCtrl.js          
│   │   ├── templates/
|   |   |   ├── advanced-search.html    -- templates can be hyphen-separated 
│   │   │   └── search.html 
│   │   └── index.js                    -- angular.module('lowtatras.search', []);
│   │       
│   └── app.js                          -- angular.module('ltApp', ['lowtatras.main', 'lowtatras.panoramaView', ...]);
│                                       -- use either prefix in short form
│
├── styles/
│   ├── moduleName
│   │   ├── _foo.scss
│   │   └── _long-name.scss
│   └── styles.scss
├── fonts/
├── assets/                             -- any sort of static assets, images, etc.
├── index.html                          -- ng-app="ltApp"
└── landscape-view.html                 -- names of directly accessible assets hyphen-separated 
```