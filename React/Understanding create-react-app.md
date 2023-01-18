#### node_modules

This folder is part of the npm system. [npm](https://docs.npmjs.com/files/folders.html) puts local installs of packages in `./node_modules` of the current package root. Basically, the packages you want to use by calling an “import” statement go here.

#### public

This folder contains the `index.html` and `manifest.json` files. Let’s look at the files inside the public folder.

#### manifest.json

This is a [web app manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest) that describes your application, and it’s used by, e.g., mobile phones if a shortcut is added to the home screen**.** Let’s look at the contents to understand it further:

```json
{
  "short_name": "React App",
  "name": "Create React App Sample",
  "icons": [
    {
      "src": "favicon.ico",
      "sizes": "64x64 32x32 24x24 16x16",
      "type": "image/x-icon"
    }
  ],
  "start_url": ".",
  "display": "standalone",
  "theme_color": "#000000",
  "background_color": "#ffffff"
}
```

The contents of this file are pretty self-explanatory. But where are these values used?

When a user adds a web app to their home screen using Chrome or Firefox on Android — or Safari on iOS — the metadata in manifest.json determines what icons, names, and branding colors to use when the web app is displayed. [The web app manifest guide](https://developers.google.com/web/fundamentals/engage-and-retain/web-app-manifest/) provides more context about what each field means, and how your customizations will affect your users’ experience.

#### `package.json`

This file lists the packages your project depends on and [which versions of a package](https://docs.npmjs.com/about-semantic-versioning) your project can use. In tandem with either package-lock.json or yarn.lock (more on these files below), it also makes your build reproducible and, therefore, easier to share with other developers.

This specifies that when you run npmcommands like `npm start`, it will actually run `react-scripts start`

The `index.js` file has the following line:

`ReactDOM.render(<App/>, document.getElementById('root'));`

This line calls ReactDOM’s `render()` method, which renders a React element into the DOM in the supplied container and returns a [reference](https://reactjs.org/docs/more-about-refs.html) to the component. The React element here is the `<App>` component, and the supplied container is the DOM element `root` (which is referenced in `index.html`).