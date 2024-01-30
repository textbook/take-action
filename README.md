# Set up Playwright

## Steps

1. **Checks out the repository** _(optional)_
2. **Validates working directory** - ensures `package.json` is present and determines an appropriate [package manager](#package-managers) from the lockfile
3. **Installs pnpm standalone** _(if needed)_ - version can be explicitly specified as `pnpm-version` or taken from the `packageManager` field in `package.json`
4. **Installs Node.js** - version can be:
   - explicitly specified as `node-version`;
   - taken from the `.engines.node` field in `package.json` (if valid for both [npm](https://docs.npmjs.com/cli/v9/configuring-npm/package-json#engines) and [nvm](https://github.com/actions/setup-node#supported-version-syntax)\*); or
   - looked up from an e.g. `.nvmrc` file specified as `node-version-file`.
5. **Installs dependencies** _(optional)_ - ensures relevant lockfile is unchanged and bails if it's inconsistent
6. **Caches dependencies** - uses `actions/setup-node`'s default caching for the appropriate package manager

## Usage

```yaml
    steps:
      - uses: textbook/take-action@playwright
```

### Inputs

- `working-directory`: Working directory to use for commands (**default**: `'.'`, the root of the repo)

### Outputs

- `cache-hit`: Whether the cache was hit by `actions/cache`
- `playwright-version`: The version of Playwright detected and used
