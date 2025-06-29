# GitHub Upload Guide for Y-It.Shop

## 🚀 Quick Upload to GitHub

### Step 1: Create Repository
1. Go to [github.com/hagermann00](https://github.com/hagermann00)
2. Click "New repository" or go to existing `y-it.shop` repo
3. Repository name: `y-it.shop`
4. Set to Public (required for GitHub Pages with free account)
5. Don't initialize with README (we have our own files)

### Step 2: Upload Files
**Option A: Web Interface (Easiest)**
1. Click "uploading an existing file"
2. Drag and drop ALL files from this folder
3. Commit message: "Initial Y-It Systems website deployment"
4. Click "Commit changes"

**Option B: Git Commands**
```bash
git clone https://github.com/hagermann00/y-it.shop.git
cd y-it.shop
# Copy all files from this package into the cloned directory
git add .
git commit -m "Initial Y-It Systems website deployment"
git push origin main
```

### Step 3: Enable GitHub Pages
1. Go to repository Settings
2. Scroll to "Pages" section
3. Source: "Deploy from a branch"
4. Branch: `gh-pages` (will be created automatically by GitHub Actions)
5. Folder: `/ (root)`

### Step 4: Configure Custom Domain
1. In Pages settings, add custom domain: `y-it.shop`
2. Check "Enforce HTTPS"
3. GitHub will verify domain ownership

### Step 5: DNS Configuration
Configure your domain registrar with these DNS records:

**A Records:**
```
Type: A
Name: @
Value: 185.199.108.153

Type: A  
Name: @
Value: 185.199.109.153

Type: A
Name: @
Value: 185.199.110.153

Type: A
Name: @
Value: 185.199.111.153
```

**CNAME Record:**
```
Type: CNAME
Name: www
Value: hagermann00.github.io
```

## 🔧 Automatic Deployment
- GitHub Actions will automatically build and deploy on every push to main branch
- First deployment may take 5-10 minutes
- Subsequent deployments take 2-3 minutes

## 📋 Files Included
- ✅ Complete React application
- ✅ GitHub Actions workflow
- ✅ Deployment configurations (Vercel, Netlify)
- ✅ Custom domain setup (CNAME)
- ✅ README and documentation
- ✅ All dependencies and build configs

## 🚨 Important Notes
1. **Repository must be PUBLIC** for GitHub Pages (free tier)
2. **Domain propagation** can take up to 24 hours
3. **SSL certificate** will be automatically provisioned
4. **First build** may take longer than subsequent ones

## 🔍 Troubleshooting
- **Build fails**: Check Actions tab for error details
- **Domain not working**: Verify DNS propagation at [whatsmydns.net](https://whatsmydns.net)
- **404 errors**: Ensure GitHub Pages is enabled and branch is correct

## 📞 Need Help?
Check the DEPLOYMENT.md file for detailed troubleshooting and alternative hosting options.

