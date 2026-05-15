---
name: ai-website-deployment
description: Deploys AI-generated websites to production using Netlify. Use when the user wants to host a website, deploy to a live URL, or publish an Anti-Gravity project online.
---

# AI Website Deployment

Deploy Anti-Gravity generated websites to Netlify for free hosting.

## When to use this skill
- User wants to deploy a website
- User needs a live URL for their project
- User mentions Netlify or hosting
- User wants to share their Anti-Gravity project

## Deployment Methods

### Method 1: Manual Deploy (Quick)
Best for one-time deployments or demos.

### Method 2: GitHub Integration (Continuous)
Best for ongoing projects with version control.

## Method 1: Manual Deploy Workflow

### Phase 1: Build the Project
- [ ] Open Anti-Gravity terminal
- [ ] Run `npm run build`
- [ ] Locate the `out` folder (or `dist`/`.next`)

### Phase 2: Deploy to Netlify
- [ ] Go to netlify.com
- [ ] Click "Add new site" → "Deploy manually"
- [ ] Drag and drop the `out` folder
- [ ] Wait for deployment
- [ ] Copy the generated URL

## Terminal Commands

### Build Static Export (Next.js)
```bash
npm run build
```

> **Note**: For static export to work, ensure `next.config.js` has:
> ```js
> output: 'export'
> ```

### Locate Build Output
The output folder is typically:
- Next.js: `out/` or `.next/`
- Vite: `dist/`
- Create React App: `build/`

## Netlify Manual Deploy Steps

1. Go to [app.netlify.com](https://app.netlify.com)
2. Click **"Add new site"**
3. Select **"Deploy manually"**
4. **Drag and drop** your build folder
5. Wait for deployment (usually < 1 minute)
6. Copy the URL (format: `random-name.netlify.app`)

## Setting Custom Domain

After deployment:
1. Go to **Site settings** → **Domain management**
2. Click **"Add custom domain"**
3. Follow DNS configuration instructions

## Method 2: GitHub Integration

### Setup
1. Push project to GitHub repository
2. Connect Netlify to GitHub
3. Select repository
4. Configure build settings:
   - Build command: `npm run build`
   - Publish directory: `out`

### Benefits
- Automatic deploys on git push
- Preview deployments for PRs
- Rollback capabilities

## Common Issues

### "Build Failed" Error
Ensure static export is configured:
```javascript
// next.config.js
module.exports = {
  output: 'export',
  images: {
    unoptimized: true
  }
}
```

### Images Not Loading
For static export, ensure images are in `/public/` folder and referenced with absolute paths.

### Large File Size
- Compress images before build
- Remove unused dependencies
- Check for accidentally included videos

## Alternative Hosting

| Platform | Free Tier | Best For |
|----------|-----------|----------|
| Netlify | Yes | Static sites |
| Vercel | Yes | Next.js apps |
| GitHub Pages | Yes | Simple HTML |
| Cloudflare Pages | Yes | Edge performance |

## Quick Deploy Checklist

```markdown
- [ ] Build succeeds locally
- [ ] `out/` folder exists
- [ ] Images load correctly
- [ ] No console errors
- [ ] Mobile responsive
- [ ] Drag to Netlify
- [ ] Test live URL
```

## Resources
- [Netlify](https://netlify.com)
- [Vercel](https://vercel.com)
- [Next.js Static Export Docs](https://nextjs.org/docs/pages/building-your-application/deploying/static-exports)
