# CloudB Documentation Repository

This repository contains the documentation for CloudB, a comprehensive platform for Delhom engineers to manage acoustic tools, analyze data, and much more.

## About CloudB

CloudB is an all-in-one solution that streamlines various tasks related to acoustic project management and data analysis. This platform features a variety of workspaces and applications, including Eolyse for wind farm analysis and Acmonitor Connect for acoustic measurements.

For more detailed information about CloudB's features, please consult the documentation available in this repository.

---

# MkDocs Deployment Guide

This guide outlines the steps to deploy updates to MkDocs documentation. 

## Steps to Deploy

### 1. Navigate to Project Directory

Open the terminal and navigate to your MkDocs project directory.

```bash
cd path/to/your/mkdocs/project
```

### 2. Pull Latest Changes (Optional)
```bash
git pull origin main
```

### 3. Make your changes
Update the Markdown files and other assets in your MkDocs project. Don't forget to update the index pages.

### 4. Preview Changes Locally (Optional)
Before pushing, preview the documentation to ensure it appears as expected.
```bash
mkdocs serve
```

### 6. Add and Commit Changes
Stage and commit your changes to the git repository.
```bash
git add .
git commit -m "Updated documentation"
```

### 7. Push to GitHub
```bash
git push origin main
```

### 8. Deploy to GitHub Pages
Deploy your updated documentation to GitHub Pages.
```bash
mkdocs gh-deploy
```

### 9. Verify Deployment
After deployment is complete, check your live documentation to ensure the changes are reflected.