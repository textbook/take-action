# Set up Node.js



## Steps

1. **Checks out the repository** _(optional)_
2. **Validates working directory** - ensures `package.json` is present and determines an appropriate [package manager](#package-managers) from the lockfile
3. **Installs pnpm standalone** _(if needed)_ - version can be explicitly specified as `pnpm-version` or taken from the `packageManager` field in `package.json`
4. **Installs Node.js** - version can be:
   - explicitly specified as `node-version`;
   - taken from the `.engines.node` field in `package.json` (if valid for both [npm](https://docs.npmjs.com/cli/v9/configuring-npm/package-json#engines) and [nvm](https://github.com/actions/setup-node#supported-version-syntax)\*); or
   - looked up from an e.g. `.nvmrc` file specified as `node-version-file`.
5. **Installs dependencies** - ensures relevant lockfile is unchanged and bails if it's inconsistent
6. **Caches dependencies** - uses `actions/setup-node`'s default caching for the appropriate package manager

## Usage

```yaml
    steps:
      - uses: textbook/take-action@nodejs
        with:
          node-version: lts/hydrogen
```

### Inputs

- `checkout`: Whether to run `actions/checkout` (**default**: `'true'`)
- `install`: Whether to run the install step (**default**: `'true'`)
- `node-version`: Version to pass to [`actions/setup-node`](https://github.com/actions/setup-node#supported-version-syntax) (**default**: `''`)
- `node-version-file`: Version file to pass to `actions/setup-node` (**default**: `''`)
- `pnpm-version`: Version to pass to [`pnpm/action-setup`](https://github.com/pnpm/action-setup#version) (**default**: `''`)
- `working-directory`: Working directory to use for commands (**default**: `'.'`, the root of the repo)

### Package managers

Your repo must have a `package.json` in the working directory. This action supports the following package managers:

- npm (if `package-lock.json` is in the working directory)
- pnpm (if `pnpm-lock.yaml` is in the working directory)
- Yarn (if `yarn.lock` is in the working directory)

### Outputs

- `cache-hit`: Whether the cache was hit by `actions/setup-node`
- `node-version`: The version of Node.js installed by `actions/setup-node`
- `package-manager`: The package manager detected and used (one of `'npm'`, `'pnpm'`, `'yarn'`)

\* _Basically you're limited to either a version number (i.e. `x`, `x.y` or `x.y.z`), optionally prefixed with `v`, or a wildcard `*`. nvm doesn't accept most of npm's semver-ish options, like `^20` or `18.x` (although both agree that `21.*` would be fine), and npm doesn't accept nvm's aliases, like `lts`._
