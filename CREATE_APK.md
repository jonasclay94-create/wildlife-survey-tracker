# 📦 Creating an APK from Wildlife Survey Tracker PWA

This guide will show you how to convert your PWA into a native Android APK file that can be installed on any Android device.

---

## 🎯 Method 1: PWA Builder (Easiest - No Coding Required)

**Best for:** Non-developers, quick testing, simple APKs

### Step 1: Host Your PWA Online

You must host your PWA online with HTTPS before building an APK.

**Quick Option - GitHub Pages (Free):**

1. Create a GitHub account at github.com
2. Create a new repository (name it `wildlife-survey-tracker`)
3. Upload all your files:
   - index.html
   - manifest.json
   - service-worker.js
   - icon-192.png
   - icon-512.png
4. Go to **Settings** > **Pages**
5. Select your branch (main/master) and click **Save**
6. Your app will be live at: `https://yourusername.github.io/wildlife-survey-tracker/`

### Step 2: Use PWA Builder

1. Go to **https://www.pwabuilder.com/**
2. Enter your PWA URL (from GitHub Pages)
3. Click **Start** and wait for analysis
4. Review the report and fix any issues if needed
5. Click on **Package For Stores** tab
6. Select **Android** platform
7. Click **Generate Package**
8. Download your APK file!

### Step 3: Install the APK

1. Transfer the APK to your Android device
2. Enable **Install Unknown Apps** in Settings
3. Open the APK file and install
4. Done! 🎉

**Pros:**
- ✅ Super easy, no technical knowledge needed
- ✅ Works in minutes
- ✅ No software installation required

**Cons:**
- ❌ Requires online hosting first
- ❌ Less customization options
- ❌ May have size limitations

---

## 🛠️ Method 2: Capacitor (Recommended - Full Control)

**Best for:** Developers, production apps, full customization

### Prerequisites

Install these first:
- **Node.js** (v18 or later) - https://nodejs.org/
- **Android Studio** - https://developer.android.com/studio
- **Java JDK** (comes with Android Studio)

### Step 1: Setup Capacitor Project

Open a terminal/command prompt:

```bash
# Create a new folder for your project
mkdir wildlife-survey-app
cd wildlife-survey-app

# Initialize npm project
npm init -y

# Install Capacitor
npm install @capacitor/core @capacitor/cli
npm install @capacitor/android

# Initialize Capacitor
npx cap init "Wildlife Survey Tracker" "com.wildlife.surveytracker"
```

When prompted:
- **App name:** Wildlife Survey Tracker
- **Package ID:** com.wildlife.surveytracker (or your own domain)
- **Web directory:** www

### Step 2: Prepare Your Web Files

```bash
# Create www directory
mkdir www

# Copy your files to www folder:
# - index.html
# - manifest.json
# - service-worker.js
# - icon-192.png
# - icon-512.png
```

On **Windows:**
```cmd
copy index.html www\
copy manifest.json www\
copy service-worker.js www\
copy icon-192.png www\
copy icon-512.png www\
```

On **Mac/Linux:**
```bash
cp index.html www/
cp manifest.json www/
cp service-worker.js www/
cp icon-192.png www/
cp icon-512.png www/
```

### Step 3: Configure Capacitor

Edit `capacitor.config.json`:

```json
{
  "appId": "com.wildlife.surveytracker",
  "appName": "Wildlife Survey Tracker",
  "webDir": "www",
  "server": {
    "androidScheme": "https"
  }
}
```

### Step 4: Add Android Platform

```bash
# Add Android platform
npx cap add android

# Sync files
npx cap sync android
```

### Step 5: Open in Android Studio

```bash
# Open project in Android Studio
npx cap open android
```

This will launch Android Studio with your project.

### Step 6: Configure App Icons (in Android Studio)

1. In Android Studio, right-click on `app/src/main/res`
2. Select **New** > **Image Asset**
3. Choose **Launcher Icons**
4. Upload your `icon-512.png`
5. Click **Next** then **Finish**

### Step 7: Build APK

In Android Studio:

