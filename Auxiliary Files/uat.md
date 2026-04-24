# User Acceptance Testing (UAT) — Play by Play Admin

This document defines **four core features**, acceptance criteria, and traceability to automated tests in `uat/*.test.tsx`.

## How to run UAT-linked tests

```bash
npx vitest run uat
```

---

## Feature 1: User authentication (login)

**Specification:** An administrator can sign in with email and password. Invalid or incomplete input shows clear errors; successful sign-in establishes a session and navigates to the home route.

**User story:** As an administrator, I want to sign in securely so I can manage games and content.

| ID         | Scenario                       | Preconditions | Steps (summary)                        | Expected result                                                        |
| ---------- | ------------------------------ | ------------- | -------------------------------------- | ---------------------------------------------------------------------- |
| UAT-AUTH-1 | Successful login               | On `/login`   | Enter valid email/password → Sign In   | Loading state; `emailSignInService` + `login` called; navigate to `/`  |
| UAT-AUTH-2 | Validation — empty fields      | On `/login`   | Submit with empty fields               | Message: `Please fill in all fields`; stay on login                    |
| UAT-AUTH-3 | Invalid credentials (Firebase) | On `/login`   | Submit with credentials that fail auth | Message: `Invalid email or password. Please try again.`; stay on login |

**Automated tests:** `uat/uat-authentication.test.tsx`

---

## Feature 2: Game controls (live game)

**Specification:** With an **active game**, Game Controls loads question templates, shows template actions and play-window controls, and allows **Resync Videos** to bump the game’s refresh sequence for clients.

**User story:** As an administrator, I want to run questions during a live game so players can predict and see results.

| ID       | Scenario                          | Preconditions                  | Steps (summary)                | Expected result                                                                                            |
| -------- | --------------------------------- | ------------------------------ | ------------------------------ | ---------------------------------------------------------------------------------------------------------- |
| UAT-GC-1 | Controls visible with active game | Logged-in context; active game | Render Game Controls with game | Header `Game Controls`; template `SELECT`; `Resync Videos`; `+ Custom Question`; templates loaded          |
| UAT-GC-2 | Resync Videos                     | Active game                    | Click **Resync Videos**        | `updateGameService` called with incremented `refreshSequence`; feedback toast text includes resync success |
| UAT-GC-3 | Create question from template     | Active game; templates loaded  | Click **SELECT** on a template | `createQuestionFromTemplateService` called; success toast for question selected                            |

**Automated tests:** `uat/uat-game-controls.test.tsx`

---

## Feature 3: Template Builder

**Specification:** Administrators can open the Template Builder, see template sets derived from loaded templates, open **+ Create Set** to add a set, and navigate into a set to edit questions on the set dashboard route.

**User story:** As an administrator, I want to manage reusable question template sets so live games can use them.

| ID       | Scenario                 | Preconditions                       | Steps (summary)                 | Expected result                                             |
| -------- | ------------------------ | ----------------------------------- | ------------------------------- | ----------------------------------------------------------- |
| UAT-TB-1 | View sets from templates | Logged in; templates in API context | Open Template Builder           | Sidebar tab; set names and question counts visible          |
| UAT-TB-2 | Create set via modal     | On Template Builder                 | **+ Create Set** → submit modal | `createQuestionTemplateService` called; templates refreshed |
| UAT-TB-3 | Open set dashboard       | At least one set                    | Click a set card                | Navigate to `/template-builder/:setName`                    |

**Automated tests:** `uat/uat-template-builder.test.tsx`

---

## Feature 4: Game History

**Specification:** Administrators can open **Game History** to see ended games with question and player counts, filter or search the list, and open a game to view its detail route.

**User story:** As an administrator, I want to review past games and drill into a specific game so I can inspect outcomes and stats.

| ID       | Scenario                     | Preconditions                                      | Steps (summary)                                | Expected result                                                                                                                                |
| -------- | ---------------------------- | -------------------------------------------------- | ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| UAT-GH-1 | View list of completed games | Logged in; `gameHistory` loaded with ≥1 ended game | Open Game History page                         | Heading **Game History**; **Past Games** section; game card shows name, Questions/Players counts, **Ended** date; **Showing _n_ of _n_ games** |
| UAT-GH-2 | Open game detail             | Same as UAT-GH-1                                   | Click a game card                              | Navigate to `/game-history/{gameId}`                                                                                                           |
| UAT-GH-3 | Search filters games by name | Multiple games in history                          | Type a substring into **Search games by name** | Only games whose names contain the query remain visible                                                                                        |

**Automated tests:** `uat/uat-game-history.test.tsx`

---

## Sign-off

| Tester        | Date      | Feature             | Status | Notes |
| ------------- | --------- | ------------------- | ------ | ----- |
| Liam          | 3/17/2026 | User Authentication | T      |       |
| Sinclair      | 4/24/2026 | Game Controls       | T      |       |
| Shristi       | 3/17/2026 | Game History        | T      |       |
| Drew / Jayden | 3/17/2026 | Template Builder    | T      |       |
