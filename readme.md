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

`````
**## Secrets Configuration ##**

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

**Below with the Repo details**
* GitHub Actions workflow
* README
* Screenshots
* <img width="1919" height="1199" alt="Screenshot 2026-04-14 184701" src="https://github.com/user-attachments/assets/06fa23c4-c64d-4d70-ad0f-7f1c01b544e9" />
* <img width="951" height="1079" alt="Screenshot 2026-04-14 190226" src="https://github.com/user-attachments/assets/b12c2e93-c3eb-46ac-b69c-7ff6e368ff87" />
* <img width="950" height="1070" alt="Screenshot 2026-04-14 190311" src="https://github.com/user-attachments/assets/65fc33e3-348b-4019-b964-464d0166e5e2" />