1. Click **Build** menu
2. Select **Build Bundle(s) / APK(s)**
3. Click **Build APK(s)**
4. Wait for build to complete
5. Click **locate** to find your APK

**APK Location:**
```
wildlife-survey-app/android/app/build/outputs/apk/debug/app-debug.apk
```

### Step 8: Install on Device

```bash
# Connect your Android device via USB
# Enable USB debugging in Developer Options

# Install using ADB
adb install android/app/build/outputs/apk/debug/app-debug.apk
```

Or transfer the APK to your device and install manually.

---

## 🏭 Method 3: Production-Ready APK (For Publishing)

### Create Signed APK for Google Play Store

**Step 1: Generate Keystore**

```bash
# Navigate to android/app
cd android/app

# Generate keystore (do this ONCE and keep it safe!)
keytool -genkey -v -keystore wildlife-survey.keystore -alias wildlife-tracker -keyalg RSA -keysize 2048 -validity 10000
```

Save the password securely!

**Step 2: Configure Signing**

Create `android/app/gradle.properties`:

```properties
MYAPP_RELEASE_STORE_FILE=wildlife-survey.keystore
MYAPP_RELEASE_KEY_ALIAS=wildlife-tracker
MYAPP_RELEASE_STORE_PASSWORD=YOUR_PASSWORD_HERE
MYAPP_RELEASE_KEY_PASSWORD=YOUR_PASSWORD_HERE
```

**Step 3: Update Build Configuration**

Edit `android/app/build.gradle`:

```gradle
android {
    ...
    signingConfigs {
        release {
            storeFile file(MYAPP_RELEASE_STORE_FILE)
            storePassword MYAPP_RELEASE_STORE_PASSWORD
            keyAlias MYAPP_RELEASE_KEY_ALIAS
            keyPassword MYAPP_RELEASE_KEY_PASSWORD
        }
    }
    buildTypes {
        release {
            signingConfig signingConfigs.release
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}
```

**Step 4: Build Release APK**

```bash
# Navigate to android folder
cd android

# Build release APK
./gradlew assembleRelease

# APK will be at:
# android/app/build/outputs/apk/release/app-release.apk
```

---

## 📱 Method 4: Using Cordova (Alternative)

### Step 1: Install Cordova

```bash
npm install -g cordova
```

### Step 2: Create Cordova Project

```bash
# Create project
cordova create wildlife-survey com.wildlife.surveytracker "Wildlife Survey Tracker"

# Navigate to project
cd wildlife-survey

# Add Android platform
cordova platform add android
```

### Step 3: Copy Your Files

Copy all your files to the `www` folder:
```bash
# Remove default files
rm -rf www/*

# Copy your files
cp /path/to/your/index.html www/
cp /path/to/your/manifest.json www/
cp /path/to/your/service-worker.js www/
cp /path/to/your/*.png www/
```

### Step 4: Configure App

Edit `config.xml`:

```xml
<?xml version='1.0' encoding='utf-8'?>
<widget id="com.wildlife.surveytracker" version="1.0.0" xmlns="http://www.w3.org/ns/widgets">
    <name>Wildlife Survey Tracker</name>
    <description>
        Multi-record wildlife surveys with geolocation
    </description>
    <author email="your@email.com" href="https://yoursite.com">
        Your Name
    </author>
    <content src="index.html" />
    <access origin="*" />
    <allow-intent href="http://*/*" />
    <allow-intent href="https://*/*" />
    <platform name="android">
        <allow-intent href="market:*" />
    </platform>

    <!-- Permissions -->
    <preference name="permissions" value="none"/>
    <feature name="Geolocation">
        <param name="android-package" value="org.apache.cordova.geolocation.Geolocation"/>
    </feature>
</widget>
```

### Step 5: Install Geolocation Plugin

```bash
cordova plugin add cordova-plugin-geolocation
```

### Step 6: Build APK

```bash
# Debug build
cordova build android

# Release build (after setting up keystore)
cordova build android --release
```

**APK Location:**
```
platforms/android/app/build/outputs/apk/debug/app-debug.apk
```

---

## 🎨 Creating App Icons

You need icons in multiple sizes for Android. Here's the easiest way:

