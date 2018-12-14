## Browser Development

### Compiling

Make sure you have both git and [yarn](https://yarnpkg.com/en/docs/install) installed.

You need to use node.js version `8.x` to build the browser currently. (`nvm install 8.0`)

- `git clone https://github.com/EONetwork/safe_browser.git`
- `cd safe_browser`
- `NODE_ENV=dev yarn` (sometimes this fails, re-running it should resolve it)
- `yarn rebuild`

Want to run 'production' variables, but with hot reloading?
- `yarn put-live-net-files-for-<windows|osx|linux>`

Note, you'll need a crust.config set for the application. 

And to package:
- `yarn package`

The resulting packages are contained within the `releases` folder.

A packaged application, built in a `NODE_ENV=dev`, can access either `prod` or `dev` networks. `prod` is the default, or alternatively you can open the application and pass a `--mock` flag to open and use a mock network.

