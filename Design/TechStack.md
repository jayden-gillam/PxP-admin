# Tech Stack

## Frontend
- **React.js** ([React Official Website](https://react.dev/))  
  We selected React.js because it allows us to build dynamic, component-based user interfaces efficiently. Its strong ecosystem and community support make it a reliable choice for developing the web-based administrative system.  

- **TypeScript** ([TypeScript Official Website](https://www.typescriptlang.org/))  
  We selected TypeScript because it provides static type checking, which helps catch errors at compile time and improves maintainability of the codebase. It integrates well with React.js and is widely used in modern web applications.  

## Build tooling
- **Vite** ([Vite Official Website](https://vitejs.dev/))  
  Vite provides fast local development and an optimized production build pipeline for modern React/TypeScript apps.

## App routing & UI utilities
- **React Router** ([React Router](https://reactrouter.com/))  
  Used for client-side routing across admin pages and deep links into operational workflows.

## Media / livestream validation (as needed)
- **HLS.js** ([hls.js](https://github.com/video-dev/hls.js/))  
  Used to validate/preview HLS streams in-browser during game setup and operational checks.

## Optional AI (deployment-dependent)
- **Google Generative AI SDK (Gemini)** ([Google AI for Developers](https://ai.google.dev/))  
  Optional assistant (and related flows) use Gemini when `VITE_GEMINI_API_KEY` is set at build time; optional `VITE_GEMINI_MODEL` overrides the default model. If unset, the app uses a no-op client.

## Backend
- **Firebase** ([Firebase Official Website](https://firebase.google.com/))  
  We selected Firebase because it provides a fully managed backend solution, including authentication, real-time database, hosting, and cloud functions. This allows the team to focus on building features instead of managing servers, and it scales automatically with user demand.  

## Hosting / deployment (typical)
- **Netlify** ([Netlify](https://www.netlify.com/))  
  Common choice for hosting the Vite `dist/` output with CI from Git.

- **Firebase Hosting** ([Firebase Hosting](https://firebase.google.com/docs/hosting))  
  Supported by the application repo (`firebase.json` serves `dist/` with SPA rewrites); use when keeping static hosting alongside Firestore/Auth in one Firebase project.

## Quality / testing
- **Vitest** ([Vitest](https://vitest.dev/))  
  Fast unit/integration testing for services and UI logic.  
- **ESLint** ([ESLint](https://eslint.org/))  
  Static analysis for consistent TypeScript/React code quality.

## Version Control
- **GitHub** ([GitHub Official Website](https://github.com/))  
  We selected GitHub for version control and collaboration. It enables the team to manage source code effectively, track changes, and collaborate seamlessly.
