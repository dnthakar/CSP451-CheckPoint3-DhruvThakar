# Workflows

## CI Pipeline
Purpose: Lint, test (coverage), build and upload artifacts.
Triggers: push to `main` or `develop`, PR to `main`.
Jobs: lint -> test -> build.
Secrets: `CODECOV_TOKEN` (optional), `GITHUB_TOKEN` (automatic).
Troubleshooting: check Actions logs; ensure `npm test` generates `coverage/coverage-summary.json`.

## Dependency Audit
Purpose: Daily `npm audit`. Create Issue if vulnerabilities found.
Triggers: daily schedule (02:00 UTC) and manual.
Secrets: `GITHUB_TOKEN` (automatic).
Troubleshooting: open `audit.json` in run logs.

## Deploy to GitHub Pages
Purpose: Build and publish `./dist` to `gh-pages`.
Triggers: push to `main`.
Secrets: `GITHUB_TOKEN` (automatic).
Troubleshooting: ensure `npm run build` outputs `./dist`. Check Pages settings and action logs.

## Composite Action
Purpose: Reuse Node setup and install steps.
Location: `.github/actions/setup-node-env`
Usage: `- uses: ./.github/actions/setup-node-env`

## Notes
- Enforce coverage: CI fails if `lines.pct` < 80 from `coverage/coverage-summary.json`.
- Add `CODECOV_TOKEN` in repo Settings → Secrets if your repo is private and you use Codecov.
