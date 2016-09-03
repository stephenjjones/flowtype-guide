# flowtype-guide

### Overview

* Allows for gradual typing
* Flowtype does not prevent you from running code with type errors

### Flowtype vs Typescript

* Flowtype is a static type checker, not a compiler (Typescript is a compiler)
* Typescript offers an end to end solution
  - could use with babel by compiling first to es6, but cannot get benefit of all babel plugins
  - does not support features in stage-2

### Setup

* Install flow and create a config file
```bash
$ touch .flowconfig
or 
$ flow init

$ npm install --save-dev flow-bin
```

* add `//@flow` to the top of any files to be checked
* run flow `$ npm run-script flow`
* babel integration
```bash
$ npm install -g babel-cli
$ npm install --save-dev babel-plugin-transform-flow-strip-types
$ echo '{"plugins": ["transform-flow-strip-types"]}' > .babelrc
```
* You can now simply run the transpiler in the background using the babel command: 
  - `$ babel --watch=./src --out-dir=./build`

### Annotations

* Annotation types
  - `string`
  - `number`
  - `Array<number>`
  - `any` is a special type annotation that represents the universal dynamic type
  - [Predicate types]
  - [exact types]
* examples
```js
function add(num1: number, num2: number): number {
  return num1 + num2;
}
var x: number = add(3, '0'); // ERROR!
```

### Flow Config

```
[include]
../externalFile.js
../externalDir/
../otherProject/*.js
../otherProject/**/coolStuff/
``` 

### Misc

### Editor integration

* [vim plugin](https://github.com/flowtype/vim-flow)
* [atom/nuclide integration](https://nuclide.io/docs/languages/flow/)


### Resources

* [flowtype docs](https://flowtype.org/docs/getting-started.html#_)
* [javaScript Air Episode 038: Typed JavaScript with TypeScript and Flow](https://www.youtube.com/watch?v=Qiqsg02nXFE)
* [flow talk by Jeff Morrison](https://www.youtube.com/watch?v=9U4_hlnaFEE)
