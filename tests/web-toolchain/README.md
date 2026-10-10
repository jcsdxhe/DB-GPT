# Frontend toolchain browser regression

This suite checks the existing DB-GPT frontend with deterministic API fixtures.
It covers page entry, navigation, forms, charts, SQL editing and downloads.
The application runs from `web/`; this separate package does not change its
dependency installation.

## Run

Use Node >=20.19 and npm 10.8.2.

1. In `web/`, install with `npm ci`. Start `npm run dev`, or run
   `npm run build` followed by `npm start` for production verification.
2. Wait for Next to report that the server is ready.
3. In this directory:

   ```sh
   npm ci
   npx playwright install chromium
   npm test
   ```

`REGRESSION_URL` overrides `http://127.0.0.1:3000`; `REGRESSION_MODE` names the
result folder, and `REGRESSION_OUTPUT` changes its root directory.

`REGRESSION_BROWSER` selects `chromium` (default), `firefox` or `webkit` after
installing that Playwright browser. Use `npm test -- --grep 'route:'` for page
entry checks. The compound `markdown-chart-sql-data-and-download` case requires
Chromium clipboard permissions; exclude it when running Firefox or WebKit.

## Results and limits

Each case records requests, browser diagnostics, a page snapshot and screenshot.
Failed cases also save traces. Assertions reject unexpected API calls, HTTP
failures, uncaught exceptions and console warnings/errors. Navigation-cancelled
`ERR_ABORTED` requests are excluded from network failures.

These are browser tests with API fixtures. They do not verify backend
persistence, model inference, authorization, live connectors or scheduled jobs.
Existing application failures can be exposed by the suite; they should be
reported separately from toolchain regressions, without expanding the upgrade
into unrelated business changes. Store validation evidence outside the source
tree and summarize the tested revision and limits in the PR description.
