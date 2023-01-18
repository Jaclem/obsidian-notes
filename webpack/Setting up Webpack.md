To setup a webpack environment we must first initialize `npm` and then install `webpack` and `webpack-cli`
The `--save-dev` means that we're saving dependencies

```bash
npm init -y
npm install webpack webpack-cli --save-dev
```

Once that is done we should see some of the following files have been added

The colorless files are the ones that our install created 
The ones in green are the ones we will create.
```diff
  webpack-demo
+ |- /dist
	|- main.js
+	|- index.html
+ |- /src
+   |- index.js
  |- node_modules
  |- package.json
  |- package-lock.json
+ |- webpack.config.js
```

We should now open up the `package.json` file and remove "test" and add in "build": "webpack"

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack"
  },
```

We will now create a file called `webpack.config.js` 

```javascript
const path = require('path');

module.exports = {
	mode: 'development',
	entry: path.resolve(__dirname, 'src/index.js'),
	output: {
		path: path.resolve(__dirname, 'dist'),
		filename: 'main.js',
	},
}
```

After this process is set up we can use `npm run build` in our terminal to build out our `main.js` file

Now we need to update our `index.html` file by adding in `<script src="main.js"></script>`

```html
 <!DOCTYPE html>
 <html>
   <head>
     <meta charset="utf-8" />
     <title>Getting Started</title>
	 <script src="https://unpkg.com/lodash@4.17.20"></script>
   </head>
   <body>
    <script src="main.js"></script>
   </body>
 </html>
```

-------------------------------------------------------------------------------
## Loaders & Sass Compiling

Loaders can be used to load *images, css, sass* 

we can run `npm i -D sass style-loader css-loader sass-loader` 
This command is saying npm install loaders as dependencies 

We can now create a sass folder in our `src` folder
Then we'll create a `main.scss` file inside of that

```diff
  webpack-demo
  |- /dist
	|- main.js
	|- index.html
  |- /src
+   |- /style
+     |- main.scss
    |- index.js
  |- node_modules
  |- package.json
  |- package-lock.json
  |- webpack.config.js
```

From here we can import the file inside our `index.js` file

```javascript
import './styles/main.scss'
```

We can now come back to our `webpack.config.js` file and set up the loaders to work

When adding loaders we will add a `module` object
We'll then put in a rules array with an object inside that for each file type I.E *Loaders*

```javascript
  module: {
    rules: [
      {
        test: /\.scss$/,
        use: [
          'style-loader',
          'css-loader',
          'sass-loader'
        ],
      },
    ],
  },
};
```

The regular expression being used `/\.scss$/,` means that any file that ends with this extension scss we're going to apply these loaders

After this is added and saved we can use `npm run build` again to set everything up

## Loading Images

We can now go back to our `webpack.config.js` file and add in the below code
**note** 
`The commented out code is just the code we put in for the css-loaders it should **NOT** be commented out in the actual file`

```javascript
      //{
        //test: /\.scss$/,
        //use: ['style-loader','css-loader','sass-loader'],
      //},
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: 'asset/resource',
      },
```

Images can now be added to the `/src` folder

```diff
  webpack-demo
  |- node_modules
  |- package.json
  |- package-lock.json
  |- webpack.config.js
  |- /dist
	|- main.js
	|- index.html
  |- /src
    |- /style
      |- main.scss
    |- index.js
+   |- icon.png
```

In our `index.js` file we can import the icon from the folder and use it in our program

```javascript
import Icon from './icon.png';

const myIcon = new Image();
myIcon.src = Icon;

element.appendChild(myIcon);
```

-------------------------------------------------------------------------------
## HTML Webpack Plugin

One reason we would download the html webpack plugin is that if we delete the `dist` folder with the `main.js` and `index.html` files in them once we run the `npm run build` command it will rebuild these folders to keep everything running inside our environment. 

First we'll need to run `npm i -D html-webpack-plugin`

First we can add this piece of code to our `webpack.config.js` file

```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin');
```

We'll then add this piece of code under our `module` object 

```javascript
  plugins: [
    new HtmlWebpackPlugin ({
      title: 'webpack App',
      filename: 'index.html',
      template: 'src/template.html',
    }),
  ],
```

The last piece of this code is the `template: 'src/template.html'` and this basically keeps track of a template that we can create in our source folder so that when the html file in `/dist/index.html` gets rebuilt and gets wiped of all its contents it can refer to the template that has all of the information that we have added.

We can then add the template.html file in our src folder
```diff
  webpack-demo
  |- /dist
	|- main.js
	|- index.html
  |- /node_modules
  |- /src
    |- /style
      |- main.scss
    |- index.js
    |- icon.png
+   |- template.html
  |- package.json
  |- package-lock.json
  |- webpack.config.js
```

### last step

We also need to add `clean: true` to our `webpack.config.js` file so that when we run `npm run build` it doesn't put another `main.js` file on top of our pre-existing `main.js` file

```javascript
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'main.js',
    clean: true,
  },
```


-------------------------------------------------------------------------------

## Adding a dev server

We can create a dev server so that we don't have to use the live share on VS Code anymore

We must first open up the `package.json` file and add in this piece of text `"dev": "weback serve`

```javascript
 "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack",
    "dev": "webpack serve"
  },
```

Next we'll run `npm run dev` instead of `build`

-------------------------------------------------------------------------------

## Source maps

Source maps are a handy way to track down which source file (index.js, a.js, b.js) an error is coming from when you use webpack to bundle them together.

We can go over to our `webpack.config.js` and add this line `devtool: 'source-map',`

```javascript
module.exports = {
  mode: 'development',
  entry: path.resolve(__dirname, 'src/index.js'),
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'main.js',
    clean: true,
  },
  devtool: 'source-map',
```

-------------------------------------------------------------------------------
## Asset Resource Loader

The asset resource loaders will allow us to load in different images and fonts into our JavaScript
This functionality comes with webpack by default so we just need to define what we want in our `webpack.config.js` file

```javascript
  module: {
    rules: [
      { // loader for scss
        test: /\.scss$/,
        use: ['style-loader','css-loader','sass-loader'],
      },
      { // letting webpack know that we want to use different image types
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: 'asset/resource',
      },
      { // letting webpack know that we want to use different font types
        test: /\.(woff|woff2|eot|ttf|otf)$/i,
        type: 'asset/resource',
      },
    ],
  },
```

We should also update the `output:` so that the images we put into our code will have the same name always.

We will add `assetModuleFilename: '[name][ext]'` inside the `output:`

```javascript
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'main.js',
    clean: true,
    assetModuleFilename: '[name][ext]',
  },
```

Now we can add images to a folder we will call `assets` 

```diff
  webpack-demo
  |- /dist
	|- main.js
	|- index.html
  |- /node_modules
  |- /src
+   |- /assets
+     |- imageName.jpeg
    |- /style
      |- main.scss
    |- index.js
    |- icon.png
    |- template.html
  |- package.json
  |- package-lock.json
  |- webpack.config.js
```

If we run `npx webpack --watch` we will not have to rerun webpack every time we make a change