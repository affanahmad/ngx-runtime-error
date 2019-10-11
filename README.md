# NGX-Runtime-Error

A library which capture error from your website and notify to your email address.

## Installation

Use the package manager npm to install ngx-runtime-error.

```bash
npm i ngx-runtime-error
```

## Usage

```typescript
import { ErrorHandler } from '@angular/core';
import { isDevMode } from '@angular/core';
import { NgxRuntimeError } from 'ngx-runtime-error'
class RuntimeError implements ErrorHandler {
  constructor(private ngx_error:NgxRuntimeError) { 
    const params = {
            email : 'YOUR_EMAIL_ADDRESS',
            prodMode : !isDevMode() //for Production
        }
     this.ngx_error.init(params);
  }

  handleError(error) {
    console.error(error)
    this.ngx_error.captureExceptions(error)
  }

}

@NgModule({
  providers: [NgxRuntimeError,{provide: ErrorHandler, useClass: RuntimeError}]
})
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## Links
[GITHUB](https://github.com/affanahmad/ngx-runtime-error), [NPM](https://www.npmjs.com/package/ngx-runtime-error)

## License
[MIT](https://choosealicense.com/licenses/mit/)
