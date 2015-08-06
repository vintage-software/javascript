#TypeScript Style Guide

TypeScript is a statically typed super set of JavaScript (ES6/ES7). TypeScript follows all the same standards 
as the [JavaScript Style Guide](https://github.com/vintage-software/javascript). Currently we keep types to a minimum and stay close to the standard ES spec using TypeScript as our preferred transpiler.

Note TypeScript is compile time type checking. At runtime your ES6 Classes can be altered by their prototype and or object properties. 

## Class Primitive Properties

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

## Injected Services and Classes
Injected services should be typed by their imported class.

``` typescript
import {Inject} from 'angular2/di';
import {ApiService} from 'app/services/common/api.service';
import {ErrorsService} from 'app/services/common/errors.service';

export class AuthenticationService {
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

## Data Objects and DTOs
Simple objects such as data transfer objects (DTOs) can by typed to the `any` option to allow 
the most flexibility when working with data. 

``` typescript
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

## Classes

ES6 Classes and ES7 Decorators can be used but advoid using TypeScript keywords such as `private` and `public`. This may change in the future but currently we would like to stay close to the ES spec as possible. 

## Interfaces

Try to advoid using interfaces for now as we preffer staying to the ES spec as closely as possible. This may change in the near future depending on the ES spec process of new features. 

## TypeScript Definition Files

Include TypeScript Definition Files to allow standard JavaScript libraries to be statically typed and allow improved intellisense with the IDE. See [http://definitelytyped.org/](http://definitelytyped.org/) and [http://definitelytyped.org/tsd/](http://definitelytyped.org/tsd/) for more information on how to get started.
