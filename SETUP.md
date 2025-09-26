# Databricks CI/CD Setup Guide

This repository contains a Databricks project with GitHub Actions CI/CD pipeline for automated deployment.

## Prerequisites

1. **Databricks Workspace**: You need access to a Databricks workspace
2. **Personal Access Token**: Generate a Databricks personal access token
3. **GitHub Repository**: This repository should be set up with the required secrets

## GitHub Secrets Setup

To enable the CI/CD pipeline, you need to configure the following secrets in your GitHub repository:

### Required Secrets

1. **DATABRICKS_HOST**: Your Databricks workspace URL
   - Example: `https://adb-520209755093735.15.azuredatabricks.net`

2. **DATABRICKS_TOKEN**: Your Databricks personal access token
   - Generate this from: User Settings → Developer → Access tokens

### How to Set Up Secrets

1. Go to your GitHub repository
2. Click on **Settings** tab
3. In the left sidebar, click **Secrets and variables** → **Actions**
4. Click **New repository secret**
5. Add each secret with the exact names above

## Project Structure

```
├── .github/workflows/          # GitHub Actions workflows
│   ├── deploy.yml             # Simple deployment workflow
│   └── ci-cd.yml              # Comprehensive CI/CD pipeline
├── resources/                  # Databricks bundle resources
│   ├── github_dabs.job.yml    # Job definition
│   └── github_dabs.pipeline.yml # Pipeline definition
├── src/                       # Source code
│   ├── hello_world.ipynb      # Hello World notebook
│   └── github_dabs/           # Python package
├── databricks.yml             # Bundle configuration
└── pyproject.toml             # Python project configuration
```

## Workflow Triggers

### Simple Deployment (`deploy.yml`)
- Triggers on push to `main` branch
- Triggers on pull requests to `main`
- Manual trigger via workflow_dispatch

### Comprehensive CI/CD (`ci-cd.yml`)
- **Pull Requests**: Runs tests and validation
- **Develop Branch**: Deploys to development environment
- **Main Branch**: Deploys to production environment
- **Manual**: Can be triggered manually

## Local Development

1. **Install Databricks CLI**:
   ```bash
   pip install databricks-cli
   ```

2. **Configure Databricks CLI**:
   ```bash
   databricks configure --token
   ```

3. **Deploy locally**:
   ```bash
   databricks bundle deploy --target dev
   ```

4. **Run job locally**:
   ```bash
   databricks bundle run --target dev
   ```

## Testing the Pipeline

1. **Make a change** to any file (e.g., update the hello world message)
2. **Commit and push** to the `main` branch
3. **Check GitHub Actions** tab to see the workflow running
4. **Verify deployment** in your Databricks workspace

## Job Configuration

The job is configured in `resources/github_dabs.job.yml` and runs:
- A simple "Hello World" notebook
- Scheduled to run daily (can be modified)
- Uses development mode by default

## Troubleshooting

### Common Issues

1. **Authentication Errors**: Verify your DATABRICKS_TOKEN is valid
2. **Host Errors**: Ensure DATABRICKS_HOST is correct
3. **Permission Errors**: Check your token has necessary permissions

### Debug Steps

1. Check GitHub Actions logs for detailed error messages
2. Verify secrets are set correctly in repository settings
3. Test local deployment first: `databricks bundle deploy --target dev`

## Next Steps

1. Set up the required GitHub secrets
2. Push changes to trigger the pipeline
3. Monitor the deployment in Databricks workspace
4. Customize the job configuration as needed
