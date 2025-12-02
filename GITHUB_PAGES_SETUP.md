# 🚀 GitHub Pages Setup Guide - Wildlife Survey Tracker

Follow these steps to get your PWA live on the internet for FREE!

---

## 📋 Prerequisites

- A GitHub account (free) - Sign up at https://github.com/signup

---

## 🎯 Step-by-Step Instructions

### Step 1: Create a GitHub Account (if you don't have one)

1. Go to https://github.com/signup
2. Enter your email, password, and username
3. Verify your email address
4. Complete the setup

### Step 2: Create a New Repository

1. Go to https://github.com/new (or click the **+** icon → **New repository**)
2. Fill in the details:
   - **Repository name:** `wildlife-survey-tracker` (or any name you prefer)
   - **Description:** "Wildlife Survey Tracker PWA with offline support"
   - **Public** (select this - required for free GitHub Pages)
   - ✅ Check "Add a README file"
3. Click **Create repository**

### Step 3: Upload Your Files

You have two options:

#### Option A: Upload via Web Interface (Easiest)

1. On your repository page, click **Add file** → **Upload files**
2. Drag and drop ALL these files from your computer:
   - `index.html`
   - `manifest.json`
   - `service-worker.js`
   - `INSTALL.md`
   - `CREATE_APK.md`
   - `GITHUB_PAGES_SETUP.md`

   **Note:** You'll need to download these files from the working directory first!

3. Add a commit message: "Initial commit - Wildlife Survey Tracker"
4. Click **Commit changes**

#### Option B: Using Git Command Line (For Advanced Users)

```bash
# Navigate to your working directory
cd /root/workdir

# Initialize git repository
git init

# Add all files
git add index.html manifest.json service-worker.js *.md

# Commit files
git commit -m "Initial commit - Wildlife Survey Tracker"

# Add your GitHub repository as remote
git remote add origin https://github.com/YOUR-USERNAME/wildlife-survey-tracker.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 4: Enable GitHub Pages

1. In your repository, click **Settings** (top menu)
2. In the left sidebar, click **Pages**
3. Under **Source**, select:
   - **Branch:** main
   - **Folder:** / (root)
4. Click **Save**
5. Wait 1-2 minutes for deployment

### Step 5: Get Your PWA URL

After a few minutes, you'll see a message:

> ✅ Your site is live at https://YOUR-USERNAME.github.io/wildlife-survey-tracker/

**This is your PWA URL!** 🎉

### Step 6: Test Your PWA

1. Visit your URL in Chrome or Safari
2. You should see your Wildlife Survey Tracker
3. Look for the **Install** button in the address bar
4. Click it to install the PWA!

---

## 🎨 Adding App Icons (Optional but Recommended)

Your app currently references these icon files:
- `icon-192.png` (192x192 pixels)
- `icon-512.png` (512x512 pixels)

### Quick Icon Creation:

1. **Use an online generator:**
   - Go to https://favicon.io/favicon-generator/
   - Or use https://realfavicongenerator.net/

2. **Upload a wildlife image** (lizard, dormouse, leaf, etc.)

3. **Download the generated icons**

4. **Rename the files to:**
   - `icon-192.png`
   - `icon-512.png`

5. **Upload to your GitHub repository**:
   - Go to your repository
   - Click **Add file** → **Upload files**
   - Upload both icon files
   - Commit changes

### Simple Icon Creation (If you don't have an image):

I can help you create a simple text-based icon:

1. Go to https://favicon.io/favicon-generator/
2. Settings:
   - **Text:** 🦎 (or 🐭)
   - **Background:** #7c3aed (purple)
   - **Font:** Any you like
3. Click **Download**
4. Extract and find the PNG files
5. Upload to GitHub as described above

---

## 📱 Installing Your PWA

### On Android (Chrome/Edge):

1. Open your GitHub Pages URL in Chrome
2. Tap the menu (⋮) → **Install app** or **Add to Home screen**
3. The app icon will appear on your home screen
4. Launch it like any other app!

### On iOS (Safari):

1. Open your GitHub Pages URL in Safari
2. Tap the **Share** button
3. Scroll and tap **Add to Home Screen**
4. Name it and tap **Add**
5. Find it on your home screen!

### On Desktop (Chrome/Edge):

1. Open your GitHub Pages URL
2. Click the install icon (⊕) in the address bar
3. Click **Install**
4. The app opens in its own window!

---

## 🔄 Updating Your App

When you make changes:

1. Edit your files locally
2. Go to your GitHub repository
3. Click on the file you want to update
4. Click the **pencil icon** (Edit)
5. Make your changes
6. Click **Commit changes**
7. Wait 1-2 minutes for deployment
8. Your PWA will auto-update!

Or upload new versions:
1. **Add file** → **Upload files**
2. Drag the updated file (it will replace the old one)
3. Commit changes

---

## 🐛 Troubleshooting

### "404 - Page not found"
- Wait 2-5 minutes after enabling GitHub Pages
- Make sure `index.html` is in the root folder
- Check Settings → Pages shows the correct URL

### PWA won't install
- Make sure you're using HTTPS (GitHub Pages provides this automatically)
- Check browser console (F12) for errors
- Try clearing cache and reloading

### Icons not showing
- Make sure `icon-192.png` and `icon-512.png` are uploaded
- Check file names match exactly (case-sensitive)
- Clear cache and reinstall the PWA

### Service worker not working
- Check `service-worker.js` is in the root folder
- Visit the URL with `/service-worker.js` to verify it's accessible
- Check browser console for service worker registration errors

---

## ✅ Checklist

Before going live, make sure:

- [ ] All files uploaded to GitHub
- [ ] GitHub Pages enabled in Settings
- [ ] Site is accessible at the GitHub Pages URL
- [ ] App icons uploaded (optional but recommended)
- [ ] PWA installs correctly on a test device
- [ ] Offline mode works (try airplane mode)
- [ ] GPS location works (requires HTTPS ✅)

---

## 🎉 You're Done!

Your Wildlife Survey Tracker is now:
- ✅ Live on the internet
- ✅ Installable as a PWA
- ✅ Works offline
- ✅ Shareable with anyone
- ✅ Free forever!

**Your PWA URL:**
```
https://YOUR-USERNAME.github.io/wildlife-survey-tracker/
```

Share this URL with your team, install it on your devices, and start tracking wildlife! 🦎🐭

---

## 🚀 Next Steps

1. **Create an APK** - Follow `CREATE_APK.md` to create an Android APK
2. **Share the URL** - Send it to your team members
3. **Install on devices** - Add to home screen on all your devices
4. **Start surveying** - Your data saves automatically!

---

## 💡 Pro Tips

- **Custom Domain:** You can add a custom domain (yourname.com) to GitHub Pages for free!
- **SSL Certificate:** GitHub Pages provides free HTTPS automatically
- **Unlimited Bandwidth:** Share your PWA with as many people as you want
- **Version Control:** All changes are tracked in Git history
- **Backups:** Your code is safely backed up on GitHub

---

## 📞 Need Help?

If you run into issues:
1. Check the troubleshooting section above
2. Visit GitHub Pages docs: https://pages.github.com/
3. Check browser console (F12) for errors
4. Make sure all files are in the root directory

Happy surveying! 🎉
