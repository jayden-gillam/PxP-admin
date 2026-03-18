# User Acceptance Testing (UAT) Document


This document defines acceptance tests for the core features of the Play by Play Admin application.

---

## Feature 1: User Authentication

### Description
Users can sign in to the admin dashboard using email and password credentials. Only users with admin access can access the dashboard.

### User Story
As an administrator, I want to securely log in to the admin dashboard so that I can manage games and content.

### Acceptance Tests

#### UAT-1.1: Successful login with valid admin credentials
**Preconditions:**
- User has a registered admin account
- User is on the login page

**Steps:**
1. Enter valid email address in the email field
2. Enter correct password in the password field
3. Click "Sign In" button

**Expected Result:**
- Button shows "Signing in..." while loading
- User is redirected to the home dashboard ("/")
- User session is established

#### UAT-1.2: Login validation - empty fields
**Preconditions:**
- User is on the login page

**Steps:**
1. Leave email field empty
2. Leave password field empty
3. Click "Sign In" button

**Expected Result:**
- Error message displays: "Please fill in all fields"
- User remains on login page

#### UAT-1.3: Login failure - invalid credentials
**Preconditions:**
- User is on the login page

**Steps:**
1. Enter a valid email format
2. Enter an incorrect password
3. Click "Sign In" button

**Expected Result:**
- Error message displays: "Invalid email or password. Please try again."
- User remains on login page

---

## Feature 2: Game Controls

### Description
Game Controls allow administrators to manage live game questions, including creating questions from templates, closing the play window, and sending results.

### User Story
As an administrator, I want to control the flow of questions during a live game so that players can make predictions and receive results.

### Acceptance Tests

#### UAT-2.1: View game controls with active game
**Preconditions:**
- User is logged in as an administrator
- An active game exists

**Steps:**
1. View the Game Controls section on the home page

**Expected Result:**
- Header shows "Game Controls"
- Question templates are loaded and displayed
- "+ Custom Question" button is visible
- "Resync Videos" button is visible

#### UAT-2.2: Create question from template
**Preconditions:**
- User is logged in as an administrator
- An active game exists
- Question templates are loaded

**Steps:**
1. Click the "SELECT" button on a template

**Expected Result:**
- New question is created from the template
- Template button changes to "SELECTED" (disabled)
- Success toast: "Question selected successfully!"
- Play window shows "CLOSE PLAY WINDOW" button

#### UAT-2.3: Close play window
**Preconditions:**
- User is logged in as an administrator
- A question is active (status: "active")

**Steps:**
1. Click "CLOSE PLAY WINDOW" button

**Expected Result:**
- Question status changes to "closed"
- Play window shows "PLAY WINDOW CLOSED"
- Predictions are no longer accepted

#### UAT-2.4: Send answers - success
**Preconditions:**
- User is logged in as an administrator
- A question is closed (not active)
- Answers are selected

**Steps:**
1. Click on one or more answer options to select them
2. Click "Send Answers" button

**Expected Result:**
- Answers are sent and saved
- Selected answers are cleared
- Success toast: "Answers sent successfully!"

---

## Feature 3: Legends Manager

### Description
The Legends Manager allows administrators to configure ended games for Legend mode playback. Legend mode enables players to replay historical games with time-synced questions.

### User Story
As an administrator, I want to configure timemarks on questions so that players can replay games in Legend mode with questions appearing at the correct video timestamps.

### Acceptance Tests

#### UAT-3.1: View available games
**Preconditions:**
- User is logged in as an administrator
- User navigates to Legends Manager page

**Steps:**
1. Click on the "Select Game" dropdown

**Expected Result:**
- Dropdown shows games with status "ended" (shown as "[Draft]") or "legend" (shown as "[LIVE]")
- Default option shows "-- Select a game --"

#### UAT-3.2: Select game and load questions
**Preconditions:**
- User is logged in as an administrator
- At least one game exists with status "ended" or "legend"

**Steps:**
1. Navigate to Legends Manager page
2. Select a game from the dropdown

**Expected Result:**
- Game info panel displays status badge and video URL
- All questions for the selected game are displayed
- Each question shows its text, status, and timemark

#### UAT-3.3: Auto-fill timemarks
**Preconditions:**
- User is logged in as an administrator
- A game with multiple questions is selected

**Steps:**
1. Click the "Auto-fill Timemarks" button

**Expected Result:**
- All questions receive calculated timemarks
- Success toast message: "Auto-filled timemarks for X questions"
- Questions display their new timemarks in m:ss format

#### UAT-3.4: Publish game to Legend mode
**Preconditions:**
- User is logged in as an administrator
- A game with status "ended" is selected
- At least one question has a timemark set

**Steps:**
1. Click the "Publish to Legend Mode" button

**Expected Result:**
- Game status changes to "legend"
- Status badge updates to show "PUBLISHED" (green)
- Success toast message: "Game published to Legend mode!"

---

## Test Environment Requirements

- Browser: Chrome, Firefox, Safari, or Edge (latest versions)
- User must have valid admin credentials
- Firebase backend must be accessible

## Test Data Requirements

1. **Admin user account** - For authentication testing
2. **Active game with templates** - For Game Controls testing
3. **Ended game with questions** - For Legends Manager testing

---

## Sign-off

| Tester | Date | Feature | Status | Notes |
|--------|------|---------|--------|-------|
|        |      | User Authentication |  |  |
|        |      | Game Controls |  |  |
|        |      | Legends Manager |  |  |
