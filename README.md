## Browser Development

### Compiling

Make sure you have both git and [yarn](https://yarnpkg.com/en/docs/install) installed.

You need to use node.js version `8.x` to build the browser currently.

- `git clone https://github.com/EONetwork/safe_browser.git`
- `cd safe_browser`
- `NODE_ENV=dev yarn` (`NODE_ENV` is needed to install mock libs and to run `yarn mock-dev`).
- `yarn rebuild`

And to run dev mode:
- `yarn mock-dev`

Want to run 'production' variables, but with hot reloading?
- `yarn put-live-net-files-for-<windows|osx|linux>`
- `yarn prod-dev`

Note, you'll need a crust.config set for the application. [Helper commands for osx/linux/windows](https://github.com/maidsafe/safe_browser/blob/master/package.json#L55-L58)

And to package:
- `yarn package`

The resulting packages are contained within the `releases` folder.

A packaged application, built in a `NODE_ENV=dev`, can access either `prod` or `dev` networks. `prod` is the default, or alternatively you can open the application and pass a `--mock` flag to open and use a mock network.

#### Build commands

There are a few build commands for various situations:

- `yarn mock-dev` will run a developer version of the application using `MockVault`
- `yarn prod-dev` will run a developer version of the application using the live network.
- `yarn build` compiles all code, but you shouldn't need to use this
- `yarn build-preload` will need to be run whenever you change the `preload.js` file for changes to show up in the browser.

### Release

`yarn bump` is available for automatically updating versions and generating a changelog update based upon conventional-commits.


### Redux

The core is built around redux for simple state management allowing for easy
extensibility.

### React

The interface is built in react for simple data flow and clear componentisation.


### Webpack

`webpack.config.base` contains loaders and alias' used across all webpack configs.

There is a prod, config. Alongside renderer configs.

When developing against hot reloading, the `vendor` setup is used to speed up build times etc.

There are 'dev' mode configs for running against the NODE_ENV=develeopment setup.
There are 'live-dev' configs for running against NODE_ENV=production but without needing to package.

### Testing

- `yarn test` runs jest (you have the optional `yarn test-watch`, too).
- `yarn test-e2e` runs spectron integration tests (not yet stable).
- `yarn lint` ...lints...

### Logging

Via electron-log: `import logger from 'logger'`, and you can `logger.info('things')`.

Logs are printed to both render console and stdout. Logs are also written to a log file per system.

`yarn log-osx` will tail the file. Similar commands (as yet untested) exist for linux/windows.


## SAFE Network

The `safe` code is contained within the `app/extensions` folder. This includes
a simple http server with is used to provide the http like functionalities of the safe network.

Currently you need to authenticate against the SAFE Browser to get network access.

### Authenticator

Currently, we're using a `temp_dist` version of the authenticator webapp, prebuilt from the 'beaker-plugin-safe-authenticator'.

- APIs are located in `app/extensions/safe/api`;
- APIs are located in `app/extensions/safe/auth-api`;

## Further Help

You can discuss development-related questions on the [SAFE Dev Forum](https://forum.safedev.org/).
If you are just starting to develop an application for the SAFE Network, it's very advisable to visit the [SAFE Network Dev Hub](https://hub.safedev.org) where you will find a lot of relevant information, including tutorials.

## License

SAFE Browser is a lightly modified fork of the [Peruse Browser](https://github.com/joshuef/peruse).

This SAFE Network application is dual-licensed under the Modified BSD ([LICENSE-BSD](LICENSE-BSD) https://opensource.org/licenses/BSD-3-Clause) or the MIT license ([LICENSE-MIT](LICENSE-MIT) https://opensource.org/licenses/MIT) at your option.
