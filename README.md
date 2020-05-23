# ParcelJS Template
A bare-bones template repo for TypeScript projects compiled and bundled using ParcelJS

## Using ParcelJS
_This has already been done in this project_
1. Add ParcelJS to your project using  
`npm i parcel-bundler --save-dev`
2. In your main .html file add a script tag referencing you entry file  
`<script src="./index.ts"></script>`
3. In your terminal run  
`parcel index.html` _or whatever your html file is called_  
to build and run or  
`parcel build index.html`  
to build only but with smaller minified code  
4. Run  
`parcel build index.html --no-source-maps`  
to prevent the inclusion of sourcemaps

That's it!
Parcel will create a local dist/ folder in which it will deposit a bundled, transpiled, and minified copy of your code. Source maps will be included. HTML and CSS files will be copied there as well. All files will be appended with a hash and the main .html file script tag will be updated to point to the bundled JS code.

## NPM scripts
Optionally add the following npm scripts to make development easier:  
1. For building and running  
`"dev": "parcel index.html"`
2. For deleting the dist folder before building and running (Windows)  
`"predev": "del -r dist"`  - Windows (requires confirmation)  
`"predev": "rd /s /q dist"`  - Windows (does not require confirmation)  
`"predev": "rm -rf dist"`  - Unix  
This will be run automatically when calling `npm run dev`
3. For building  
`"build": "parcel build index.html"` (optionally add ` --no-source-maps` to exclude source maps) 
4. For deleteing the dist folder before building (Windows)  
`"prebuild": "del -r dist"`  - Windows (requires confirmation)  
`"prebuild": "rd /s /q dist"`  - Windows (does not require confirmation)  
`"prebuild": "rm -rf dist"`  - Unix  
Will be run automatically when calling `npm run build`

Currently the template includes the following two scripts as described above:  
`npm run dev`  
and  
`npm run build`

## Resource folder
If you have a resource folder that also needs to be copied into the dist folder then install the following npm package  
`npm i parcel-plugin-static-files-copy --save-dev`
Then, to copy the resource folder over you'll need to add the following to your package.json  
```json
"staticFiles": {
    "staticPath": [
      {
        "staticPath": "resources",
        "staticOutDir": "resources"
      }
    ],
    "watcherGlob": "**"
  },
```
Where the `staticPath` is the path the path to the source resources and `staticOutDir` is the path in which to place them relative to the dist folder.  
So with the above settings the contents of our root level `resources` folder will be copied into `dist/resources`
