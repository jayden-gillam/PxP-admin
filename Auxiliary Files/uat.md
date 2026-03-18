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

## Feature 4: Template Builder

### Description
The Template Builder allows administrators to create, edit, and manage reusable question templates for use in live games.

### User Story
As an administrator, I want to create and manage reusable question templates so that I can use different templates for a live game.

### Acceptance Tests

#### UAT-4.1: View Template Builder page
**Preconditions:**
- User is logged in

**Steps:**
1. Navigate to the Template Builder page  

**Expected Result:**
- Template Builder page loads successfully  
- Existing templates are displayed  
- "+ Create Set" button is visible  

#### UAT-4.2: Create a new template
**Preconditions:**
- User is on the Template Builder page  

**Steps:**
1. Click "+ New Set"
2. Enter Set Name
3. Click Next
4. Enter question text  
5. Enter answer options  
6. Click "Create Question"  

**Expected Result:**
- Template is saved successfully  
- Template appears in the list  

#### UAT-4.3: Validation - missing required fields
**Preconditions:**
- User is on the Template Builder page  

**Steps:**
1. Click "+ New Set"  
2. Leave required fields empty  
3. Click "Next"  

**Expected Result:** 
- The User isn't moved on  
- User remains on form  

#### UAT-4.4: Edit an existing template 
**Preconditions:**
- At least one template exists  

**Steps:** 
1. Select a template  
2. Click Edit next to a question
3. Modify the text  
4. Click "Save"  

**Expected Result:** 
- Changes are saved  
- Updated template is displayed   

#### UAT-4.5: Delete a template 
**Preconditions:**
- At least one template exists  

**Steps:** 
1. Select a template  
2. Click "Delete Set"  
3. Confirm deletion  

**Expected Result:** 
- Template is removed   

#### UAT-4.6: Template availability in Game Controls 
**Preconditions:** 
- Templates exist  
- Active game exists  

**Steps:** 
1. Navigate to Game Controls  

**Expected Result:** 
- Templates appear in Game Controls  
- Templates can be selected to create questions

#### UAT-4.7: Rename a template set
**Preconditions:**
- At least one template set exists  

**Steps:**
1. Select a template set  
2. Click on the "rename" button
3. Enter a new set name  
4. Click "Save"

**Expected Result:**
- Set name is updated successfully  
- New name is displayed in the Template Builder list  

---

#### UAT-4.8: Validation - rename set with empty name
**Preconditions:**
- At least one template set exists  

**Steps:**
1. Select a template set  
2. Attempt to rename the set with an empty value  
3. Click "Save"  

**Expected Result:**
- Rename is not allowed  
- Set name remains unchanged  
- User stays in edit mode or receives validation feedback  

---

#### UAT-4.9: Delete a question from a template set
**Preconditions:**
- At least one template set exists  
- Template set contains at least one question  

**Steps:**
1. Select a template set  
2. Locate a question  
3. Click "Delete" next to the question  
4. Confirm deletion  

**Expected Result:**
- Question is removed from the set  
- Remaining questions are still displayed correctly  

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
|Liam    |3/17/2026| User Authentication | T |  |
|        ||        |             |   |
|Shristi |3/17/2026| Legends Manager | T |  |
|Drew |3/17/2026| Template Builder | T |  |
