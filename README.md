## Piral with Monorepo Bug

This minimal working example project can be used to recreate the build error bug which occurs on a fresh clone when using Piral with a monorepo.

## Project Setup

- Simple monorepo with 2 workspaces inside the `packages` folder
  - `app-shell` - Piral Application Shell
    - created using `piral new --target app-shell`
  - `react-app-01` - React Application
    - created using `yarn create react-app react-app-01 --template typescript`

## Steps to recreate

make sure `yarn` is installed globally on the host

1. run `yarn` on the root
2. run `yarn build` on the root

To repeat, run `yarn clean` (which will delete the root `node_modules` folder), then run step 1 & 2 above.

## Notes

- When the build error occurs, some zombie node processes still running in the wild for some time (assume the parcel-bundler still runs in parallel)
- Therefore rerunning `yarn build` after the 1st failure without deleting the root `node_modules` will make the build succeed.

## Screenshot of Error

NOTE: Each time the error occurs `'Cannot find module %'` _may_ have different module names.

![Image](https://i.imgur.com/vDyLZrc.png)
