# GitHub Actions CI/CD Setup Guide

Complete step-by-step guide to set up automatic deployment for your portfolio using GitHub Actions.

---

## 📋 Prerequisites

- ✅ GitHub account
- ✅ Git installed on your computer
- ✅ Portfolio code ready to push
- ✅ Node.js installed (for local testing)

---

## 🚀 Step-by-Step Setup

### **Step 1: Prepare Your Local Repository**

1. **Open PowerShell/Command Prompt** in your portfolio directory (`D:\Portfolio`)

2. **Check if Git is initialized:**
   ```bash
   git status
   ```
   If you see "not a git repository", initialize it:
   ```bash
   git init
   ```

3. **Add all files:**
   ```bash
   git add .
   ```

4. **Make your first commit:**
   ```bash
   git commit -m "Initial commit - Portfolio with GitHub Actions"
   ```

---

### **Step 2: Create GitHub Repository**

1. **Go to [GitHub.com](https://github.com)** and sign in

2. **Click the "+" icon** (top right) → **"New repository"**

3. **Repository Settings:**
   - **Name:** `yourusername.github.io` (for main site) OR `portfolio` (for project site)
     - Example: `SurajRKU.github.io` or `Portfolio`
   - **Description:** "My professional portfolio website"
   - **Visibility:** ✅ Public** (required for free GitHub Pages)
   - **⚠️ DO NOT** check:
     - ❌ Add a README file
     - ❌ Add .gitignore
     - ❌ Choose a license

4. **Click "Create repository"**

---

### **Step 3: Connect Local Repository to GitHub**

1. **Copy the repository URL** from GitHub (it will show after creation)
   - Example: `https://github.com/SurajRKU/SurajRKU.github.io.git`

2. **In your terminal, run:**
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
   git branch -M main
   git push -u origin main
   ```
   
   **Replace:**
   - `YOUR_USERNAME` with your GitHub username
   - `YOUR_REPO_NAME` with your repository name

3. **Enter your GitHub credentials** when prompted

---

### **Step 4: Enable GitHub Pages Settings**

1. **Go to your repository on GitHub**

2. **Click "Settings"** tab (top menu)

3. **Click "Pages"** in the left sidebar

4. **Under "Source":**
   - Select: **"GitHub Actions"** (NOT "Deploy from a branch")
   - This enables automatic deployment via GitHub Actions

5. **Click "Save"**

---

### **Step 5: Verify GitHub Actions Workflow**

1. **Go to "Actions" tab** in your repository

2. **You should see:**
   - A workflow named "Deploy Portfolio to GitHub Pages"
   - It may show as "Queued" or "In progress"

3. **Click on the workflow** to see the build process

4. **Wait 2-3 minutes** for the first deployment

5. **Once complete, you'll see a green checkmark ✅**

---

### **Step 6: Access Your Live Site**

**For `username.github.io` repository:**
- URL: `https://yourusername.github.io`
- Example: `https://SurajRKU.github.io`

**For project repository:**
- URL: `https://yourusername.github.io/repository-name`
- Example: `https://SurajRKU.github.io/Portfolio`

---

## 🔄 How It Works

### **Automatic Deployment Flow:**

1. **You push code** → `git push`
2. **GitHub Actions triggers** → Detects push to `main` branch
3. **Workflow runs:**
   - ✅ Checks out your code
   - ✅ Sets up Node.js
   - ✅ Installs npm dependencies
   - ✅ Builds Tailwind CSS (`npm run build`)
   - ✅ Deploys to GitHub Pages
4. **Site updates** → Live in 1-2 minutes

### **Manual Trigger:**

You can also trigger deployment manually:
1. Go to **Actions** tab
2. Select **"Deploy Portfolio to GitHub Pages"**
3. Click **"Run workflow"** → **"Run workflow"**

---

## 📝 Making Updates

### **To update your portfolio:**

1. **Edit files locally** (e.g., `index.html`, `src/input.css`)

2. **Test locally** (optional):
   ```bash
   npm install
   npm run build:css
   # Open index.html in browser
   ```

3. **Commit and push:**
   ```bash
   git add .
   git commit -m "Update portfolio content"
   git push
   ```

4. **GitHub Actions automatically:**
   - Builds your CSS
   - Deploys to GitHub Pages
   - Your site updates in 1-2 minutes

5. **Check deployment status:**
   - Go to **Actions** tab
   - See the latest workflow run

---

## 🔍 Troubleshooting

### **❌ Workflow Fails**

**Check:**
1. **Actions tab** → Click failed workflow → See error logs
2. **Common issues:**
   - Missing `package.json` → Make sure it's committed
   - Missing `src/input.css` → Ensure source files are committed
   - Node version issues → Check `package.json` dependencies

### **❌ CSS Not Building**

**Solution:**
- Verify `package.json` has the `build` script:
  ```json
  "scripts": {
    "build": "tailwindcss -i ./src/input.css -o ./dist/output.css --minify"
  }
  ```

### **❌ Site Not Updating**

**Check:**
1. **Actions tab** → Is workflow running successfully?
2. **Pages settings** → Is source set to "GitHub Actions"?
3. **Wait 2-3 minutes** after push**

### **❌ 404 Error on Site**

**Solutions:**
1. **Wait 5 minutes** after first deployment
2. **Check repository name:**
   - For main site: Must be `username.github.io` (exact match)
   - Case-sensitive!
3. **Verify Pages is enabled:**
   - Settings → Pages → Source = "GitHub Actions"

### **❌ Images/Assets Not Loading**

**Check:**
1. **Assets folder is committed:**
   ```bash
   git ls-files Assets/
   ```
2. **Image paths in HTML are relative:**
   - ✅ Correct: `Assets/Suraj_Image.jpeg`
   - ❌ Wrong: `D:\Portfolio\Assets\Suraj_Image.jpeg`

---

## 📁 Files Structure

Your repository should have:
```
Portfolio/
├── .github/
│   └── workflows/
│       └── deploy.yml          ← GitHub Actions workflow
├── Assets/
│   ├── Suraj_Image.jpeg
│   ├── SAP_Logo.png
│   └── ... (all assets)
├── dist/
│   └── output.css              ← Built by GitHub Actions
├── src/
│   └── input.css                ← Tailwind source
├── index.html
├── package.json
├── tailwind.config.js
└── .gitignore
```

---

## ✅ Verification Checklist

Before pushing, ensure:

- [ ] `package.json` has `build` script
- [ ] `.github/workflows/deploy.yml` exists
- [ ] `Assets/` folder is included
- [ ] `index.html` references `./dist/output.css`
- [ ] Repository is **Public**
- [ ] GitHub Pages source is set to **"GitHub Actions"**

---

## 🎯 Quick Commands Reference

```bash
# Check status
git status

# Add all changes
git add .

# Commit
git commit -m "Your message"

# Push to GitHub (triggers deployment)
git push

# View workflow runs
# Go to: https://github.com/username/repo/actions
```

---

## 📚 Additional Resources

- [GitHub Actions Documentation](https://docs.github.com/actions)
- [GitHub Pages Documentation](https://docs.github.com/pages)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)

---

## 🎉 **You're All Set!**

Once configured, every `git push` will automatically:
1. Build your Tailwind CSS
2. Deploy to GitHub Pages
3. Update your live site

**No manual steps needed!** 🚀

---

## 💡 Pro Tips

1. **Monitor deployments:** Check Actions tab regularly
2. **Test locally first:** Run `npm run build` before pushing
3. **Use meaningful commit messages:** Helps track changes
4. **Keep dependencies updated:** Run `npm update` periodically

---

**Need Help?** Check the Actions tab logs for detailed error messages!

