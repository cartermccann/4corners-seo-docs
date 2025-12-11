# Deployment Guide - Vercel

This guide will walk you through deploying your Comcreate SEO report to Vercel.

## Prerequisites

- GitHub account
- Vercel account (free tier works great)
- Your SEO report markdown files added to `src/content/docs/`

## Step 1: Test Your Build Locally

Before deploying, always test that your site builds successfully:

```bash
npm run build
```

If successful, you'll see output like:
```
✓ Completed in 2.5s
```

Preview the built site:
```bash
npm run preview
```

Visit `http://localhost:4321` to verify everything looks correct.

## Step 2: Push to GitHub

If you haven't already, initialize a Git repository and push to GitHub:

```bash
# Initialize git (if not already done)
git init

# Add all files
git add .

# Create your first commit
git commit -m "Initial SEO report for [Client Name]"

# Create a new repository on GitHub, then:
git remote add origin https://github.com/your-username/client-name-seo-report.git
git branch -M main
git push -u origin main
```

## Step 3: Connect to Vercel

### Option A: Deploy via Vercel Dashboard (Recommended)

1. Go to [vercel.com](https://vercel.com) and log in
2. Click "Add New..." → "Project"
3. Import your GitHub repository
4. Vercel will automatically detect Astro
5. **No configuration needed!** Vercel uses these defaults:
   - **Framework Preset**: Astro
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`
   - **Install Command**: `npm install`
6. Click "Deploy"

Your site will be live in ~1-2 minutes!

### Option B: Deploy via Vercel CLI

```bash
# Install Vercel CLI globally
npm i -g vercel

# Deploy
vercel

# For production deployment
vercel --prod
```

## Step 4: Configure Your Deployment (Optional)

### Custom Domain

1. In your Vercel project dashboard, go to "Settings" → "Domains"
2. Add your custom domain (e.g., `client-name-seo-report.comcreate.org`)
3. Update your DNS records as instructed by Vercel
4. Vercel automatically provisions SSL certificate

### Environment Variables (if needed)

If you add any environment variables in the future:

1. Go to "Settings" → "Environment Variables"
2. Add your variables for Production, Preview, and Development
3. Redeploy for changes to take effect

## Step 5: Share with Client

After deployment, you'll get a URL like:
- `https://your-project-name.vercel.app`
- Or your custom domain: `https://client-name-seo-report.comcreate.org`

Share this URL with your client. The site is:
- **Fast**: Static files served via global CDN
- **Secure**: Automatic HTTPS
- **Always online**: 99.99% uptime
- **Free**: No cost for this use case

## Automatic Deployments

Vercel automatically deploys when you push to GitHub:

### Production Deployment
Push to `main` branch:
```bash
git add .
git commit -m "Update SEO report"
git push origin main
```
→ Deploys to your production URL

### Preview Deployments
Push to any other branch or create a Pull Request:
```bash
git checkout -b updates
git add .
git commit -m "Draft updates"
git push origin updates
```
→ Creates a unique preview URL for testing

## Updating Your Report

To update the SEO report after initial deployment:

1. Edit your markdown files in `src/content/docs/`
2. Test locally: `npm run dev`
3. Commit and push:
   ```bash
   git add .
   git commit -m "Update [section name]"
   git push origin main
   ```
4. Vercel automatically rebuilds and deploys in ~1-2 minutes

## Troubleshooting

### Build Fails

**Check the build logs** in Vercel dashboard:

Common issues:
- **Missing frontmatter**: Ensure all `.md` files have valid frontmatter
- **Invalid markdown**: Check for syntax errors in markdown
- **Missing content**: Ensure `src/content/docs/` has at least one file

**Local test first**:
```bash
npm run build
```

### Site Shows 404

- Ensure your markdown files are in `src/content/docs/` (not `src/pages/`)
- Check that frontmatter has a `title` field
- Verify the build completed successfully

### Styles Not Loading

- Clear Vercel cache and redeploy:
  1. Vercel Dashboard → Deployments
  2. Click "..." menu → "Redeploy"
  3. Check "Use existing Build Cache" is OFF

## Performance Optimization

Your Astro site is already optimized, but here are some tips:

### Images
Add images to `public/images/` and reference them:
```markdown
![Description](/images/chart.png)
```

For better performance, use optimized images:
- PNG/JPG for photos
- SVG for diagrams
- WebP for smaller file sizes

### Analytics (Optional)

Add Vercel Analytics:
1. Project Settings → "Analytics"
2. Enable Web Analytics
3. View traffic insights in dashboard

Or add Google Analytics in `src/layouts/BaseLayout.astro`:
```astro
<head>
  <!-- Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'GA_MEASUREMENT_ID');
  </script>
</head>
```

## Cost

For SEO reports, Vercel is **100% free**:
- Hobby (free) tier includes:
  - Unlimited personal projects
  - 100 GB bandwidth per month
  - HTTPS included
  - Global CDN
  - Automatic deployments

This is more than enough for client SEO reports.

## Security

Your deployed reports are:
- **Public by default**: Anyone with the URL can view
- **Secure**: HTTPS encrypted
- **No client data at risk**: Static site, no backend/database

### Password Protection (Optional)

To password-protect a report (requires Vercel Pro):

1. Upgrade to Vercel Pro ($20/month)
2. Enable "Password Protection" in project settings
3. Set a password
4. Share password with client separately

**Alternative**: Use Vercel's branch deployments for preview URLs that are harder to guess.

## Need Help?

- **Vercel Docs**: [vercel.com/docs](https://vercel.com/docs)
- **Astro Docs**: [docs.astro.build](https://docs.astro.build)
- **Comcreate Support**: sales@comcreate.org or (619) 955-0105

---

**Congratulations!** Your SEO report is now live and accessible to your client 24/7.
