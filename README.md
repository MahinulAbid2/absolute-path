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


# Absolute paths in 
