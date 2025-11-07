# Play by Play Admin - Development Guide

## Table of Contents

1. [Overview](#overview)
2. [Technology Stack](#technology-stack)
3. [Prerequisites](#prerequisites)
4. [Environment Setup](#environment-setup)
5. [Project Structure](#project-structure)
6. [Configuration Files](#configuration-files)
7. [Running the Application](#running-the-application)
8. [Replicating via Docker](#replicating-via-docker)
9. [Testing Guide](#testing-guide)
10. [Troubleshooting](#troubleshooting)

---

## Overview

**Play by Play Admin** is a React-based admin dashboard application designed for managing game sessions with real-time communication. The application provides authenticated users with a comprehensive interface for game control, message handling, and app state management.

---

## Technology Stack

### Core Technologies

| Technology       | Version | Purpose                                          |
| ---------------- | ------- | ------------------------------------------------ |
| **React**        | ^19.1.1 | UI framework for building interactive components |
| **TypeScript**   | ~5.9.3  | Type-safe JavaScript development                 |
| **Vite**         | ^7.1.7  | Fast build tool and development server           |
| **React Router** | ^7.9.4  | Client-side routing and navigation               |
| **Firebase**     | ^12.4.0 | Authentication and backend services              |

### Development Tools

| Tool                     | Version               | Purpose                         |
| ------------------------ | --------------------- | ------------------------------- |
| **ESLint**               | ^9.36.0               | Code linting and quality checks |
| **@vitejs/plugin-react** | ^5.0.4                | React plugin for Vite           |
| **TypeScript ESLint**    | ^8.45.0               | TypeScript-specific linting     |
| **Node.js**              | 16+ (recommended 18+) | JavaScript runtime              |

---

## Prerequisites

Before setting up your development environment, ensure you have the following installed:

### Required Software

1. **Node.js** (version 16 or higher, recommended 18+)
   - Download from [nodejs.org](https://nodejs.org)
   - Verify installation: `node --version` and `npm --version`

2. **Git**
   - Download from [git-scm.com](https://git-scm.com)
   - Verify installation: `git --version`

3. **Code Editor** (recommended)
   - VS Code ([download](https://code.visualstudio.com))
   - WebStorm ([download](https://www.jetbrains.com/webstorm/))
   - Or any modern code editor supporting TypeScript

### IDE Extensions (VS Code)

For optimal development experience with VS Code, install:

- **ES7+ React/Redux/React-Native snippets** (dsznajder.es7-react-js-snippets)
- **TypeScript Vue Plugin** (Vue.volar)
- **ESLint** (dbaeumer.vscode-eslint)
- **Prettier - Code formatter** (esbenp.prettier-vscode)

---

## Environment Setup

### Step 1: Clone the Repository

```bash
  git clone https://github.com/shristikhadka/play-by-play-admin.git
  cd play-by-play-admin
```

### Step 2: Install Dependencies

```bash
  npm install
```

This command installs all dependencies listed in `package.json` into the `node_modules` directory.

**Expected Output:**

```
added 500+ packages in 45s
```

### Step 3: Environment Configuration

Create a `.env` file in the root directory:

```bash
  touch .env
```

Add the following variables (replace placeholders with actual values):

```env
VITE_FIREBASE_API_KEY=your_firebase_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

**Note**: Environment variables prefixed with `VITE_` are exposed to the client-side code.

### Step 4: Verify Installation

```bash
  npm run lint
```

This command checks your code for linting errors and ensures TypeScript compilation is successful.

---

## Project Structure

### Directory Organization

```
play-by-play-admin/
├── src/
│   ├── assets/                    # Static assets (images, SVGs)
│   │   ├── logo.svg
│   │   └── react.svg
│   │
│   ├── components/                # Reusable React components
│   │   ├── app-view/              # Left panel - Application display
│   │   │   ├── AppView.tsx
│   │   │   └── AppView.css
│   │   │
│   │   ├── game-controls/         # Middle panel - Game state management
│   │   │   ├── GameControls.tsx
│   │   │   ├── GameControls.css
│   │   │   ├── GameControlsMock.tsx
│   │   │   ├── types.ts
│   │   │   └── components/
│   │   │       ├── AnswerSelector.tsx
│   │   │       ├── PlayWindowControl.tsx
│   │   │       └── QuestionTypeButtons.tsx
│   │   │
│   │   ├── message-controls/      # Right panel - Messaging interface
│   │   │   ├── MessageControls.tsx
│   │   │   └── MessageControls.css
│   │   │
│   │   ├── create-game/           # Modal - Create new game
│   │   │   ├── CreateGameModal.tsx
│   │   │   └── CreateGameModal.css
│   │   │
│   │   └── protected-route/       # Auth guard component
│   │       └── ProtectedRoute.tsx
│   │
│   ├── contexts/                  # React Context providers
│   │   └── AuthContext.tsx        # Authentication state management
│   │
│   ├── hooks/                     # Custom React hooks
│   │   └── useAuth.ts             # Hook to consume AuthContext
│   │
│   ├── pages/                     # Page-level components (routed)
│   │   ├── login/                 # Authentication page
│   │   │   ├── Login.tsx
│   │   │   └── Login.css
│   │   │
│   │   ├── home/                  # Home page (post-login)
│   │   │   ├── Home.tsx
│   │   │   └── Home.css
│   │   │
│   │   └── dashboard/             # Main application interface
│   │       ├── Dashboard.tsx
│   │       └── Dashboard.css
│   │
│   ├── config/                    # Configuration files
│   │   └── firebaseConfig.ts      # Firebase initialization
│   │
│   ├── types/                     # TypeScript type definitions
│   │   ├── index.ts
│   │   ├── context.ts
│   │   ├── game.ts
│   │   ├── question.ts
│   │   └── user.ts
│   │
│   ├── App.tsx                    # Root component with routing
│   ├── App.css                    # App-level styles
│   ├── main.tsx                   # React entry point
│   ├── index.css                  # Global styles
│   │
├── public/                        # Public assets
│   └── vite.svg
│
├── eslint.config.js               # ESLint configuration
├── vite.config.ts                 # Vite configuration
├── tsconfig.json                  # TypeScript root config
├── tsconfig.app.json              # TypeScript app config
├── tsconfig.node.json             # TypeScript node config
├── package.json                   # Dependencies and scripts
├── package-lock.json              # Locked dependency versions
├── README.md                      # Project overview
├── SETUP.md                       # Quick setup guide
└── Development.md                 # This file
```

### Key Directories Explained

#### `/src/components`

Contains all reusable React components. Follows a modular structure where each component has:

- `.tsx` file (component logic)
- `.css` file (component styles)
- Optional `types.ts` (component-specific types)
- `components/` subfolder (nested components)

#### `/src/pages`

Top-level routed pages. These are rendered by React Router based on the URL path.

#### `/src/contexts`

Global state management using React Context API. Currently houses `AuthContext` for authentication state.

#### `/src/config`

Configuration files for external services (Firebase, APIs, etc.).

#### `/src/types`

Centralized TypeScript type definitions to maintain consistency across the app.

---

## Configuration Files

### `vite.config.ts`

Vite build and development server configuration:

```typescript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
});
```

**What it does:**

- Enables React plugin for JSX transformation
- Configures hot module replacement (HMR)
- Sets up build optimization

### `tsconfig.json`

Root TypeScript configuration that references app and node configs:

```json
{
  "files": [],
  "references": [
    { "path": "./tsconfig.app.json" },
    { "path": "./tsconfig.node.json" }
  ]
}
```

### `tsconfig.app.json`

Application-specific TypeScript settings:

- Target ES2020 for modern JavaScript features
- Enables JSX support
- Configures module resolution
- Sets strict type checking

### `eslint.config.js`

ESLint configuration for code quality:

- React hooks linting rules
- React refresh compatibility
- TypeScript support

---

## Running the Application

### Development Server

Start the development server with hot module replacement:

```bash
  npm run dev
```

**Expected Output:**

```
  VITE v7.1.7  ready in 234 ms

  ➜  Local:   http://localhost:5173/
  ➜  press h to show help
```

Access the application at `http://localhost:5173/`

---

## Replicating via Docker

The repository includes a Docker workflow that mirrors the local development setup. Use it when you want to avoid installing Node.js locally or to verify onboarding steps from a clean slate.

### Prerequisites

- The repository cloned locally (as described in [Environment Setup](#environment-setup))
- Docker Desktop (or any Docker Engine) installed and running
  - macOS (Homebrew):
  ```bash
  brew install --cask docker
  open /Applications/Docker.app
  ```
    - Or download from https://www.docker.com/get-started
    - You can follow the instructions if you are stuck at some point. 
      - Windows: https://docs.docker.com/docker-for-windows/install/
      - Mac: https://docs.docker.com/docker-for-mac/install/


- `docker compose` (recommended): bundled with modern Docker Desktop releases. To install the standalone Compose plugin via Homebrew (if needed):
  ```bash
  brew install docker-compose
    ```
- A populated `.env` file at the project root containing the required `VITE_*` Firebase variables (same as the non-Docker setup)

> **Important:** The compose file reads environment variables from your host machine at runtime. Ensure they are exported in your shell session or stored in a `.env` file that Docker can consume.

### Quick Start (docker compose)

```bash

# Build the image and start the dev server with hot reload
docker compose up --build

# Shut everything down when finished
docker compose down
```

When the container is running, open `http://localhost:5173` in your browser. Source code changes under the project directory trigger Vite's HMR thanks to the bind mount defined in `docker-compose.yml`.

---

## Testing Guide

### Authentication Flow Testing

#### Test Case 1: Login with Valid Credentials

1. Start the development server: `npm run dev`
2. Navigate to `http://localhost:5173/login`
3. Enter any email and password
4. Click "Login"

**Expected Result:**

- ✅ Credentials are stored in firebase
- ✅ Redirected to `/` (home page)
- ✅ User info displays in header

#### Test Case 2: Logout

1. While logged in, click the "Logout" button
2. Try navigating to `/dashboard`

**Expected Result:**

- ✅ User has been logged out
- ✅ Redirected to login page

### Component Testing

#### Test Case 3: Create Game Modal

1. On home page, click "+ Create Game"
2. Fill in game details
3. Click "Create"

**Expected Result:**

- ✅ Modal closes
- ✅ Redirected to `/dashboard`
- ✅ Game controls initialize

#### Test Case 4: Navigation

1. From home page, click "Dashboard" in navigation
2. From dashboard, click "Home" in navigation

**Expected Result:**

- ✅ Smooth page transitions
- ✅ No errors in console
- ✅ Layout renders correctly

### Browser DevTools Testing

#### Console Inspection

1. Open DevTools: `F12` (Windows/Linux) or `Cmd+Option+I` (macOS)
2. Go to "Console" tab
3. Check for errors or warnings

**Healthy Console Output:**

```
[No errors]
```

#### Network Tab

1. Open DevTools → "Network" tab
2. Perform an action (login, create game)
3. Check request/response status

**Expected Status Codes:**

- `200`: Successful requests
- `401`: Unauthorized (expected on login redirect)

**Example Failure:**

```
TypeError: Cannot read property 'map' of undefined
  at AppView.tsx:45
```

**Action**: Check if data is properly loaded before rendering.

---

## Troubleshooting

### Common Issues and Solutions

#### Issue 1: Port 5173 Already in Use

**Error:**

```
Error: listen EADDRINUSE: address already in use :::5173
```

**Solution:**

```bash

# use a different port
npm run dev -- --port 5174
```

#### Issue 2: Firebase Configuration Error

**Error:**

```
Failed to initialize Firebase: Missing API key or
Uncaught FirebaseError: Firebase: Error (auth/invalid-api-key).
```

**Solution:**

1. Verify `.env` file exists in root directory
2. Check all Firebase credentials are correctly set
3. Restart development server to reload environment variables

#### Issue 3: Dependencies Installation Failed

**Error:**

```
npm ERR! code E404
npm ERR! 404 Not Found
```

**Solution:**

```bash
#   Clear npm cache
    npm cache clean --force

    # Delete node_modules and reinstall
    rm -rf node_modules package-lock.json
    npm install
```

---

**Last Updated**: October 2025
**Maintainers**: [PxP Team]
