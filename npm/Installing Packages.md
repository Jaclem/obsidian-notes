The **node package manager** is a command-line tool that gives you access to a gigantic repository of plugins, libraries and tools.

## Installing unscoped packages

Unscoped packages are always public, which means they can be searched for, downloaded, and installed by anyone. To install a public package, on the command line, run

`npm install <package_name>`

This will create the `node_modules` directory in your current directory (if one doesn't exist yet) and will download the package to that directory.

## Installed a scoped public package

**Scoped public packages** can be downloaded and installed by anyone, as long as the scope name is referenced during installation:

`npm install @scope/private-package-name`


## Installing a package with dist-tags

Like `npm publish`, `npm install <package_name>` will use the `latest` tag by default.

To override this behavior, use `npm install <package_name>@<tag>`. For example, to install the `example-package` at the version tagged with `beta`, you would run the following command:

`npm install example-package@beta`



