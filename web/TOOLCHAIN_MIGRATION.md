# Frontend tooling

The web application uses Next.js 16.3.8, React 18.3.1, TypeScript 5.9.3,
ESLint 9 and npm 10. Use Node >=20.19 and npm 10.8.2 with the committed
`package-lock.json`.

## Compatibility

- Pages Router and the existing backend API remain in use.
- Native `transpilePackages` replaces `next-transpile-modules`. Webpack remains
  explicit in development and production for Monaco workers and existing plugins.
- The OB editor uses the installed `sql-formatter` instead of bundling its large
  generated formatter parser. Completion continues to use OB SQL workers.
- Pages Router session wrappers attach an iron-session 8 session before calling
  handlers, preserving the previous wrapper contract.
- `npm run compile` uses `output: 'export'` instead of the removed `next export`.
  Server builds retain the API rewrite; static exports are served by Python.
- Type checking includes application sources. Each build uses an isolated
  temporary TypeScript config so declarations from other output directories do
  not interfere. Type errors remain fatal.
- ESLint uses flat config and retains Rules of Hooks and exhaustive-deps checks.
  React Compiler is not enabled. Prettier remains a separate formatting command.

## Checks

```sh
npm ci
npm run typecheck
npm run lint
npm run test:build
npm test
npm run build
npm run compile
```

The existing web workflow keeps its Ubuntu/macOS matrix and web-only automatic
triggers. It installs the pinned npm version, checks types, lint and frontend
tests, then builds. Manual dispatch supports verification of a selected branch.
It does not run backend, connector or live-service tests.

For browser checks, see [the test runner](../tests/web-toolchain/README.md).
For Python-served packaging, follow [the web README](README.md).
Results and known limitations belong in the PR description or CI artifacts,
rather than dated acceptance reports in the source tree.
