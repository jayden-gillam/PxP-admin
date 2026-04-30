# Play by Play Admin - Deployment & Maintenance Guide

## Table of Contents

1. [Overview](#overview)
2. [Firebase project (who owns what)](#firebase-project-who-owns-what)
3. [Option 1: GitHub + Netlify Integration (Recommended)](#option-1-github--netlify-integration-recommended)
4. [Option 2: Manual Build & Upload to Netlify](#option-2-manual-build--upload-to-netlify)
5. [Option 3: Firebase Hosting](#option-3-firebase-hosting)
6. [Environment Variables](#environment-variables)
7. [Monitoring & Logs](#monitoring--logs)
8. [Troubleshooting](#troubleshooting)

---

## Overview

**Play by Play Admin** is a **Vite + React** SPA backed by **Firebase Authentication + Cloud Firestore**. The static build output (`dist/`) can be hosted on **Netlify**, **Firebase Hosting**, or any static host—as long as the **Firebase web app config** is supplied at **build time** via `VITE_*` variables (they are compiled into the client bundle).

This guide is written for the **application repository** (the codebase you deploy), e.g. [play-by-play-admin](https://github.com/shristikhadka/play-by-play-admin). This `PxP-admin` repository primarily contains documentation and design artifacts; keep deployment steps aligned with whichever repo actually contains `package.json` and `vite.config.*`.

---

## Firebase project (who owns what)

- **Each environment should use its own Firebase project** (or clearly separated Firebase “sites”/projects for dev vs prod). A client or partner typically **creates their own Firebase project**, enables **Authentication** and **Firestore**, deploys **security rules** (and indexes) from the app repo or their fork, and puts the **Web app config** values into hosting **environment variables** (or a local `.env` before `npm run build`).
- **Hosting provider ≠ Firebase backend**: Netlify (or Firebase Hosting) only serves the static JS/CSS; **Auth, Firestore, and rules** still live in **their** Firebase project.
- The application repo includes **`firebase.json`** configured for **Hosting** (`public`: `dist`) and SPA rewrites, plus Firestore rules/indexes for local/emulator workflows—so **Firebase Hosting + `firebase deploy`** is a supported path, not only Netlify.

---

## Option 1: GitHub + Netlify Integration (Recommended)

### Step 1: Push code to GitHub

From your **application** repository root:

```bash
git status
git add .
git commit -m "Describe the change"
git push
```

Notes:

- Use whatever your team’s default branch is (`main`, `dev`, etc.). Netlify can deploy from a specific branch—configure that in Netlify rather than assuming `main`.

### Step 2: Connect to Netlify

1. Go to [netlify.com](https://netlify.com)
2. Sign in (commonly via **GitHub**)
3. Authorize Netlify if prompted

### Step 3: Import project

1. Click **Add new site** → **Import an existing project**
2. Select **GitHub** (or your provider)
3. Pick the admin app repository

### Step 4: Configure build settings

Netlify may auto-detect Vite. If not, set:

| Setting               | Value           |
| --------------------- | --------------- |
| **Build command**     | `npm run build` |
| **Publish directory** | `dist`          |
| **Node version**      | **20** (recommended) or **18+** (match your CI/local) |

### Step 5: Set environment variables

1. Netlify → **Site configuration** → **Environment variables** (wording varies slightly by Netlify UI version)
2. Add the Firebase variables your build expects (commonly `VITE_*`):

```text
VITE_FIREBASE_API_KEY=...
VITE_FIREBASE_AUTH_DOMAIN=...
VITE_FIREBASE_PROJECT_ID=...
VITE_FIREBASE_STORAGE_BUCKET=...
VITE_FIREBASE_MESSAGING_SENDER_ID=...
VITE_FIREBASE_APP_ID=...
VITE_FIREBASE_MEASUREMENT_ID=...   # optional, if used
```

3. If AI features are enabled for your deployment, add **Gemini** variables (see [Environment variables](#environment-variables)).

### Step 6: Deploy

1. Click **Deploy site** (first time) or rely on automatic deploys after connecting Git
2. Wait for the build to finish
3. Open the generated `*.netlify.app` URL (or your custom domain)

### Step 7: Continuous deployment

After Git integration, pushes to the configured branch typically trigger a new deploy automatically.

---

## Option 2: Manual build & upload to Netlify

Manual drag-and-drop deploys upload a **prebuilt** `dist/` folder. Environment variables are **not** magically applied to an already-built bundle unless you rebuild with those values present at build time.

### Step 1: Build locally (with env vars available)

From the **application** repository root:

```bash
npm install
npm run build
```

Ensure your local `.env` (not committed) contains the required `VITE_*` values before running `npm run build`.

### Step 2: Deploy `dist/` to Netlify

1. Netlify → **Add new site** → **Deploy manually**
2. Drag the `dist/` folder into the deploy drop zone

### Step 3: Future updates

Repeat:

```bash
npm run build
```

…and upload the new `dist/`.

---

## Option 3: Firebase Hosting

Use this when you want the static app on **Firebase Hosting** (same ecosystem as Firestore/Auth). The app repo’s `firebase.json` expects the built files in **`dist/`**.

### Prerequisites

- [Firebase CLI](https://firebase.google.com/docs/cli) (`npm install -g firebase-tools` or use `npx firebase-tools`)
- Access to the target Firebase project (owner/editor)

### Steps

1. **Create / select the Firebase project** in the Firebase Console and register a **Web app** if you have not already.
2. In the **application** repo, run `firebase login` and `firebase use <projectId>` (or `firebase init` if you are wiring the repo to a new project).
3. **Set environment variables** for the build (same `VITE_*` values as below)—locally via `.env`, or via your CI (GitHub Actions, etc.) before `npm run build`.
4. Build and deploy:

```bash
npm install
npm run build
firebase deploy --only hosting
```

5. In Firebase Console → **Authentication** → **Settings** → **Authorized domains**, add your Hosting domain (for example `your-project.web.app`, `your-project.firebaseapp.com`, and any custom domain).

**Security note (AI)**: If you set `VITE_GEMINI_API_KEY` for production, treat it as a **client-exposed** secret: restrict the key in [Google AI Studio](https://aistudio.google.com/) (e.g. HTTP referrer restrictions for your deployed origin), since it will be present in the built bundle.

---

## Environment Variables

### Finding Firebase credentials

1. Go to [Firebase Console](https://console.firebase.google.com)
2. Select your project → **Project settings**
3. Under **Your apps**, select the web app and copy config values into `VITE_*` variables

### Firebase (required for a real backend)

These are read in the app as `import.meta.env.VITE_FIREBASE_*` (see `src/contexts/config/firebaseConfig.ts` in the application repo).

| Variable | Purpose |
| -------- | ------- |
| `VITE_FIREBASE_API_KEY` | Web API key |
| `VITE_FIREBASE_AUTH_DOMAIN` | Auth domain |
| `VITE_FIREBASE_PROJECT_ID` | Project ID |
| `VITE_FIREBASE_STORAGE_BUCKET` | Storage bucket (if used) |
| `VITE_FIREBASE_MESSAGING_SENDER_ID` | Sender ID |
| `VITE_FIREBASE_APP_ID` | App ID |
| `VITE_FIREBASE_MEASUREMENT_ID` | Optional (Analytics) |

### AI — Google Gemini (optional)

If unset, the app uses a **no-op AI client** (assistant / moderation features that depend on AI stay disabled or show a configuration message).

| Variable | Required? | Purpose |
| -------- | --------- | ------- |
| `VITE_GEMINI_API_KEY` | Optional | Enables the real Gemini client when non-empty |
| `VITE_GEMINI_MODEL` | Optional | Model id; if empty, the app defaults to **`gemini-2.0-flash`** |

Source of truth in the app repo: **`.env.example`** and `src/services/ai/createAiTextClient.ts`.

### Local development

Create `.env` or `.env.local` in the **application** repo root (do not commit it). Copy from `.env.example` and add **all** Firebase keys the app needs:

```env
VITE_FIREBASE_API_KEY=your_key_here
VITE_FIREBASE_AUTH_DOMAIN=your_domain_here
VITE_FIREBASE_PROJECT_ID=your_project_id_here
VITE_FIREBASE_STORAGE_BUCKET=your_bucket_here
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id_here
VITE_FIREBASE_APP_ID=your_app_id_here
VITE_FIREBASE_MEASUREMENT_ID=your_measurement_id_here
VITE_GEMINI_API_KEY=
VITE_GEMINI_MODEL=gemini-2.0-flash
```

**Important**:

- `VITE_*` variables are bundled into client-side code at build time.
- Never commit `.env` to Git.

---

## Starting & stopping (local)

### Start development server

```bash
npm install
npm run dev
```

Vite defaults to `http://localhost:5173` unless configured otherwise.

### Stop development server

Press **Ctrl+C** in the terminal.

### Production deploy (Git-connected Netlify)

Push to the branch Netlify is configured to deploy from.

### Production deploy (Firebase Hosting)

After CI or local `npm run build`, run `firebase deploy --only hosting` from the application repo (with Firebase CLI authenticated to the correct project).

---

## Monitoring & logs

### Deployment status + build logs

**Netlify:** Netlify dashboard → your site → **Deploys** → open a deploy → **Deploy log**.

**Firebase Hosting:** Firebase Console → **Hosting** → release history; or CLI output from `firebase deploy`.

### Runtime errors

1. Open the live site
2. Open browser devtools → **Console**

Common signals:

- Missing Firebase config at build time (mis-set `VITE_*` vars)
- Auth domain not allowlisted for your **Netlify** or **Firebase Hosting** hostname

### Firebase-side checks

1. Firebase Console → **Authentication** (domain allowlisting / sign-in method issues)
2. Firebase Console → **Firestore** (rules/quota issues)

---

## Troubleshooting

### Blank page / app won’t load

1. Check browser console errors
2. Verify **build-time** environment variables for **the same build** that produced the deployed `dist/` (Netlify site env, CI secrets, or local `.env` used when you ran `npm run build`)
3. Trigger a clean rebuild/redeploy after changing env vars

### Firebase authentication fails (`auth/invalid-api-key`, etc.)

1. Verify values in Firebase project settings
2. Add your deployed hostname(s) to Firebase Auth **Authorized domains** — for example `your-site.netlify.app`, `your-project.web.app`, `your-project.firebaseapp.com`, and any custom domain

### Site feels slow

1. Check **Network** waterfall for large assets / slow endpoints
2. Review Firestore query patterns (over-fetching, missing pagination, etc.)

---

## Quick reference commands

```bash
# Local development
npm install
npm run dev

# Production build
npm run build

# Quality
npm run lint
npm test
```

---

## Useful links

- **Netlify**: https://app.netlify.com
- **Firebase Console**: https://console.firebase.google.com
- **Vite**: https://vitejs.dev

---

**Last updated**: April 2026  
**Version**: 3.1
