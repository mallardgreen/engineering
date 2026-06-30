# Private Packages

To consume `@mallardgreen` private packages follow these steps:

On a new machine, authenticate GitHub CLI:

```sh
gh auth login
gh auth refresh -h github.com -s read:packages
```

Store the GitHub Packages token globally for (p)npm:

```sh
npm config set //npm.pkg.github.com/:_authToken "$(gh auth token)"
```

In any project that consumes `@mallardgreen/*` packages, commit this `.npmrc`:

```ini
@mallardgreen:registry=https://npm.pkg.github.com
```

Then install with pnpm:

```sh
pnpm add @mallardgreen/relic
```
