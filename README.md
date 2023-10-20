# Set up Node.js

## Usage

```yaml
    steps:
      - uses: textbook/take-action@nodejs
        with:
          node-version: lts/hydrogen
```

### Inputs

- `checkout`: Whether to run `actions/checkout` (**default**: `'true'`)
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
