# Y-It.Shop Deployment Guide

## 🚀 Quick Deployment to y-it.shop

### Option 1: Vercel (Recommended)
1. **Connect Repository**
   - Go to [vercel.com](https://vercel.com)
   - Import your GitHub repository: `hagermann00/y-it.shop`
   - Vercel will auto-detect the React/Vite setup

2. **Configure Build Settings**
   - Build Command: `npm run build`
   - Output Directory: `dist`
   - Install Command: `npm install`

3. **Add Custom Domain**
   - Go to Project Settings → Domains
   - Add `y-it.shop` and `www.y-it.shop`
   - Configure DNS records as instructed by Vercel

### Option 2: Netlify
1. **Connect Repository**
   - Go to [netlify.com](https://netlify.com)
   - New site from Git → GitHub → Select `y-it.shop` repo

2. **Build Settings**
   - Build command: `npm run build`
   - Publish directory: `dist`

3. **Custom Domain**
   - Site settings → Domain management
   - Add custom domain: `y-it.shop`

### Option 3: GitHub Pages
1. **Enable GitHub Pages**
   - Repository Settings → Pages
   - Source: GitHub Actions

2. **Create Workflow File**
   Create `.github/workflows/deploy.yml`:
   ```yaml
   name: Deploy to GitHub Pages
   on:
     push:
       branches: [ main ]
   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v3
         - uses: actions/setup-node@v3
           with:
             node-version: 18
         - run: npm install
         - run: npm run build
         - uses: peaceiris/actions-gh-pages@v3
           with:
             github_token: ${{ secrets.GITHUB_TOKEN }}
             publish_dir: ./dist
   ```

## 📋 Pre-Deployment Checklist

- [ ] Repository is public or you have proper access
- [ ] All dependencies are in package.json
- [ ] Build command works locally (`npm run build`)
- [ ] Custom domain DNS is configured
- [ ] SSL certificate is enabled

## 🔧 DNS Configuration for y-it.shop

### For Vercel:
```
Type: A
Name: @
Value: 76.76.19.61

Type: CNAME
Name: www
Value: cname.vercel-dns.com
```

### For Netlify:
```
Type: A
Name: @
Value: 75.2.60.5

Type: CNAME
Name: www
Value: [your-site-name].netlify.app
```

## 🚨 Important Notes

1. **Build Time**: First deployment may take 2-3 minutes
2. **Cache**: Changes may take up to 24 hours to propagate globally
3. **HTTPS**: SSL certificates are automatically provisioned
4. **Redirects**: Both www and non-www versions will work

## 🔍 Troubleshooting

### Build Fails
- Check Node.js version (should be 18+)
- Verify all dependencies are installed
- Run `npm run build` locally first

### Domain Not Working
- Check DNS propagation: [whatsmydns.net](https://whatsmydns.net)
- Verify domain ownership in hosting platform
- Ensure SSL certificate is active

### 404 Errors
- Check that SPA redirects are configured
- Verify `vercel.json` or `netlify.toml` is present

## 📞 Support
If you encounter issues, check the hosting platform's documentation or contact their support team.

