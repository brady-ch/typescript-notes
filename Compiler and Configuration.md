# Compiler and Configuration

## tsconfig.json
This file is where you configure which typescript files are to be compiled. You can use wildcards for paths.
 
### Basic Properties
 
| Properties | Use | 
|---|---|
| exclude | Use this to exclude a file(s) during compilation, node_modules is excluded by default, however if you add a file to exclude you must add all files to exclude. So this means that you must add node_modules if you choose to use this property |
| include | Use this to include a file(s) during compilation. |
| files | Use this to point at individual files,  similar to include however you cannot specify entire folders using the files property. |
 
### Compiler Options
Options for compiler behavior

Below are some common options that you may use

| Option | Description |
|---|---|
| target | Enabled by default, this option will tell typescript what you want to compile the code into. You can use this to generate code that works in older browsers as well as newer ones. |
| module | TODO |
| [[#lib]] | If not set some defaults are assumed which are basically what you would need to have typescript run in the browser. If you add these yourself you can add things like "dom" which will give you access to the dom.   |
| allowJs | You can allow Javascript files to be compiled |
| checkJs | This will check the js file for potential errors, but will not compile it. |
| sourceMap | If you set this to true, it will generate .js.map files which will allow you to see your typescript files within the browser which can help with debugging. |
| outDir | You can use this to configure where you want the output .js files to be placed so they are not all placed next to each other. |
| rootDir | You can use this to set which folder you want the typescript compiler to compile. |
| removeComments | Will remove comments when the code is compiled, this will make your files smaller. |
| noEmit | This is if you do not want to create an output file. May be useful if you want to check for errors and not create an output file. |
| downLevelIteration | Gives a more exact compilation which may be needed for older versions. There are some niche cases when working with loops where you may run into errors with this off, however it creates more verbose code, so leave it off unless needed. |
| noEmitOnError | Will not compile your files and emit the corresponding .js file while errors remain.  |
 
 Strict Options
 
 | Option | Description | 
 |---|---|
 | strict | Enables all strict type checking options |
 | noImplicitAny | Ensures we have to be clear about our parameters and types, it will not intuit and `any` type |
 | strictNullChecks | Enables Typescript to be strict on possible null values |
 | strictFunctionTypes | Enables Typescript to be strict with function types |
 | strictBindCallAndApply | It will check to make sure that "bind", "call" and "apply", it will type check to make sure the arguments for those make sense. |
 | strictPropertyInitialization | TODO |
 | noImplicitThis | Typescript will warn you if when you are using this it is not clear what you are referring too |
 | alwaysStrict | Controls that the javascript files that are generated are using strict mode |
 
 Additional Checks
 
| Option | Description |
|---|---|
| noUnusedLocals | Will check for unused local variables |
| noUnusedParameters | Will check for unused parameters |
| noImplicitReturns | You will get an error if you have a function that doesn't always return something. |
| noFallthroughCasesInSwitch | Basically checks if you are missing a break statement in a switch |

 
 #### lib
 The below is set by default so you have access to some common Javascript features.
 ```typescript
 "lib": [
"dom",
"es6",
"dom.iterable",
"scripthost"
 ]
 ```