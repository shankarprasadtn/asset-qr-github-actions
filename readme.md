# GitHub Actions CI/CD Pipeline for Flask Application

## Objective
Implement a CI/CD workflow using GitHub Actions for a Python Flask application.

## Repository
Project Repository:
https://github.com/shankarprasadtn/asset-qr-github-actions

## Application Overview
This project is a Flask-based Asset QR Management Application used to generate and manage QR-based asset records.

---

# Branches Used

- main
- staging

---

# Workflow Location

.github/workflows/ci-cd.yml

---

# GitHub Actions Pipeline Stages

## 1. Build
Installs required dependencies from requirements.txt using pip.

## 2. Test
Validates the Flask application using Python compile check.

## 3. Deploy to Staging
Runs automatically when code is pushed to the staging branch.

## 4. Deploy to Production
Runs automatically when a release tag is created.

---

# Workflow File Used

```yaml
name: Asset QR CI/CD

on:
  push:
    branches: [main, staging]
  release:
    types: [created]

jobs:
  build-test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
      - run: pip install -r requirements.txt
      - run: python -m py_compile app.py

  deploy-staging:
    if: github.ref == 'refs/heads/staging'

  deploy-production:
    if: startsWith(github.ref, 'refs/tags/')


## Secrets Configuration

GitHub Secrets can be added in:

Settings → Secrets and variables → Actions

Examples:

DEPLOY_KEY
API_TOKEN
How It Works
Push to main branch → Build + Test
Push to staging branch → Build + Test + Deploy to Staging
Create release tag → Build + Deploy to Production
How to Run Application Manually
pip install -r requirements.txt
python app.py

Open in browser:

http://localhost:5000