### Option 1: Online Generator

1. Go to https://icon.kitchen/
2. Upload your icon image
3. Select "Android" platform
4. Download the generated icons
5. Replace files in `android/app/src/main/res/` folders

### Option 2: Manual Creation

Create these icon sizes:
- `mipmap-mdpi/ic_launcher.png` - 48x48
- `mipmap-hdpi/ic_launcher.png` - 72x72
- `mipmap-xhdpi/ic_launcher.png` - 96x96
- `mipmap-xxhdpi/ic_launcher.png` - 144x144
- `mipmap-xxxhdpi/ic_launcher.png` - 192x192

---

## 🔧 Troubleshooting

### "JAVA_HOME not set"
- Install Java JDK from Android Studio
- Set JAVA_HOME environment variable

### "Android SDK not found"
- Open Android Studio
- Go to Settings > Appearance & Behavior > System Settings > Android SDK
- Note the SDK location
- Set ANDROID_HOME environment variable

### "Build failed"
- Make sure all files are in the `www` folder
- Check `manifest.json` is valid JSON
- Ensure all icon files exist

### "App crashes on launch"
- Check browser console for errors
- Make sure service-worker.js paths are correct
- Test the PWA in browser first

### APK size too large
- Remove unused images
- Minify JavaScript
- Compress images

---

## 📋 Comparison of Methods

| Method | Difficulty | Time | Customization | Best For |
|--------|-----------|------|---------------|----------|
| PWA Builder | ⭐ Easy | 10 min | Low | Quick testing |
| Capacitor | ⭐⭐⭐ Medium | 30 min | High | Production apps |
| Cordova | ⭐⭐⭐ Medium | 30 min | High | Legacy projects |

---

## 🚀 Recommended Workflow

**For Testing:**
1. Use PWA Builder for quick APK
2. Test on real device
3. Iterate on your web code

**For Production:**
1. Use Capacitor for full control
2. Create signed release APK
3. Test thoroughly
4. Publish to Play Store (optional)

---

## 📱 Installing APK on Android

### Enable Installation from Unknown Sources

**Android 8.0+:**
1. Go to **Settings** > **Apps & Notifications**
2. Tap **Advanced** > **Special App Access**
3. Tap **Install Unknown Apps**
4. Select your browser or file manager
5. Enable **Allow from this source**

**Older Android:**
1. Go to **Settings** > **Security**
2. Enable **Unknown Sources**

### Install the APK

1. Transfer APK to your Android device via:
   - USB cable
   - Email attachment
   - Cloud storage (Drive, Dropbox)
   - Direct download
2. Tap the APK file
3. Tap **Install**
4. Wait for installation
5. Tap **Open** to launch!

---

## 🎯 Tips for Success

✅ Test your PWA thoroughly in browser first
✅ Make sure all features work offline
✅ Create high-quality app icons
✅ Test on real Android devices
✅ Keep your keystore file SAFE (you can't recover it!)
✅ Start with PWA Builder for quick tests
✅ Use Capacitor for production apps

---

## 📚 Additional Resources

- **Capacitor Docs:** https://capacitorjs.com/docs
- **PWA Builder:** https://www.pwabuilder.com/
- **Cordova Docs:** https://cordova.apache.org/docs/
- **Android Studio:** https://developer.android.com/studio
- **Icon Generator:** https://icon.kitchen/

---

## ⚠️ Important Notes

1. **Keystore Security:** NEVER lose your keystore file or password! You can't update your app without it.

2. **Package Name:** Use a unique package ID like `com.yourname.wildlifesurvey` (must be unique if publishing to Play Store)

3. **Permissions:** The app requests location permissions for GPS features. Users must grant this on first use.

4. **Data Storage:** All data is stored locally using IndexedDB. Uninstalling the app will delete all data!

5. **Updates:** To update your app:
   - Update your web files
   - Rebuild the APK
   - Increment version number
   - Reinstall on device

---

Good luck building your APK! 🎉

For the easiest experience, start with **Method 1 (PWA Builder)**. If you need more control, use **Method 2 (Capacitor)**.
