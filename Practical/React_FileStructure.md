# React Folder Structure



`src` folder: where all of the main codes go.

- assets: images, svg, global.css ...
- components: share components (presentational components give state render contexts)
- context: off context
  - `__test__`
- data: json files you have.
- hooks: hook functions
- pages: all pages, and each sub-folder has own components
- utils: utility functions (pure functions)





`src` folder: where all of the main codes go.

- assets
- components
- context
- data
- features: contains subfolders for page. mini version of src folder for service. `index.js` contains all the exported files.
- hooks
- layouts: for components that laying things out so like: `navbars sidebars footers`
- lib: pull in a lot of third-party libraries, (wrap the third-party library)
- pages: individual files for each pages instead of folder structure
- services: integrating with apis.
- utils