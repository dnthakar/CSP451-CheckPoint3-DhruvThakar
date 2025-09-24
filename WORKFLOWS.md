# Workflow Documentation

## CI Pipeline
**Purpose:** Lint, test (with coverage), build  
**Trigger:** push to `main` or `develop`, PR to `main`  
**Jobs:** lint → test → build  
**Secrets:** None required for basic CI  
**Notes:** Uses composite action for Node setup + npm install

## Dependency Audit
**Purpose:** Daily `npm audit` and create GitHub issue if vulnerabilities found  
**Trigger:** scheduled daily + manual workflow_dispatch  
**Jobs:** audit  
**Secrets:** None (uses GITHUB_TOKEN)  
**Notes:** Adds issue only if vulnerabilities exist

## Deploy to GitHub Pages
**Purpose:** Build project and deploy to gh-pages branch  
**Trigger:** push to `main`  
**Jobs:** build-and-deploy  
**Secrets:** GITHUB_TOKEN (automatic)  
**Notes:** Output goes to ./dist folder

## Composite Action
**Purpose:** Reusable Node.js setup + install  
**Location:** `.github/actions/setup-node-env`  
**Usage:** `- uses: ./.github/actions/setup-node-env`
