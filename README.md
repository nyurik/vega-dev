# vega-dev

This repository gathers all Vega modules together to facilitate development. Rather than provide a true monorepo, each Vega module is installed under the `packages/` directory using a standard `git clone` (no submodules or subtrees required!). [Lerna](https://github.com/lerna/lerna) is then used to aid cross-module linking and testing.

The Vega modules included in this development shell are listed under the `vegaModules` property in `package.json`.

# Setup

1. [Install yarn](https://yarnpkg.com/en/docs/install), if you haven't already.
2. Run `git clone git@github.com:vega/vega-dev.git` to clone this repository.
3. Run `yarn` in the top-level folder to install all Vega modules and their dependencies. Each module will be cloned from its GitHub repo, and all dependencies installed. Vega module dependencies will then be symlinked (via `lerna bootstrap`) to resolve to local copies.
4. Perform development as usual! Each module in `packages/` corresponds to a separate independently-versioned package with its own git repository. It is up to you manage commits and branches like any other individual repository.

# Cross-Module Testing

Run `yarn test` in the top-level directory to run test suites for all Vega modules.

Run `yarn serve` in the top-level directory to launch a web server for interactive web-based tests located in `packages/vega-lib/test`. This command will also open a browser window, click the `test` directory link to go to the test specification viewer.
