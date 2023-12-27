# Absolute path/module-alias in General
can normally be created using `jsconfig.json`. 
```javascript
// file name : jsconfig.json , file name has to be same.

{
  "compilerOptions" : {
    "baseUrl" : "./",
    "paths"  : {
      "@components/*" : ["./src/components/*"]  // using * is important, it means select all 
    } 
  }
}



// in other file while importing,
import { components } from "@components/components.jsx";
```

<br>
<br>
<br>


# Absolute paths in react using vite.
* Vite uses `jsconfig.json` or `tsconfig.json` for TypeScript projects for aliasing similarly to JavaScript projects.
* However, Vite also supports `alias configuration` in its own config file `(vite.config.js)` directly:
```javascript
// filename : vite.config.js
// this file will be created automatically when creating react boilerplate with vite


import { defineConfig } from 'vite';

export default defineConfig({
  // Other Vite configurations...
  resolve: {
    alias: {
      '@ui': '/src/ui',               // notice that no use of * in here.
      '@moduleUI': '/src/moduleUI'   // notice that no use of * in here.
      // NOTE: also "./" this can't be used for some reason. I'll research later. only use "/" not "./"
    }
  }
});

```

<br>
<br>
<br>

# Working with path in Node.js
Up above, those rules, might not work with NODE.JS or EXPRESS.JS
* node.js has built in module like `path` to handle directories and path.
* <ins> I tried it and couldn't understand how to make absolute path with it </ins>
* I found a solution.
* In node.js or express.js, there is a package name `module-alias`. To install it:
```console
npm install module-alias
```

<br>

* <ins>Next Step: </ins> Open `package.json` file and in there, put this :
```json
"_moduleAliases": { 
  "@root"      : ".", 
  "@controller"      : "src/controller", 
  "@my_module" : "lib/some-file.js", 
  "something"  : "src/foo"
}

```
Now there is an module alias named `@controller`, `@mymodule`, `something`.

<br>

* In order to use this module in project file/code I have to `require` - `module-alias` in  project file.
```javascript
const fs = require( 'fs' );
require('module-alias/register')  // have to require it where I want to use "module-alias"

const { UpdateDB } = require ( '@controller/shopController'); 
```

