# vega-dev

This repository gathers all Vega modules together to facilitate development. Rather than provide a true monorepo, each Vega module is a submodule in the `packages/` directory.

 Use `git clone --recurse-submodules -j8 https://github.com/vega/vega-dev.git` to get everything efficiently in parallel. [Lerna](https://github.com/lerna/lerna) is then used to aid cross-module linking and testing.

# Setup

1. [Install yarn](https://yarnpkg.com/en/docs/install), if you haven't already.
2. Run `git clone --recurse-submodules -j8 https://github.com/vega/vega-dev.git` to clone this repository and its submodules.
3. Run `yarn` in the top-level folder to install all Vega module dependencies. Vega module dependencies will then be symlinked (via `lerna bootstrap`) to resolve to local copies.
4. For development, you may want to use `SSH` instead of `HTTPS` protocol by running these two commands:
```
git config url."ssh://git@".insteadOf https://
git submodule foreach git config url."ssh://git@".insteadOf https://
```
Each module in `packages/` corresponds to a separate independently-versioned package with its own git repository.

# Cross-Module Testing

Run `yarn test` in the top-level directory to run test suites for all Vega modules.

Run `yarn serve` in the top-level directory to launch a web server for interactive web-based tests located in `packages/vega-lib/test`. This command will also open a browser window, click the `test` directory link to go to the test specification viewer.

# Useful Tricks
A few useful commands when working with submodules:
* `git submodule foreach <command>` -- run a command inside each submodule, e.g. `git pull` or `git status`.
  * To ignore errors, you could use `git submodule foreach '<command> || :'`
  * To open a browser tab for each github repo, use `git submodule foreach 'xdg-open https://github.com/vega/$path'` (Linux). For MacOS you may need to use `open` instead of `xdg-open`.
* You may find [Git submodule helper tools](https://github.com/kollerma/git-submodule-tools#git-submodule-helper-scripts--gui) useful in your work.
