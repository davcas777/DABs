# GitHub DABs - Databricks Asset Bundle with CI/CD

A clean, production-ready Databricks Asset Bundle (DAB) project with GitHub Actions CI/CD pipeline for automated deployment.

## 🚀 Features

- **Environment Separation**: Development and Production environments
- **CI/CD Pipeline**: Automated deployment with GitHub Actions
- **PR-based Production**: Safe production deployments via Pull Requests
- **Clean Structure**: Minimal, focused project structure

## 📁 Project Structure

```
github_dabs/
├── .github/workflows/          # GitHub Actions CI/CD
│   ├── dev-deploy.yml         # Development deployment
│   └── prod-deploy.yml        # Production deployment
├── resources/                  # Databricks bundle resources
│   └── github_dabs.job.yml    # Job definition
├── src/                       # Source code
│   └── hello_world.ipynb      # Main notebook
├── databricks.yml             # Bundle configuration
├── requirements.txt           # Python dependencies
├── README.md                  # This file
└── ENVIRONMENT_SETUP.md       # Environment setup guide
```

## 🔄 Workflow

### **Development:**
1. **Work on `develop` branch**: Make your changes
2. **Push to develop**: `git push origin develop`
3. **Automatic deployment**: GitHub Actions deploys to dev environment
4. **Test**: Check results in Databricks workspace

### **Production:**
1. **Create Pull Request**: From `develop` → `main`
2. **Review & Approve**: Team reviews the changes
3. **Merge to main**: Merge PR to main branch
4. **Automatic deployment**: GitHub Actions deploys to production

## 🛠️ Local Development

1. **Install Databricks CLI**: https://docs.databricks.com/dev-tools/cli/databricks-cli.html
2. **Authenticate**: `databricks configure`
3. **Deploy locally**: `databricks bundle deploy --target dev`
4. **Run job**: `databricks bundle run github_dabs_job --target dev`

## 📚 Documentation

- **Environment Setup**: See `ENVIRONMENT_SETUP.md` for detailed environment configuration
- **Databricks Bundles**: https://docs.databricks.com/dev-tools/bundles/index.html
- **GitHub Actions**: https://docs.github.com/en/actions
