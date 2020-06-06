# npm-hello-world
A Hello, world! NPM package

This package is an example of an NPM module deployed to the GitHub NPM registry. See how to create and set up a Node.JS application to use such a GitHub NPM registry package like this in [@jlam55555-playground/npm-hello-world-consumer][2].

### Creating the NPM package

##### Authenticating to the GitHub Packages API
See [the GitHub help pages][1] for how to set up and authenticate with a GitHub authentication token (used to connect to the GitHub Packages API). After creating the authentication token, this will look something like (taken from the help page):
```
$ npm login --registry=https://npm.pkg.github.com
> Username: USERNAME
> Password: TOKEN
> Email: PUBLIC-EMAIL-ADDRESS
```
where `USERNAME` is your GitHub username, and `TOKEN` is the authentication token.

##### Creating the GitHub repository
Create the repository on GitHub that will store this project.

##### Creating package.json
Create a new directory for your project, and navigate into it. Make sure you have `npm` installed. Run `npm init` to generate a `package.json` configuration file for your NPM module.
```shell script
$ mkdir npm-hello-world
$ cd npm-hello-world
$ npm init
```
and fill out the specified fields. The `name` field should be in the format `@OWNER/PACKAGENAME`, where `OWNER` is the GitHub user or organization that the repo will fall under, and `PACKAGENAME` is the name of the NPM package. Open the newly-generated `package.json` file and add the `publishConfig` to the top-level object:
```json
"publishConfig": {
  "registry": "https://npm.pkg.github.com/"
}
```
The `package.json`, for this project (at version 0.1.0), for example, includes the following relevant fields:
```json
{
  "name": "@jlam55555-playground/npm-hello-world",
  "description": "A Hello, world! NPM module",
  "version": "0.1.0",
  "publishConfig": {
    "registry": "https://npm.pkg.github.com/"
  },
  "repository": {
    "type": "git",
    "url": "https://www.github.com/jlam55555-playground/npm-hello-world"
  }
}
```
Then, to publish to GitHub's NPM package registry:
```shell script
$ npm publish
```
Make sure to save your code to source control (to Git) as well.

### Updating the package
Check in and commit the code for the new release. NPM has utilities to automatically tag NPM releases and create the corresponding tags for Git (choose
`major`, `minor`, or `patch` depending on the release).
```shell script
$ npm version major   # auto-updates version from 0.1.0 -> 1.1.0; OR
$ npm version minor   # auto-updates version from 0.1.0 -> 0.2.0; OR
$ npm version patch   # auto-updates version from 0.1.0 -> 0.1.1
$ npm publish         # publish changes to NPM registry
$ git push            # push new changes
$ git push --tags     # push new tags
```

[1]: https://help.github.com/en/packages/using-github-packages-with-your-projects-ecosystem/configuring-npm-for-use-with-github-packages
[2]: https://www.github.com/jlam55555-playground/npm-hello-world-consumer
