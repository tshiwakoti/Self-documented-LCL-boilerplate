# Self documented LCL boilerplate

Since `Linked Code Library (LCL)` uses GitHub to store code, it's been decided that we could also use GitHub pages to store automatically generated documentation of the code as a good API reference. 
Auto-generated documentation uses [JSDoc3](http://usejsdoc.org/index.html) (make sure you check their [documentation](http://usejsdoc.org/index.html)) inline code comments as a source for documentation and generates HTML files that have hyperlinks and examples of the code.
Further after generating the code, it may be stored on GitHub pages. 

Current configuration doesn't analyse the code, since JScript isn't recognized as a valid JavaScript by the interpreter that reads the code, thus it only analyses comments for the code, so anything you don't describe won't appear in the documentation.
Besides, Reportal doesn't know anything about files in nested folders, so all code will have to be stored in the root folder for LCL to work in Reportal, though it's an advantage, because Reportal won't treat documentation files as Reportal code.

## Install

Make sure you have `npm` (Node.JS) and `Git` installed on your machine.
Clone this repository into your empty project and configure `package.json` for it. Basically you need to change fields `name`, `version`, `description`, `repository.url`, `author`, `description` and `homepage`
Keep note, that all documentation when generated resides in `./docs/name/version` relative to the root (where `package.json` is). So you also need to configure `"docs-commit": "git subtree push --prefix docs/YOUR_PROJECT_NAME origin gh-pages"` in `package.json` by replacing `YOUR_PROJECT_NAME` with whatever you specified in the `name` section of the config.

Then you need to configure `jsdoc.conf` that does all documents generation. You need to add filenames with extentions (relative to the`jsdoc.conf`) to the array in `source.include`. 
Only these files will be documented. It's good practice to leave `README.md` and `package.json` included. Thus `README.md` will be displayed as a homepage.

When all this is done you're good to initialize your boilerplate by executing `npm install` in command line (assuming you've already navigated to your project folder in command line). Now your project is set up.

## Comment

Make sure you read [JSDoc3 documentation](http://usejsdoc.org/index.html) and take a look at the source code of our example file [`JSON_exampleClass.js`](https://confirmitasa.github.io/Self-documented-LCL-boilerplate/0.1.0/JSON_exampleClass.js.html) and the [output docs](https://confirmitasa.github.io/Self-documented-LCL-boilerplate/0.1.0/JSON.html) to get an idea how to document Reportal Scripting code.
Since JSDoc is tuned not to read the code, only comments, you need to be as explicit as necessary for JSDoc to understand what exactly your function does. So you might need to be more descriptive than you would be describing generic JavaScript code.

## Generate

To generate docs for the project execute `npm run docs` in command line interface

## Publish

To publish docs to github pages you need first to commit and push tags of your projects to GitHub, so that your `master` branch is up-to date with the freshly generated docs. 
If you've changed version in your `package.json`, JSDoc has generated a new set of docs for this version and out the into the `docs/projectName/` folder. 
Be sure to add those to Git and commit them before publishing to GitHub pages.

If that's done, publish to github pages by executing `npm run docs-commit` in command line interface. CLI will ask you for your GitHub username and password, make sure you provide those.

If you've done everything correctly, your docs will be at `http://USERNAME.github.io/PROJECT_NAME/VERSION/`. As an example, the docs for this boilerplate are here: [http://ConfirmitASA.github.io/Self-documented-LCL-boilerplate/0.1.0/](http://ConfirmitASA.github.io/Self-documented-LCL-boilerplate/0.1.0/)
