# Play by Play Admin - Deployment & Maintenance Guide

## Table of Contents

1. [Overview](#overview)
2. [Option 1: GitHub + Netlify Integration (Recommended)](#option-1-github--netlify-integration-recommended)
3. [Option 2: Manual Build & Upload to Netlify](#option-2-manual-build--upload-to-netlify)
4. [Environment Variables](#environment-variables)
5. [Monitoring & Logs](#monitoring--logs)
6. [Troubleshooting](#troubleshooting)

---

## Overview

**Play by Play Admin** is deployed on **Netlify**, a platform for hosting modern web applications. This guide covers:

- **Automated Deployment**: Via GitHub integration (recommended)
- **Manual Deployment**: Build locally and drag-drop to Netlify

---

## Option 1: GitHub + Netlify Integration (Recommended)

### Step 1: Push Code to GitHub

```bash
    cd /Users/sinclair/Documents/GitHub/play-by-play-admin
    git init
    git add .
    git commit -m "Initial commit"
    git remote add origin https://github.com/YOUR_USERNAME/play-by-play-admin.git
    git branch -M main
    git push -u origin main
```

### Step 2: Connect to Netlify

1. Go to [netlify.com](https://netlify.com)
2. Click **"Sign Up"** → Choose **"GitHub"**
3. Authorize Netlify to access your GitHub account

### Step 3: Import Project

1. Click **"Add New Site"** → **"Import an existing project"**
2. Select **GitHub** as your Git provider
3. Search for and select `play-by-play-admin` repository
4. Click **"Continue"**

### Step 4: Configure Build Settings

Netlify should auto-detect these. If not, set manually:

| Setting               | Value           |
| --------------------- | --------------- |
| **Build Command**     | `npm run build` |
| **Publish Directory** | `dist`          |
| **Node Version**      | 18 (or higher)  |

### Step 5: Set Environment Variables

1. In Netlify, go to **Site Settings** → **Build & Deploy** → **Environment**
2. Click **"Edit Variables"**
3. Add each Firebase variable:

```
VITE_FIREBASE_API_KEY = your_api_key
VITE_FIREBASE_AUTH_DOMAIN = your_auth_domain
VITE_FIREBASE_PROJECT_ID = your_project_id
VITE_FIREBASE_STORAGE_BUCKET = your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID = your_sender_id
VITE_FIREBASE_APP_ID = your_app_id
```

### Step 6: Deploy

1. Click **"Deploy Site"**
2. Wait for build to complete (2-3 minutes)
3. Your site is now live at `https://your-site-name.netlify.app`

### Step 7: Continuous Deployment

Every push to GitHub automatically deploys:

```bash
# Make changes
git add .
git commit -m "Update feature"
git push origin main

# Netlify automatically builds and deploys within 1-2 minutes
```

---

## Option 2: Manual Build & Upload to Netlify

### Step 1: Build Locally

```bash
  npm install
  npm run build
```

This creates a `dist/` folder with all production files.

### Step 2: Sign In to Netlify

1. Go to [netlify.com](https://netlify.com)
2. Click **"Sign In"** or **"Sign Up"**
3. Choose **GitHub** or **Email**

### Step 3: Drag & Drop Deploy

1. Go to Netlify dashboard
2. Click **"Add New Site"** → **"Deploy manually"**
3. Drag the entire `dist/` folder to the drop zone
4. Wait for upload to complete

### Step 4: Environment Variables

After upload:

1. if the .env file was in the directory, when the build was made, Netlify will have those variables baked in.
   If not, go to **Site Settings** → **Build & Deploy** → **Environment**
2. Click **"Edit Variables"**
3. Add all Firebase variables (same as Option 1, Step 5)
4. Click **"Redeploy Site"**

### Step 5: Future Deployments

```bash
    # After code changes
npm run build

# Go to Netlify dashboard
# Click "Add New Site" → "Deploy manually"
# Drag new dist/ folder
# Or use "Redeploy" button to quickly redeploy
```

---

## Environment Variables

### Finding Your Firebase Credentials

1. Go to [Firebase Console](https://console.firebase.google.com)
2. Select your project → **Settings** (gear icon)
3. Go to **General** tab → scroll down to **Your Apps**
4. Copy the Firebase config object
5. Extract individual values for each `VITE_*` variable

### Setting Variables Locally (Development)

Create `.env` file in project root:

```env
VITE_FIREBASE_API_KEY=your_key_here
VITE_FIREBASE_AUTH_DOMAIN=your_domain_here
VITE_FIREBASE_PROJECT_ID=your_project_id_here
VITE_FIREBASE_STORAGE_BUCKET=your_bucket_here
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id_here
VITE_FIREBASE_APP_ID=your_app_id_here
```

**Important**: Never commit `.env` to Git. Add to `.gitignore`:

```
.env
.env.local
.env.*.local
```

---

## Starting & Stopping

### Start Development Server

```bash
  npm install
  npm run dev
```

Access at `http://localhost:5173`

### Stop Development Server

```bash
  Press Ctrl+C
```

### Deploy to Production

```bash
  git push origin main
# Netlify automatically deploys
```

or for manual:

```bash
  npm run build
# Drag dist/ folder to Netlify dashboard
```

### Pause Deployments (temporary)

1. Netlify dashboard → **Site Settings** → **Build & Deploy**
2. Find **"Deploy Contexts"**
3. Disable automatic deployment if needed

### Delete Site

1. Netlify dashboard → **Site Settings** → **General**
2. Scroll to bottom → **Delete site**
3. Confirm with site name

---

## Monitoring & Logs

### View Deployment Status

1. Go to Netlify dashboard
2. Select your site
3. Go to **Deployments** tab
4. See all deployments with status (✓ Success, ✗ Failed)

### View Build Logs

1. In **Deployments** tab, click on a deployment
2. Click **"Deploy Log"** to see build output
3. Look for errors if build failed

### View Runtime Errors

1. Open your live site in browser
2. Press **F12** (or Cmd+Option+I on Mac) to open DevTools
3. Go to **Console** tab
4. Look for errors like:
   - `Firebase: Error (auth/invalid-api-key)`
   - `Cannot read property 'map' of undefined`
   - `Uncaught ReferenceError`

### Check Firebase Logs

1. Go to [Firebase Console](https://console.firebase.google.com)
2. Select your project
3. Go to **Authentication** tab to see login errors
4. Go to **Firestore Database** to check write/read issues

---

## Troubleshooting

### Blank Page / App Won't Load

**Symptoms:** Page loads but shows nothing

**Solution:**

1. Open browser DevTools (F12)
2. Check Console tab for errors
3. Check if environment variables are set in Netlify
4. If missing: Go to Site Settings → Environment → verify all Firebase variables
5. Trigger rebuild: Go to **Deployments** → **Trigger Deploy** → **Deploy Site**

### Firebase Authentication Fails

**Error:** `Firebase: Error (auth/invalid-api-key)`

**Solution:**

1. Go to Firebase Console → Project Settings
2. Verify API key is correct
3. Go to Firebase → Authentication → Settings
4. Add your Netlify domain to "Authorized domains":
   - `your-site-name.netlify.app`
5. Copy correct API key to Netlify environment variables
6. Trigger rebuild

### Site is Very Slow

**Solution:**

1. Check bundle size: `npm run build` and look at output
2. remove unused dependencies
3. Check network in browser DevTools (F12 → Network tab)
4. Optimize Firebase queries if data loading is slow

---

## Quick Reference Commands

```bash
# Development
npm install              # Install dependencies
npm run dev             # Start dev server
npm run build           # Create production build
npm run lint            # Check code quality

# Git/GitHub
git status              # Check changes
git add .               # Stage all files
git commit -m "msg"     # Commit changes
git push origin main    # Push to GitHub (triggers Netlify deploy)
git log --oneline       # View commit history
```

---

## Useful Links

- **Netlify Dashboard**: https://app.netlify.com
- **Firebase Console**: https://console.firebase.google.com
- **GitHub Account**: https://github.com/YOUR_USERNAME
- **Live Site**: https://your-site-name.netlify.app

---

## Support

| Issue           | Where to Check                              |
| --------------- | ------------------------------------------- |
| Build errors    | Netlify Deployments → Deploy Log            |
| Runtime errors  | Browser DevTools Console (F12)              |
| Firebase errors | Firebase Console → Authentication/Firestore |
| Git/Push errors | GitHub repository or git status             |

For more help:

- Netlify Docs: https://docs.netlify.com
- Firebase Docs: https://firebase.google.com/docs
- Vite Docs: https://vitejs.dev

---

**Last Updated**: October 2025  
**Version**: 2.0
