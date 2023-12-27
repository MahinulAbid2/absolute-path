# Absolute path in General
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
    }
  }
});

```
