# Set up Playwright

## Steps

1. **Checks Playwright version and OS**
2. **Installs dependencies** - installs Playwright's dependencies
3. **Caches dependencies** - uses `actions/cache` to cache the appropriate directory

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
