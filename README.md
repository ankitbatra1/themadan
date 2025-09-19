# MADAN Solutions — Static Site (HTML/CSS/JS) + Firebase Backend

This is a lightweight, multi-page static website for MADAN Solutions with a Firebase-backed contact form.

## Pages
- Home (`index.html`)
- R&D and Innovations (`rnd.html`)
- Startup Launchpad (`launchpad.html`)
- About (`about.html`)
- Contact (`contact.html`)

## Getting Started
1) Place your logo at `assets/logo.png` (PNG or SVG recommended).
2) Add a hero/arm image at `assets/madan-arm.jpg` (optional placeholder).

## Firebase Setup (Firestore)
1) Create a Firebase project at https://console.firebase.google.com
2) Add a Web app and copy the config object.
3) Open `firebase-config.js` and replace the placeholder keys:
```js
window.FIREBASE_CONFIG = {
  apiKey: "...",
  authDomain: "<PROJECT_ID>.firebaseapp.com",
  projectId: "<PROJECT_ID>",
  storageBucket: "<PROJECT_ID>.appspot.com",
  messagingSenderId: "...",
  appId: "..."
};
```
4) In Firebase Console → Firestore Database → Create database (Start in production mode). For a quick test, you can allow public writes, but for production, secure rules to allow writes only from your site with App Check and custom auth.

### Firestore Collection
- `contact_messages`: stores form submissions from `contact.html` with fields: `name`, `email`, `subject`, `message`, `createdAt`, `source`.

## Local Preview
Open any page directly in a browser, or serve with a static server.

On Windows (PowerShell):
```powershell
Start-Process http://localhost:5500/index.html; npx --yes http-server -p 5500 | cat
```

Or just double-click `index.html` to open.

## Deployment
You can host on Firebase Hosting, GitHub Pages, Netlify, or any static host.

### Firebase Hosting (optional)
```bash
npm i -g firebase-tools
firebase login --no-localhost
firebase init hosting
# Select your project, choose "dist?" → use current directory, set as single-page app? → No
firebase deploy
```

## Customization
- Update texts inside each HTML file as needed.
- Extend styles in `styles.css`.
- Add more images under `assets/`.

## Notes
- The contact form relies on Firestore via Firebase CDN modules; no bundler required.
- Consider enabling reCAPTCHA/App Check for abuse protection in production.



