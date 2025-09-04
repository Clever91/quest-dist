# Automatic Deployment Guide

This project is configured with GitHub Actions to automatically deploy to production when code is pushed to the main branch.

## 🚀 Quick Start

The deployment workflow is already configured in `.github/workflows/deploy.yml`. By default, it will deploy to **GitHub Pages** which requires no additional setup.

## 📋 Deployment Options

### Option 1: GitHub Pages (Recommended for beginners)

**Pros:** Free, easy setup, integrated with GitHub
**Cons:** Limited customization, slower builds

**Setup:**
1. Go to your repository Settings → Pages
2. Set Source to "Deploy from a branch"
3. Select "gh-pages" branch
4. Save

The workflow will automatically create the `gh-pages` branch and deploy your site to:
`https://yourusername.github.io/your-repo-name`

### Option 2: Vercel (Recommended for production)

**Pros:** Fast, reliable, great for static sites, custom domains
**Cons:** Requires account setup

**Setup:**
1. Go to [vercel.com](https://vercel.com) and sign up
2. Import your GitHub repository
3. Get your deployment tokens from Vercel dashboard
4. Add these secrets to your GitHub repository:
   - `VERCEL_TOKEN`
   - `ORG_ID`
   - `PROJECT_ID`
5. Uncomment the Vercel deployment step in the workflow file

### Option 3: Netlify

**Pros:** Free tier, good performance, form handling
**Cons:** Requires account setup

**Setup:**
1. Go to [netlify.com](https://netlify.com) and sign up
2. Import your GitHub repository
3. Get your access token from Netlify dashboard
4. Add `NETLIFY_AUTH_TOKEN` to your GitHub secrets
5. Uncomment the Netlify deployment step in the workflow file

### Option 4: Custom Server (Advanced)

**Pros:** Full control, custom infrastructure
**Cons:** Requires server management, more complex setup

**Setup:**
1. Ensure your server has SSH access
2. Add these secrets to your GitHub repository:
   - `HOST` - Your server IP/domain
   - `USERNAME` - SSH username
   - `SSH_KEY` - Private SSH key
   - `PORT` - SSH port (usually 22)
3. Uncomment the custom server deployment step in the workflow file
4. Update the deployment path in the script

## 🔧 Configuration

### GitHub Secrets

To add secrets to your repository:
1. Go to your repository Settings → Secrets and variables → Actions
2. Click "New repository secret"
3. Add the required secrets for your chosen deployment method

### Customizing the Workflow

Edit `.github/workflows/deploy.yml` to:
- Change the trigger branches
- Add build steps if needed
- Modify deployment settings
- Add notifications (Slack, Discord, etc.)

## 📁 File Structure

Your project structure should look like this:
```
quest-dist/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── assets/
├── static/
├── index.html
└── DEPLOYMENT.md
```

## 🚨 Troubleshooting

### Common Issues:

1. **Workflow not running:**
   - Check if you're pushing to the main/master branch
   - Verify the workflow file is in `.github/workflows/`

2. **Deployment fails:**
   - Check the Actions tab for error logs
   - Verify all required secrets are set
   - Ensure your hosting platform is properly configured

3. **Site not updating:**
   - Check if the deployment completed successfully
   - Clear browser cache
   - Verify the correct branch is being deployed

### Getting Help:

- Check the GitHub Actions logs in the Actions tab
- Review the hosting platform's documentation
- Ensure all secrets and configuration are correct

## 🔄 Manual Deployment

You can also trigger deployment manually:
1. Go to Actions tab in your repository
2. Select "Deploy to Production" workflow
3. Click "Run workflow"
4. Select the branch and click "Run workflow"

## 📝 Notes

- The workflow runs on Ubuntu latest
- Node.js 18 is available for any build steps
- All deployment methods are commented out except GitHub Pages
- Uncomment and configure the method you want to use
- Remove or comment out unused deployment methods to avoid conflicts 