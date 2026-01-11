# 🚀 Quick Start - GitHub Actions Deployment

## ⚡ Fast Setup (5 Minutes)

### 1️⃣ **Create GitHub Repository**
- Go to GitHub → New repository
- Name: `yourusername.github.io` (or any name)
- Make it **Public**
- **Don't** initialize with README

### 2️⃣ **Push Your Code**
```bash
git add .
git commit -m "Add GitHub Actions workflow"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git branch -M main
git push -u origin main
```

### 3️⃣ **Enable GitHub Pages**
- Repository → **Settings** → **Pages**
- Source: **"GitHub Actions"** (NOT "Deploy from branch")
- Click **Save**

### 4️⃣ **Done! 🎉**
- Go to **Actions** tab to see deployment
- Your site: `https://yourusername.github.io`

---

## 📝 **What Happens Next?**

Every time you run `git push`:
1. ✅ GitHub Actions automatically builds Tailwind CSS
2. ✅ Deploys to GitHub Pages
3. ✅ Your site updates in 1-2 minutes

**No manual steps needed!**

---

## 📖 **For Detailed Instructions**

See: **[GITHUB_ACTIONS_SETUP.md](GITHUB_ACTIONS_SETUP.md)**

---

## ✅ **Files Created**

- ✅ `.github/workflows/deploy.yml` - GitHub Actions workflow
- ✅ `.gitignore` - Excludes node_modules
- ✅ `package.json` - Updated with build script

**All set! Just push and deploy! 🚀**

