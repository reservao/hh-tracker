# Project Rules for HH-Tracker

## Automatic Deployment Workflow
- Whenever changes or additions are made to files in this repository, automatically stage, commit, and push the changes to GitHub (`git push origin main`).
- This will automatically trigger the GitHub Actions workflow (`.github/workflows/deploy.yml`) to deploy the updated version to Firebase Hosting without requiring manual user intervention.
