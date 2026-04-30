# Project Description

## Summary

Play-by-Play Admin is a web-based dashboard for Game Masters (GMs) and Ad Masters (AMs) to operate live or pre-recorded (“Legend Mode”) prediction games. It provides tools to create/manage games, manage prediction questions/templates, operate live game controls, manage ads, message players and moderate chat when enabled, review historical game data/audit logs, and export operational data for analysis.

## High-level Features

- **Game operations**: create games (including drafts), run live dashboards, and manage Legend Mode sessions.
- **Prediction content management**: build and manage templates/sets of questions (including reordering).
- **Operator efficiency**: hotkeys (including combination hotkeys) and UI affordances like checklists for live operations.
- **Observability & reporting**: game history, audit logs, search/filter, and CSV/JSON exports.
- **Messaging & moderation (when enabled)**: operator broadcasts plus player chat moderation workflows.
- **Player experience preview**: AppView emulation to reflect mobile gameplay in the dashboard.
- **AI assistance (optional)**: in-app assistant to support operator workflows when enabled/configured.

## Non-Functional Requirements

- **Performance**: Admin actions during live games should feel responsive (minimal perceived lag for common workflows).
- **Security**: Role-based access for admin users; sensitive configuration should not be committed to source control.
- **Reliability**: The dashboard should remain stable during long live sessions (avoid crashes that interrupt operations).
- **Auditability**: Administrative actions should be traceable (audit trail) for accountability and incident review.
- **Data portability**: Operators should be able to export operational datasets (CSV/JSON) for analysis and record keeping.
- **Safety for moderation**: Player chat moderation workflows should help operators identify risky content (profanity/AI flags, depending on configuration) without blocking core game operation when disabled.
- **Optional AI**: AI-assisted workflows should degrade gracefully when not configured or intentionally disabled.

## Constraints

- **Backend dependency**: The production system depends on Firebase (Auth + Firestore) and the project’s security rules/configuration.
- **Client-only exports**: CSV/JSON exports are generated from what the UI currently has loaded/filtered (not a separate server-side reporting pipeline unless explicitly added later).
- **AI provider dependency**: Optional Gemini integration uses **`VITE_GEMINI_API_KEY`** (and optionally **`VITE_GEMINI_MODEL`**) at build time; if unset, AI runs in a no-op/disabled mode.
- **Browser assumptions**: The admin experience is optimized for desktop browsers (mobile layouts are primarily previewed via AppView emulation).