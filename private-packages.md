# Private Packages

Projects can consume private `@mallardgreen/*` packages from GitHub Packages.

## One-time setup

Authenticate GitHub CLI and grant package read access:

```sh
gh auth login
gh auth refresh -h github.com -s read:packages
```

Store that token in your global npm config:

```sh
npm config set //npm.pkg.github.com/:_authToken "$(gh auth token)"
```

## Project setup

Commit this `.npmrc` in any project that installs `@mallardgreen/*` packages:

```ini
@mallardgreen:registry=https://npm.pkg.github.com
```

Then install normally:

```sh
pnpm add @mallardgreen/relic
```

Do not commit auth tokens. The committed `.npmrc` should only contain the scoped registry line above.
