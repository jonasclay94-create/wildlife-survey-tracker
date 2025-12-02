# 📱 Wildlife Survey Tracker - PWA Installation Guide

Your Wildlife Survey Tracker is now a **Progressive Web App (PWA)**! This means you can install it on your device like a native app and use it offline.

## ✨ Features

- ✅ **Works Offline** - All data stored locally on your device
- ✅ **Install Like an App** - Add to home screen on any device
- ✅ **No App Store Needed** - Install directly from your browser
- ✅ **Persistent Data** - Your surveys and projects are saved using IndexedDB
- ✅ **Cross-Platform** - Works on Android, iOS, Windows, macOS, Linux

---

## 📲 How to Install

### Android (Chrome/Edge)

1. Open the app in Chrome or Edge browser
2. Look for the **"Install"** or **"Add to Home Screen"** prompt at the bottom
3. Tap **"Install"** or **"Add"**
4. The app icon will appear on your home screen
5. Launch it like any other app!

**Alternative Method:**
1. Tap the **⋮** (three dots) menu in the top right
2. Select **"Add to Home screen"** or **"Install app"**
3. Follow the prompts

### iOS/iPadOS (Safari)

1. Open the app in Safari browser
2. Tap the **Share** button (square with arrow pointing up)
3. Scroll down and tap **"Add to Home Screen"**
4. Name it "Survey Tracker" (or whatever you prefer)
5. Tap **"Add"**
6. The app icon will appear on your home screen

**Note:** iOS requires Safari browser for PWA installation.

### Desktop (Chrome/Edge/Brave)

1. Open the app in your browser
2. Look for the **install icon** (⊕) in the address bar
3. Click it and select **"Install"**
4. The app will open in its own window
5. Find it in your applications menu

**Alternative Method:**
1. Click the **⋮** (three dots) menu
2. Select **"Install Wildlife Survey Tracker"** or **"Create shortcut"**
3. Check **"Open as window"** for app-like experience

---

## 🔧 Setup Requirements

### Icons (Optional but Recommended)

The app references two icon files that should be in the same directory as index.html:
- `icon-192.png` (192x192 pixels)
- `icon-512.png` (512x512 pixels)

**Quick Icon Creation:**
You can create simple icons using any image editor, or use an online tool like:
- [Favicon Generator](https://favicon.io/)
- [RealFaviconGenerator](https://realfavicongenerator.net/)

Just upload a wildlife-themed image (lizard, dormouse, etc.) and it will generate the icons for you!

If you don't have icons yet, the app will still work - it just won't have a custom icon on your home screen.

### Files Needed

Make sure these files are all in the same directory:
```
/your-app-folder/
  ├── index.html
  ├── manifest.json
  ├── service-worker.js
  ├── icon-192.png (optional)
  └── icon-512.png (optional)
```

---

## 🌐 Hosting the PWA

To install the PWA, you need to serve it from a web server. Here are some options:

### Option 1: Local Testing (Python)
```bash
# Navigate to your app folder
cd /path/to/your-app-folder

# Python 3
python -m http.server 8000

# Then visit: http://localhost:8000
```

### Option 2: Local Testing (Node.js)
```bash
# Install http-server globally
npm install -g http-server

# Navigate to your app folder and run
http-server -p 8000

# Then visit: http://localhost:8000
```

### Option 3: Deploy to Free Hosting

**GitHub Pages (Free, HTTPS):**
1. Create a GitHub repository
2. Upload all files
3. Go to Settings > Pages
4. Select your branch and save
5. Your app will be live at `https://yourusername.github.io/repo-name/`

**Netlify (Free, HTTPS):**
1. Sign up at netlify.com
2. Drag and drop your folder
3. Get instant HTTPS URL
4. Auto-deploy on updates

**Vercel (Free, HTTPS):**
1. Sign up at vercel.com
2. Import your project
3. Deploy with one click

**Important:** PWAs require HTTPS (or localhost for testing). All the hosting options above provide HTTPS automatically.

---

## 🗄️ Data Storage

### How Your Data is Stored

- **IndexedDB**: All surveys and projects are stored in your browser's IndexedDB
- **Offline-First**: Works completely offline after first load
- **No Cloud**: Data stays on your device (private and secure)

### Backing Up Your Data

Since data is stored locally:

1. **Export CSV regularly** - Use the export buttons to backup your surveys
2. **Export KML files** - Backup GPS data for projects
3. **Browser sync** - If using Chrome/Edge with account sync, data may sync across devices

### Important Notes

- Clearing browser data will delete your surveys!
- Uninstalling the PWA may clear data (export first!)
- Each device/browser has its own separate database

---

## 🔄 Updating the App

When you update the app files:

1. The service worker will detect changes
2. The new version will be cached
3. Refresh the app to see updates
4. Your data is preserved across updates

---

## 🐛 Troubleshooting

### App Won't Install
- Make sure you're using HTTPS (or localhost)
- Try a different browser (Chrome/Edge work best)
- Check that manifest.json is accessible
- Look for errors in browser DevTools (F12)

### Data Not Saving
- Check browser storage permissions
- Make sure you have disk space
- Try clearing cache and reinstalling
- Export your data first!

### Offline Mode Not Working
- Visit the app while online first (to cache assets)
- Check service worker registration in DevTools
- Make sure service-worker.js is in the right location

### GPS Not Working
- Allow location permissions when prompted
- Make sure you're using HTTPS (required for geolocation)
- GPS works best outdoors with clear sky view

---

## 📊 Using the App Offline

Once installed, the app works completely offline:

✅ Create new surveys
✅ Add multiple records with GPS locations
✅ Create and manage projects
✅ View all history and statistics
✅ Export CSV and KML files
✅ Generate email summaries (requires online connection for Poe API)

**Note:** Email summary feature requires internet connection as it uses the Poe AI API.

---

## 🎉 You're All Set!

Your Wildlife Survey Tracker is now installed and ready to use offline!

**Tips:**
- Capture GPS locations for each record to use KML export
- Export CSV regularly to backup your data
- Use projects to organize long-term surveys
- The app saves automatically - no need to worry about losing data

Happy surveying! 🦎🐭
