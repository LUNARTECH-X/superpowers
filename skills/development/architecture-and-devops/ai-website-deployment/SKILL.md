---
name: AI Website Deployment
description: Deploy AI-generated websites to production using modern hosting platforms
---

# AI Website Deployment

Deploy websites created with AI coding assistants to production using Vercel, Netlify, Cloudflare Pages, or GitHub Pages.

## Overview

After an AI assistant generates your website code, follow this workflow to deploy it live:

1. Version control setup
2. Platform selection
3. Configuration
4. Deployment
5. Custom domain (optional)

## Quick Start by Platform

### Vercel (Recommended for Next.js/React)

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy from project directory
vercel

# Follow prompts to:
# - Link to Vercel account
# - Configure project settings
# - Deploy to preview URL

# Deploy to production
vercel --prod
```

### Netlify (Great for Static Sites)

```bash
# Install Netlify CLI
npm i -g netlify-cli

# Login and initialize
netlify login
netlify init

# Deploy draft
netlify deploy

# Deploy to production
netlify deploy --prod
```

### Cloudflare Pages

```bash
# Install Wrangler CLI
npm i -g wrangler

# Login
wrangler login

# Deploy
wrangler pages deploy ./dist
```

### GitHub Pages (Free, Simple)

```bash
# In your repo, enable GitHub Pages:
# Settings → Pages → Source: GitHub Actions

# Or use gh-pages package
npm i -g gh-pages
gh-pages -d dist
```

## Project Configuration

### Vercel (`vercel.json`)

```json
{
  "version": 2,
  "builds": [
    { "src": "package.json", "use": "@vercel/next" }
  ],
  "routes": [
    { "src": "/(.*)", "dest": "/" }
  ]
}
```

### Netlify (`netlify.toml`)

```toml
[build]
  command = "npm run build"
  publish = "dist"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

### Cloudflare Pages

```bash
# Set in dashboard or wrangler.toml
# Build command: npm run build
# Build output directory: dist
# Root directory: /
```

## Framework-Specific Configs

### Vite

```javascript
// vite.config.js
export default {
  base: '/', // or '/repo-name/' for GitHub Pages
  build: {
    outDir: 'dist'
  }
}
```

### Next.js

```javascript
// next.config.js
module.exports = {
  output: 'export', // For static export
  // or leave default for Vercel serverless
}
```

### Plain HTML/CSS/JS

```bash
# No build step needed
# Just deploy the folder containing index.html
vercel ./public
# or
netlify deploy --dir=./public
```

## Environment Variables

### Setting via CLI

```bash
# Vercel
vercel env add VARIABLE_NAME

# Netlify  
netlify env:set VARIABLE_NAME "value"

# Cloudflare
wrangler secret put VARIABLE_NAME
```

### Using `.env` Files

```bash
# .env.production
VITE_API_URL=https://api.example.com
NEXT_PUBLIC_API_KEY=xxx
```

> [!WARNING]
> Never commit secrets to git. Use platform environment variables for sensitive data.

## Custom Domains

### Vercel

```bash
vercel domains add yourdomain.com
# Update DNS: Add CNAME record pointing to cname.vercel-dns.com
```

### Netlify

```bash
netlify domains:add yourdomain.com
# Update DNS per Netlify instructions
```

### Cloudflare Pages

```bash
# Add custom domain in Cloudflare dashboard
# If using Cloudflare DNS, it's automatic
```

## GitHub Actions Workflow

```yaml
# .github/workflows/deploy.yml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          
      - name: Install & Build
        run: |
          npm ci
          npm run build
          
      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.ORG_ID }}
          vercel-project-id: ${{ secrets.PROJECT_ID }}
          vercel-args: '--prod'
```

## Deployment Checklist

### Pre-Deployment
- [ ] `npm run build` succeeds locally
- [ ] All environment variables configured
- [ ] `robots.txt` and `sitemap.xml` present (SEO)
- [ ] Favicon and meta tags configured
- [ ] No console errors in production build

### Post-Deployment
- [ ] Site loads correctly at deployed URL
- [ ] All pages/routes work
- [ ] Forms and interactive features function
- [ ] SSL certificate active (HTTPS)
- [ ] Performance acceptable (run Lighthouse)

## Platform Comparison

| Feature | Vercel | Netlify | Cloudflare | GitHub Pages |
|---------|--------|---------|------------|--------------|
| **Free Tier** | Generous | Generous | Generous | Unlimited |
| **Build Time** | Fast | Fast | Very Fast | Moderate |
| **Serverless** | ✅ Edge Functions | ✅ Functions | ✅ Workers | ❌ |
| **Best For** | Next.js, React | Static, JAMstack | Speed-critical | Simple sites |
| **Custom Domain** | ✅ Free | ✅ Free | ✅ Free | ✅ Free |

## Troubleshooting

### Build Fails
```bash
# Check build logs
vercel logs
netlify build

# Common fixes:
# - Missing dependencies in package.json
# - Node version mismatch (specify in config)
# - Environment variables not set
```

### 404 on Routes
```bash
# For SPAs, add redirect rule:
# All routes → /index.html

# Vercel: vercel.json rewrites
# Netlify: _redirects file or netlify.toml
```

### Assets Not Loading
```bash
# Check base path in build config
# Ensure paths are relative or use correct base URL
```

## Resources

- [Vercel Documentation](https://vercel.com/docs)
- [Netlify Documentation](https://docs.netlify.com/)
- [Cloudflare Pages Docs](https://developers.cloudflare.com/pages/)
- [GitHub Pages Docs](https://docs.github.com/pages)
