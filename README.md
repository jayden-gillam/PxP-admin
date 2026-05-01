# Play-by-Play Admin

**Source code (admin app):** [github.com/shristikhadka/play-by-play-admin](https://github.com/shristikhadka/play-by-play-admin)

This repository (**PxP-admin**) holds **documentation and design artifacts** for the Play-by-Play Admin dashboard. The admin web app is built from the repository above. See also [Links to source repositories](#links-to-source-repositories).

## Features (product)

The admin dashboard supports operators and admins in running prediction games end-to-end, including:

- **Games**: Create and manage live or Legend Mode sessions; save **drafts** and resume setup later.
- **Predictions**: Template Builder, question sets, **reordering** questions/plays, presets, marking correct answers.
- **Live operations**: Dashboard controls, configurable **hotkeys** (including combinations), **AppView** player UI preview, game notes checklist.
- **Players & messaging**: Broadcasts and **player chat moderation** when enabled.
- **History & compliance**: Game History with search/filter; **audit logs**; **CSV/JSON exports** where supported.
- **Optional AI**: In-app assistant and related flows when **Gemini** is configured (`VITE_GEMINI_*` in the app repo).

For detailed walkthroughs, see [`Documentation/User.md`](Documentation/User.md).

## Tech stack (application)

The admin application ([play-by-play-admin](https://github.com/shristikhadka/play-by-play-admin)) is built with:

| Area | Technologies |
| ---- | -------------- |
| UI | React, TypeScript, Vite |
| Routing | React Router |
| Backend | Firebase Authentication, Cloud Firestore |
| Media | HLS.js (stream validation / preview) |
| Quality | Vitest, ESLint |
| Hosting (typical) | Netlify and/or Firebase Hosting; static `dist/` output |

Design-level stack notes: [`Design/TechStack.md`](Design/TechStack.md).

## Setup (this documentation repository)

There is **no app runtime** in this repo—only Markdown and related assets.

```bash
git clone https://github.com/jayden-gillam/PxP-admin.git
cd PxP-admin
```

Browse [`Documentation/README.md`](Documentation/README.md) for the doc index, or open [`Documentation/User.md`](Documentation/User.md) / [`Documentation/Development.md`](Documentation/Development.md) directly.

## Setup (admin application source)

Clone the app repo, install dependencies, add environment variables, and run locally:

```bash
git clone https://github.com/shristikhadka/play-by-play-admin.git
cd play-by-play-admin
npm install
# Copy .env.example → .env and set VITE_FIREBASE_* (and optional VITE_GEMINI_*)
npm run dev
```

Full steps (Firebase, AI, tests, emulators): [`Documentation/Development.md`](Documentation/Development.md).  
Deploy / env overview: [`Documentation/Deployment.md`](Documentation/Deployment.md).

## Links to source repositories

| Repository | Role |
| ---------- | ---- |
| [**PxP-admin**](https://github.com/jayden-gillam/PxP-admin) | This repo: documentation, design docs, meeting notes, and project materials. |
| [**play-by-play-admin**](https://github.com/shristikhadka/play-by-play-admin) | Admin dashboard **source code** (React/Vite app; primary branch may be `dev` or `main`—check the repo). |

## Documentation quick links

- [Project description](ProjectDescription.md)
- [Documentation hub](Documentation/README.md)
- [Design documents](Design/README.md)
- [Team meeting minutes](MeetingMinutes/Team)
- [Mentor meeting minutes](MeetingMinutes/Mentor)
- [Client partner meeting minutes](MeetingMinutes/ClientPartner)

## Team members

- Jayden Gillam
- Liam Grube
- Shristi Khadka
- Sinclair Nzenwata
- Drew Scott

## Client partner

- **Company:** Play-by-Play  
- **Contacts:** Matt Foss, Abeeb Visram

## Project management

https://github.com/users/jayden-gillam/projects/4
