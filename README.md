## Why it's a patch

ESLint's long awaited module resolver overhaul still has not materialized as of ESLint 7.  As a stopgap,
we created a small **.eslintrc.js** patch that solves the problem adequately for most real world scenarios.
This patch was proposed as an ESLint feature with [PR 12460](https://github.com/eslint/eslint/pull/12460), however
the maintainers were not able to accept it unless it is reworked into a fully correct design.  Such a requirement
would impose the same hurdles as the original GitHub issue; thus, it seems best to stay with the patch approach.

Since the patch is now in wide use, we've converted it into a proper NPM package to simplify maintenance.


## How to use it

Add a `require()` call to the to top of the **.eslintrc.js** file for each project that depends on your shared
ESLint config, for example:

**.eslintrc.js**
```ts
// This is a workaround for https://github.com/eslint/eslint/issues/3458
require('@rushstack/eslint-config/patch/modern-module-resolution');
// Add your "extends" boilerplate here, for example:
module.exports = {
  extends: ['@callback-cats/eslint-config'],
  parserOptions: { tsconfigRootDir: __dirname }
};