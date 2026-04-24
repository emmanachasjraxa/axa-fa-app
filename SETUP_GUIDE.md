# AXA FA Command Center — Setup Guide
## Works online + offline · Installs on phone, iPad & computer · Real-time sync

---

## STEP 1: Host the files for free on GitHub Pages (5 minutes)

1. Go to https://github.com and create a free account (if you don't have one)
2. Click the **+** button → **New repository**
3. Name it: `axa-fa-app`
4. Set it to **Public**, check "Add a README file", then click **Create repository**
5. Click **Add file** → **Upload files**
6. Upload ALL files from the axa-pwa folder:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`
7. Click **Commit changes**
8. Go to **Settings** → **Pages** (left sidebar)
9. Under "Branch", select **main** → **/root** → click **Save**
10. After ~2 minutes, your app URL will be:
    `https://YOUR-GITHUB-USERNAME.github.io/axa-fa-app`

---

## STEP 2: Set up free real-time sync with Firebase (10 minutes)

1. Go to https://console.firebase.google.com
2. Click **Create a project** → name it `axa-fa-sync` → Continue
3. Disable Google Analytics (not needed) → **Create project**
4. In the left sidebar, click **Firestore Database**
5. Click **Create database** → choose **Start in test mode** → select a region close to you (e.g. asia-southeast1 for Philippines) → **Enable**
6. In the left sidebar, click **Project Settings** (gear icon)
7. Scroll down to **Your apps** → click the **</>** (Web) icon
8. Register app name: `axa-fa-app` → click **Register app**
9. You'll see a config block like this:

```javascript
const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "axa-fa-sync.firebaseapp.com",
  projectId: "axa-fa-sync",
  storageBucket: "axa-fa-sync.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

10. Open `index.html` and find this line near the top of the `<script>` section:
```javascript
const FB_CONFIG = null; // PASTE YOUR FIREBASE CONFIG HERE
```
11. Replace it with your config:
```javascript
const FB_CONFIG = {
  apiKey: "AIza...",
  authDomain: "axa-fa-sync.firebaseapp.com",
  projectId: "axa-fa-sync",
  ...
};
```
12. Save and re-upload `index.html` to GitHub Pages

---

## STEP 3: Install as an app on each device

### iPhone / iPad (Safari):
1. Open your GitHub Pages URL in **Safari**
2. Tap the **Share** button (box with arrow)
3. Tap **"Add to Home Screen"**
4. Tap **Add**
5. The AXA FA icon will appear on your home screen like a real app

### Android:
1. Open your URL in **Chrome**
2. A banner will pop up: **"Install AXA FA App"** → tap Install
3. Or tap the 3-dot menu → **"Add to Home screen"**

### Computer (Chrome/Edge):
1. Open your URL
2. Look for the install icon (📥) in the address bar → click it
3. Or the install banner will appear at the bottom
4. Click **Install**

---

## STEP 4: Test real-time sync

1. Open the app on your phone
2. Add a sale or a lead
3. Open the app on your computer
4. You should see the data appear within 1–2 seconds ✅

---

## How it works offline

- When you're offline, all changes save to your device (IndexedDB)
- The sync dot in the top right shows: 🟢 synced · 🟠 saving · ⚫ offline
- When you come back online, everything auto-syncs to Firestore
- Other devices receive the update in real time

---

## Files in this folder

| File | Purpose |
|------|---------|
| `index.html` | The full app |
| `manifest.json` | Makes it installable as an app |
| `sw.js` | Service worker — enables offline use |
| `icon-192.png` | App icon (small) |
| `icon-512.png` | App icon (large) |
| `SETUP_GUIDE.md` | This file |

---

## Free tier limits (more than enough for personal use)

- **GitHub Pages**: Free, unlimited
- **Firebase Firestore**: 1GB storage, 50,000 reads/day, 20,000 writes/day — free forever
- **Total cost: ₱0** 🎉

---

Questions? Just ask Claude!
