#TypeScript Style Guide (In Preview)

TypeScript is a statically typed super set of JavaScript (ES6/ES7). TypeScript follows all the **same** standards 
as the [JavaScript Style Guide](https://github.com/vintage-software/javascript). TypeScript can infer types
so it is not nessesary to add type annotations everywhere. Be pragmatic if adding additional type annotaions.

**Note** TypeScript is compile time type checking. Advoid altering you Classes or Prototypes at runtime. 

1. [Classes](#classes)
2. [Functions](#functions)
3. [Interfaces](#interfaces)
4. [TypeScript Definition Files](#typescript-definition-files)
5. [Non Standard ECMAScript Features](#non-standard-ecmascript-features)
6. [Installation](#installation)

## Classes

ES6 Classes and ES7 Decorators can be used. Unlike our JavaScript styleguide private properties and Prototype functions should NOT be prefixed with `_`. Use the private keyword provided by TypeScript. Example: `private myPrivateProperty`

### Class Primitive Properties

Class level primitive properties should be typed.

``` typescript
export class AuthenticationService {
  private isAuthenticated: boolean;
  private tokenKey: string;

  constructor() {
    this.isAuthenticated = false;
    this.tokenKey = 'accessToken';
  }
}
```

### Dependency Injected Services (Singletons) in Angular 2
Injected services should be typed by their imported class. Make sure to have the 
emitDecoratorMetadata flag turned on for Angular 2 DI to know the type of the injectable service.

``` typescript
// Service
import { Injectable } from '@angular/core';

@Injectable()
export Class ApiService {
    constructor () {
    }
}

// Component
import { ApiService } from 'app/services/api.service';
import { ErrorsService } from 'app/services/errors.service';

export class UIComponent {
  constructor(
    private apiService: ApiService,
    private errorsService: ErrorsService) {

    }
}
```

## Functions
Set parameter types on functions and methods 
```typescript
updateItem(id: number, item: any) {
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
Use Interfaces where appropriate. Do **not** use "I" as a prefix for interface names. [TypeScript convention does not prefix with "I"](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Interfaces.md).

## TypeScript Definition Files

Include TypeScript Definition Files to allow standard JavaScript libraries to be statically typed and allow improved intellisense with the IDE. See the [Typings Project](https://github.com/typings/typings).


## Non Standard ECMAScript Features
This is a list of some of the major TypeScript Features that we use that are non standard to the ECMAScript/JavaScript specification. This is to help a migration away from TypeScript if needed.

- Optional Static Typing. Example: 
```typescript
    function add(num1: number, num2: number) { // ... }
```
 
    
- Interfaces.
```typescript
export interface Team {
  id: number;
  name: string;
  users: Array<User>;
}
```

## Installation
To install TypeScript we recomend installing the latest version from [npm](https://www.npmjs.com/package/typescript).
