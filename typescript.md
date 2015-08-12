#TypeScript Style Guide (In Preview)

TypeScript is a statically typed super set of JavaScript (ES6/ES7). TypeScript follows all the **same** standards 
as the [JavaScript Style Guide](https://github.com/vintage-software/javascript). Types are optional and use developer disgression of when its apropriate or usefull to use static typing. 

**Note** TypeScript is compile time type checking. Advoid altering you Classes or Prototypes at runtime. 

1. [Classes](#classes)
2. [Functions](#functions)
3. [Interfaces](interfaces)
4. [TypeScript Definition Files](typescript-definition-files)
5. [Non Standard ECMAScript Features](non-standard-ecmascript-features)

## Classes

ES6 Classes and ES7 Decorators can be used but advoid using TypeScript keywords such as `private` and `public`. This may change in the future but currently we would like to stay close to the ES spec as possible. Private properties and Prototype functions should be prefixed with `_`. Example: `_myPrivateProperty`

### Class Primitive Properties

Class level primitive properties should be typed.

``` typescript
export class AuthenticationService {
    _isAuthenticated: boolean;
    _tokenKey: string;

    constructor() {
      this._isAuthenticated = false;
      this._tokenKey = 'accessToken';
    }
}
```

### Injected Services and Classes
Injected services should be typed by their imported class.

``` typescript
import {Inject} from 'angular2/di';
import {ApiService} from 'app/services/api.service';
import {ErrorsService} from 'app/services/errors.service';

export class DataService {
    _apiService: ApiService;
    _errorsService: ErrorsService;

    constructor(
        @Inject(ApiService) ApiService,
        @Inject(ErrorsService) ErrorsService) {

        this._apiService = ApiService;
        this._errorsService = ErrorsService;
    }
}
```

## Functions
Function parameter types are optional. Use at your discretion. 

```typescript
updateItem(id : number, item : any) {
    // ...
}
```

## Data Objects/Structures and DTOs
Data Objects/Structures such as data transfer objects (DTOs) can by typed to the `any` option to allow 
the most flexibility when working with data. Optinally you can define a Interface if the object is either large or widely used in the application.

```typescript
export class TicketsService {
    data: any;

    constructor() {
        this.data = {
            tickets: [],
            ticket: null
        };
    }
}
```

## Interfaces
Use Interfaces where appropriate. Try to keep the code close to the ES spec as possible only using Interfaces when there is a advantage of doing so. Do **not** use "I" as a prefix for interface names.

## TypeScript Definition Files

Include TypeScript Definition Files to allow standard JavaScript libraries to be statically typed and allow improved intellisense with the IDE. See [http://definitelytyped.org/](http://definitelytyped.org/) and [http://definitelytyped.org/tsd/](http://definitelytyped.org/tsd/) for more information on how to get started.


## Non Standard ECMAScript Features
This is a list of some of the major TypeScript Features that we use that are non standard to the ECMAScript/JavaScript specification. This is to help a migration away from TypeScript if needed.

- Optional Static Typing. Example: 
    ```typescript
        function add(num1 : number, num2 : number) { // ... }
    ```
 
- Parameter Decorators (ES7 decorators will supported in the spec but not Parameter Decorators). This is used in Angular 2. Example:
    ```typescript
    constructor(
        @Inject(ApiService) ApiService,
        @Inject(ErrorsService) ErrorsService) {

        this._apiService = ApiService;
        this._errorsService = ErrorsService;
    }
    ```
    
- Interfaces.
    ```typescript
    export interface Team {
        id: number;
        name: string;
        users: Array<User>;
    }
    ```
