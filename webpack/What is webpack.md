Webpack is simply a tool for bundling modules. 

It is used to compile JavaScript modules. Once installed, you can interact with webpack either from its **CLI** (Command Line Interface) or **API** (Application Programming Interface).

Another amazing feature is webpack’s ability to process and manipulate your code during the compilation step. 

So, for example, if you would like to use **Sass** to write your CSS, webpack can do that for you. Webpack can manage your images and compress and optimize them for use on the web. Webpack can **minify and uglify** your code.

-------------------------------------------------------------------------------------------------------------
When writing programs we need to run `npm run build` to save the current state of the program in order to see it on our actual webpage. 

This can be seen in the `package.json` file as

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack"
  },
```

If this step is not done the changes made will not show up on the website.



