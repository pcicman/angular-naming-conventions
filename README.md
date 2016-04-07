
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
│   │   │   │                           -- optimally new module per file
│   │   │   │                           -- module dependencies shall be close to the required
│   │   │   └── LtHeaderCtrl.js
│   │   ├── services/
│   │   │   ├── ltServiceName.js        -- service names cammelCase
│   │   │   │                           -- angular.module('lowtatras.main').service('ltServiceName', ...)
│   │   │   └── LtModel.js              -- except if they are object constructors - PascalCase
│   │   ├── directives/
│   │   │   └── ltFoo/                  -- folder names cammelCase for complex directives
│   │   │       ├── ltFoo.js
│   │   │       └── ltFoo.html          -- directive templates carry the same name as coresponding js file
│   │   │                               -- keep them close to the directives
│   │   ├── filters/
│   │   ├── views/                      -- module views
│   │   │   ├── partials/
│   │   │   └── main.html               -- entry route view
│   │   └── index.js                    -- angular.module('lowtatras.main', []);
│   │               
│   ├── common/                         -- contains common reusable stuff on application level
│   │   ├── constants/                  -- top level application constants
│   │   │                               -- own module
│   │   │                               -- angular.module('lt.common.constants', []);
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
│   │   ├── views/
|   |   |   ├── advanced-search.html    -- view file names can be hyphen-separated
│   │   |   |                           -- but keep the naming consistent 
│   │   │   └── search.html 
│   │   └── index.js                    -- angular.module('lowtatras.search', []);
│   │       
│   └── decorators.js                   -- for decoration of 3rd party dependencies
│   └── app.js                          -- angular.module('lowtatras', ['lowtatras.main', 'lowtatras.panoramaView', ...]);
│                                       -- postfix application entry module with `App`
│                                       -- angular.module('ltApp', ['lowtatras', ...]);                                      
│
├── styles/                             -- use common convention
│   ├── moduleName
│   │   ├── _foo.scss                   -- not directly exposed, prefix with _
│   │   └── _long-name.scss
│   ├── styles.scss                     -- entry file
│   └── _variables.css                  -- all application wide variables here
├── fonts/
├── assets/                             -- any sort of static assets, images, etc.
├── index.html                          -- ng-app="ltApp"
└── landscape-view.html                 -- names of directly accessible assets hyphen-separated 
```