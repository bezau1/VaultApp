# Vault — Encrypted Notes App

A native Android wrapper for the Vault encrypted notes web app.  
Uses AES-256-GCM encryption entirely in the browser (WebCrypto API).  
Notes are stored in the app's local storage — never sent anywhere.

---

## 🛡️ Security Notes

- `FLAG_SECURE` is set: screenshots and screen recording are blocked by the OS
- No internet permission is used (the HTML is loaded from app assets)
- All encryption/decryption happens locally via the WebCrypto API

---

## 🔨 How to Build

### Option A — Android Studio (Easiest)

1. Install [Android Studio](https://developer.android.com/studio)
2. Open this folder as a project (`File → Open`)
3. Let it sync Gradle (it will download dependencies automatically)
4. Click **▶ Run** (or `Build → Build APK`)
5. The debug APK will be at:  
   `app/build/outputs/apk/debug/app-debug.apk`

### Option B — Command Line

Make sure you have:
- Android SDK installed (via Android Studio or standalone)
- `ANDROID_HOME` environment variable set
- Java 17 or higher

```bash
# Edit local.properties to point to your SDK first, then:
./gradlew assembleDebug

# APK output:
# app/build/outputs/apk/debug/app-debug.apk
```

### Option C — Install directly with ADB (after building)

```bash
adb install app/build/outputs/apk/debug/app-debug.apk
```

---

## 📁 Project Structure

```
VaultApp/
├── app/
│   └── src/main/
│       ├── assets/
│       │   └── index.html          ← The full Vault web app
│       ├── java/com/vault/app/
│       │   └── MainActivity.java   ← WebView wrapper
│       ├── res/
│       │   ├── layout/             ← Layout XML
│       │   ├── mipmap-hdpi/        ← Launcher icon
│       │   └── values/themes.xml   ← Dark purple theme
│       └── AndroidManifest.xml
├── build.gradle
├── settings.gradle
└── local.properties                ← Edit SDK path here
```

---

## Minimum Requirements

- Android 8.0 (API 26) or higher
- The WebView component (standard on all modern Android)
