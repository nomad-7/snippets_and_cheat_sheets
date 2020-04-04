## control structures
### Switch statement
switch (expression) {
   case constant-expression1: {
      //statements;
      break;
   }
   case constant_expression2: {
      //statements;
      break;
   }
   default: {
      //statements;
      break;
   }
}


### Strings
#### RegExp
* Literal
let regexp: RegExp = /ab+c/;
let regexpNumber: RegExp = /^[+ 0-9]{5}$/;

* calling constructor function
let regexp = new RegExp('ab+c');
let regexpNumber = new RegExp('^[+ 0-9]{5}$');


console.log(regexpNumber.test('12345
// expected output: true
console.log(regexpNumber.test('1234f
// expected output: false
console.log(regexpNumber.test('123456
// expected output: false

* Test an email address
let regexpEmail =   new RegExp('^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}$');
  regexpEmail.test('marco@expertcodebolg.com// expected output: true
  regexpEmail.test('marcoexpertcodebolg.com// expected output: false

* Match string not containing string
let regexpEmail = new RegExp('/^((?!(badstring)).)*$/');
regexpEmail.test('marco@expertcodebolg.com// expected output: true
regexpEmail.test('marcobadstring@expertcodebolg.com// expected output: false



## Variables
`let` `const` `var`
## Functions
### Signature
#### Default parameters value
    funcFoo(someparameter: string = '') {}







       // the next line causes error: queryPath doesn't exist on type string|CategoryId
       // const path = (activeCateg === 'root') ? 'categories' : `${activeCateg.queryPath}`;
       let path = '';
       if (typeof(activeCateg) !== 'string') {
         path = `${activeCateg.queryPath}/children`;
       } else {
         path = 'categories';
       }

debugger

{{ item | json}}

ng-probe($0)  =>>>>
import { enableDebugTools } from '@angular/platform-browser';
import { ApplicationRef } from '@angular/core';
...
platformBrowserDynamic().bootstrapModule(AppModule).then(module => {
  let applicationRef = module.injector.get(ApplicationRef);
  let appComponent = applicationRef.components[0];
  enableDebugTools(appComponent);
})
.catch...
