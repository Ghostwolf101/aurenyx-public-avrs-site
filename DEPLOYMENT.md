# Deployment Guide

This repository uses GitHub Pages to deploy the AVRS site to `avrs.auernyx.com`.

## One-Time Setup Required

Before the automated workflow can deploy, GitHub Pages must be manually enabled in the repository settings:

1. Go to repository **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**
3. Save the changes

## Automated Deployment

Once GitHub Pages is enabled, the workflow (`.github/workflows/pages.yml`) will automatically:

1. Build the site on every push to `main`
2. Package `index.html`, `assets/`, and `CNAME` into a deployment artifact
3. Deploy to GitHub Pages
4. Make the site available at `avrs.auernyx.com`

## Custom Domain

The `CNAME` file configures the custom domain: `avrs.auernyx.com`

Ensure DNS is properly configured to point to GitHub Pages:
- Add a CNAME record for `avrs` pointing to `<username>.github.io`
- Or configure DNS as per GitHub Pages documentation

## Troubleshooting

If deployment fails:
- Verify GitHub Pages is enabled in repository settings
- Check that the workflow has the correct permissions (defined in `pages.yml`)
- Review workflow run logs in the Actions tab
