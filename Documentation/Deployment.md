# Play by Play Admin - Deployment & Maintenance Guide

## Table of Contents

1. [Overview](#overview)
2. [Netlify (Git-connected)](#netlify-git-connected)
3. [Firebase Hosting](#firebase-hosting)
4. [Environment variables](#environment-variables)
5. [Monitoring & logs](#monitoring--logs)
6. [Troubleshooting](#troubleshooting)
7. [Quick reference](#quick-reference)

---

## Overview

The admin app is a **Vite + React** SPA that talks to **Firebase Authentication + Cloud Firestore**. You run **`npm run build`** to produce **`dist/`**; that folder is what gets hosted (static files).

**Firebase project:** Use a **dedicated Firebase project per environment** (e.g. dev vs prod). A client normally creates **their** project, enables Auth + Firestore, deploys **rules/indexes**, and copies the **Web app config** into **`VITE_FIREBASE_*`** variables at **build time** (Netlify env, CI secrets, or local `.env` before `npm run build`).

**Hosting vs backend:** Netlify or Firebase Hosting only serves the built JS/CSS. **Auth, Firestore, and security rules** always live in the Firebase project you configured—not on the static host.

This guide targets the **application** repo (e.g. [play-by-play-admin](https://github.com/shristikhadka/play-by-play-admin)). This `PxP-admin` folder is mostly docs.

---

## Netlify (Git-connected)

1. Connect the repo in Netlify and pick the deploy branch (`main`, `dev`, etc.).
2. Build settings (if not auto-detected): **Build command** `npm run build`, **Publish directory** `dist`, **Node** 20 (or 18+ to match your team).
3. **Site → Environment variables:** set all required `VITE_FIREBASE_*` (and optional Gemini — see [Environment variables](#environment-variables)).
4. Deploy; future pushes to that branch rebuild automatically.

**Manual Netlify upload:** If you drag-and-drop `dist/` instead of Git builds, variables are **not** injected after the fact—you must run `npm run build` locally (or in CI) **with** `.env` / env vars already set, then upload the new `dist/`.

---

## Firebase Hosting

The app repo includes **`firebase.json`** (hosting `public: dist`, SPA rewrites). From the app repo, with [Firebase CLI](https://firebase.google.com/docs/cli) logged in and `firebase use <projectId>`:

```bash
npm install
npm run build
firebase deploy --only hosting
```

Add your Hosting domains under Firebase **Authentication → Settings → Authorized domains** (e.g. `your-project.web.app`, custom domain).

If you use **`VITE_GEMINI_API_KEY`**, restrict that key for your deployed origin (e.g. in Google AI Studio)—it is bundled into the client.

---

## Environment variables

### Firebase (required for a real backend)

From Firebase Console → Project settings → Your web app → config values:

| Variable | Purpose |
| -------- | ------- |
| `VITE_FIREBASE_API_KEY` | Web API key |
| `VITE_FIREBASE_AUTH_DOMAIN` | Auth domain |
| `VITE_FIREBASE_PROJECT_ID` | Project ID |
| `VITE_FIREBASE_STORAGE_BUCKET` | Storage bucket |
| `VITE_FIREBASE_MESSAGING_SENDER_ID` | Sender ID |
| `VITE_FIREBASE_APP_ID` | App ID |
| `VITE_FIREBASE_MEASUREMENT_ID` | Optional (Analytics) |

Used in code as `import.meta.env.VITE_FIREBASE_*` (see `src/contexts/config/firebaseConfig.ts` in the app repo).

### AI — Google Gemini (optional)

| Variable | Purpose |
| -------- | ------- |
| `VITE_GEMINI_API_KEY` | If set (non-empty), enables Gemini; otherwise the app uses a no-op client. |
| `VITE_GEMINI_MODEL` | Optional; if empty, defaults to **`gemini-2.0-flash`**. |

See the app repo **`.env.example`** and `src/services/ai/createAiTextClient.ts`.

### Example `.env` (local / reference)

```env
VITE_FIREBASE_API_KEY=...
VITE_FIREBASE_AUTH_DOMAIN=...
VITE_FIREBASE_PROJECT_ID=...
VITE_FIREBASE_STORAGE_BUCKET=...
VITE_FIREBASE_MESSAGING_SENDER_ID=...
VITE_FIREBASE_APP_ID=...
VITE_FIREBASE_MEASUREMENT_ID=...

VITE_GEMINI_API_KEY=
VITE_GEMINI_MODEL=gemini-2.0-flash
```

`VITE_*` values are embedded in the client bundle at build time—never commit real `.env` files.

---

## Monitoring & logs

- **Netlify:** Site → **Deploys** → deploy log.
- **Firebase Hosting:** Console → **Hosting** or CLI output from `firebase deploy`.
- **Runtime:** Browser DevTools → **Console**; Firebase Console → **Authentication** / **Firestore** for backend-side issues.

---

## Troubleshooting

### Blank page / app won’t load

1. Browser console errors.
2. Confirm **`VITE_FIREBASE_*`** were present for the **same** `npm run build` that produced this `dist/`.
3. Redeploy after changing env vars.

### Auth errors / `invalid-api-key`

1. Check Firebase web app config values.
2. Add your live hostname(s) under Auth **Authorized domains** (Netlify `*.netlify.app`, Firebase `*.web.app` / `*.firebaseapp.com`, custom domain).

### Slow loads

Check Network tab and Firestore usage (over-fetching, missing pagination).

---

## Quick reference

```bash
npm install
npm run build
firebase deploy --only hosting   # if using Firebase Hosting
```

Local dev: see `Documentation/Development.md`.

---

## Useful links

- [Netlify](https://app.netlify.com)
- [Firebase Console](https://console.firebase.google.com)
- [Vite](https://vitejs.dev)

---

**Last updated**: April 2026  
**Version**: 3.2
