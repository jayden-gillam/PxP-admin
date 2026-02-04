# Play by Play Admin - User Manual

## Table of Contents

1. [Getting Started](#getting-started)
2. [Logging In](#logging-in)
3. [Registering a New Account](#registering-a-new-account)
4. [Home Page Overview](#home-page-overview)
5. [Creating a Game](#creating-a-game)
6. [Dashboard Overview](#dashboard-overview)
7. [Game Controls](#game-controls)
8. [Messaging](#messaging)
9. [Achievement Badges](#achievement-badges)
10. [Template Builder](#template-builder)
11. [Game History](#game-history)
12. [Audit Logs](#audit-logs)
13. [Keyboard Hotkeys](#keyboard-hotkeys)
14. [Ending a Game](#ending-a-game)
15. [FAQ](#faq)

---

## Getting Started

### System Requirements

Before using Play by Play Admin, ensure you have:

- **Web Browser**: Latest version of Chrome, Firefox, Safari, or Edge
- **Internet Connection**: Stable connection for real-time features
- **Device**: Desktop, tablet, or laptop (mobile not recommended for best experience)

### Accessing the Application

1. Open your web browser
2. Navigate to the application URL provided by your administrator
3. You should see the **Login Screen**

> **Note**: If you don't have login credentials, contact your administrator or the PxP team.

---

## Logging In

### Step 1: Enter Your Credentials

![Login Page](images/login.png)

1. On the login screen, enter your **Email Address** in the first field
2. Enter your **Password** in the second field
3. Click the **"Sign In"** button

### Step 2: After Successful Login

![Successful Login](images/home.png)

- You will be automatically redirected to the **Home Page**
- Your email will appear in the top-right corner of the screen
- You are now ready to create and manage games

### Troubleshooting Login

| Issue                                                         | Solution                                  |
| ------------------------------------------------------------- | ----------------------------------------- |
| "Invalid credentials" error                                   | Check your email and password are correct |
| "Cannot connect to server"                                    | Check your internet connection            |
| Page keeps redirecting to login                               | Clear your browser cache and try again    |
| Access denied. Only administrators can access this dashboard. | You don't have admin access to the system |

---

## Registering a New Account

### Overview

If you don't have an account yet, you can register for a new admin account directly from the login page.

### Step 1: Fill in Registration Details

![Register Page](images/register.png)

The registration form requires the following information:

#### Field 1: Email Address
#### Field 2: Password
#### Field 3: Confirm Password

### Step 2: Submit Registration

1. Review all information to ensure it's correct
2. Click the **"Register"** button
3. If successful, you will be redirected to the login page
4. Log in with your new credentials

### After Registration

- Your account is immediately active
- You can log in using your email and password
- You have full admin access to create and manage games

### Troubleshooting Registration

| Issue                          | Solution                                    |
| ------------------------------ | ------------------------------------------- |
| "Email already in use"         | This email is already registered. Use login instead |
| "Passwords do not match"       | Ensure both password fields are identical   |
| "Password too weak"            | Use a stronger password (6+ characters)    |
| "Invalid email format"         | Check that your email address is valid      |
| Registration button disabled   | Ensure all fields are filled correctly      |

---


## Home Page Overview

### Page Layout

![Home Page Layout](images/home-page.png)

The Home Page consists of three main sections:

#### Top Navigation Bar

- **Logo**: Click to return to home from any page
- **User Menu**: Displays your email and logout option
- **Logout Button**: Click to safely exit the application

#### Main Content Area

- **Welcome Message**: "Welcome, [Your Name]"
- **Create Game Button**: Large blue button labeled "+ Create Game"
- **Active Games Section**: Shows games you're currently running

#### Current Game Card

- **Game Name**: Name of your active game
- **Status**: Shows if the game is currently active
- **Quick Actions**: Options to view or manage the game

#### Scheduled Games Section

- **Scheduled Games List**: Shows all games scheduled for future dates
- **Game Cards**: Each scheduled game displays:
    - Game name
    - Scheduled date and time
    - Action buttons (Edit, Delete, Start Game Now)
- **Empty State**: Shows when no games are scheduled

### Key Features on Home Page

| Feature                | Description                         |
| ---------------------- | ----------------------------------- |
| Create Game            | Start a new game session            |
| Schedule Game          | Create a game for a future date/time |
| View Active Games      | See all games currently in progress |
| Manage Scheduled Games | Edit, start, or delete scheduled games |
| Quick Dashboard Access | Jump directly to game dashboard     |

---

## Creating a Game

### Step 1: Open Create Game Modal

![Create Game Button](images/create-game-update.png)

1. On the Home Page, click the **"+ Create Game"** button
2. A modal dialog will appear

### Step 2: Fill in Game Details

The Create Game modal has the following fields:

#### Field 1: Game Name (Required)

- **Label**: "Game Name"
- **Instructions**: Enter a descriptive name for your game
- **Example**:
    - "Championship Final - Team A vs Team B"

#### Field 2: Game URL (Required)

- **Label**: "Game URL"
- **Supported Formats**:
    - YouTube links: `https://www.youtube.com/watch?v=...`
    - Vimeo links: `https://vimeo.com/...`
    - HLS streams: `.m3u8` file URLs
    - Direct video URLs: HTTP/HTTPS video file links

#### Field 3: Second Game URL (Optional)

- **Label**: "Second Game URL"
- **Instructions**: Enter an additional video URL if needed
- **Supported Formats**: Same as Game URL

#### Field 4: Template Set (Optional)

- **Label**: "Template Set"
- **Instructions**: Select a question set to pre-populate questions for this game
- **Options**:
    - "None" - Start with no pre-loaded questions
    - Any set you've created in Template Builder
- **Note**: Selecting a template set will make those questions available in the Game Controls panel

#### Field 5: Schedule for Later (Optional)

- **Label**: "Schedule for later" (Checkbox)
- **Instructions**: Check this box to schedule the game for a future date and time
- **When Checked**: Additional fields appear:
    - **Scheduled Date**: Select a future date
    - **Scheduled Time**: Select a time
- **Requirements**:
    - Scheduled time must be in the future
    - Both date and time are required when scheduling

### Step 3: Create or Schedule the Game

1. Review all information you entered
2. Click the appropriate button:
    - **"Create Game"** - Start the game immediately
    - **"Schedule Game"** - Save the game for later (if scheduled)
    - **"Cancel"** - Close the modal without creating

### Step 4: Confirmation

#### For Immediate Games

- You will be automatically redirected to the **Dashboard**
- The game is now active and ready for player participation

#### For Scheduled Games

- A success message will appear: "Game scheduled successfully!"
- The game appears in the **Scheduled Games** section on the Home Page
- The game will remain scheduled until you start it
---


## Dashboard Overview

### Main Dashboard Layout

![Dashboard Layout](images/dashboard.png)

The Dashboard is divided into three main panels:

### Left Panel: App View

- **Video Player**: Shows the current game video

### Middle Panel: Game Controls

- **Play Templates**: Quick-access predefined plays
- **Answer Selection**: Choose correct answers for verification

### Right Panel: Message Controls

- **System Messages**: Game notifications and updates

### Top Navigation

- **Logo**: Return to home page
- **Logout**: Exit the dashboard
- **End Game Button**: Terminate the current game session

---

## Game Controls

### Understanding the Game Controls Panel

![Game Controls Panel](images/game-controls.png)

The Game Controls panel is where you manage all interactive elements of your game.

### Starting a play

#### Step 1: Select a play

![Play Selection](images/start-play.png)

1. Click on one of the play option buttons
2. The form will update based on your selection
3. It will highlight the selected option as being active
4. It will display a button to close the play if needed

#### Step 2: Close a play

![Close Play Button](images/close-play.png)

1. When ready to reveal answers, click the **"Close Play Window"** button
2. The **"Close Play"** button will update to **"PLAY WINDOW CLOSED"**
3. The play will be closed, and you can select the answer to the play

#### Step 3: Select the answer

![Select Answer](images/send-answer.png)

1. Click on one of the answer option buttons to select the correct answer
2. The selected answer will be highlighted
3. Click the **"Send Answers"** button to confirm your selection
4. The correct answer will be sent to all connected players
5. The play will be finally closed.

---

### Creating Custom Questions (On-the-Fly)

Custom questions allow you to create questions instantly during a game without using predefined templates. This is perfect for unexpected plays or situations that weren't anticipated.

#### Step 1: Open Custom Question Modal

1. In the Game Controls panel, locate the **"+ Custom Question"** button
2. Click the button to open the Custom Question creation modal

#### Step 2: Enter Question Details

The Custom Question modal contains the following fields:

**Question Text**

- Enter your question text (up to 200 characters)
- Example: "Will they go for a 2-point conversion?"

**Options**

- You can add 2 to 6 answer options
- For each option:
    - Enter the option text (up to 100 characters)
    - Set the points value (between 1 and 100)
- Click **"+ Add Option"** to add more options (up to 6 total)
- Click the **×** button to remove an option (minimum 2 required)

**Save as Template**

- Check the **"Save as template for future use"** checkbox if you want to reuse this question in future games
- If checked, the question will be saved to your question templates list
- If unchecked, the question will be used only for this game session

#### Step 3: Create the Question

1. Review all fields to ensure they are correct
2. Click **"Create Question"** to activate the question
    - OR click **"Cancel"** to close without creating

#### Step 4: Managing Custom Questions

Once created, custom questions work just like template questions:

1. The question appears in the Custom Question display area
2. Players can submit their predictions
3. When ready, close the play window (see [Step 2: Close a play](#step-2-close-a-play))
4. Select the correct answer(s) from the options
5. Click **"Send Answers"** to submit the results

### Important Notes for Custom Questions

- **Points Range**: Each option must have points between 1 and 100
- **Minimum Options**: At least 2 options are required
- **Maximum Options**: Up to 6 options can be added
- **Template Saving**: If you save as template, the question will appear in your question list with a number (e.g., "#10 - Will they go for a 2-point conversion?")
- **One-Time Use**: If not saved as template, the question is only available for the current game

---

## Messaging

### Message Controls Panel Overview

![Message Controls](images/message-controls.png)

The right panel allows you to reward players.

### Type of Messages

#### Reward Messages

- **Automatic**: Sent by the system
- **Content**: Congratulatory messages and rewards for correct answers to top players

### Sending a Message

![Send Message](images/send-message.png)

1. Click on one of the message reward option buttons
2. Two buttons will appear: **"Send"** and **"Cancel"**
3. Click **"Send"** to broadcast the message to all players
4. Click **"Cancel"** to discard the message

---

## Achievement Badges

### Badge System Overview

The Achievement Badge system allows you to create, manage, and award badges to players based on their performance. Badges can be awarded automatically when players meet certain criteria, or manually by you as the game master.

### Creating a Badge

#### Step 1: Open Create Badge Modal

1. In the Badge Manager section, click the **"+ Create Badge"** button
2. The Create Badge modal will appear

#### Step 2: Fill in Badge Details

**Basic Information**

- **Badge Name**: Enter a descriptive name (e.g., "Point Master", "Sharp Shooter")
- **Description**: Explain what the badge represents and how to earn it
- **Icon**: Enter an emoji (e.g., 🏆, ⭐, 🎯) or an image URL
- **Rarity**: Select from:
    - **Common** (Gray) - Basic achievements
    - **Rare** (Blue) - Uncommon achievements
    - **Epic** (Purple) - Significant achievements
    - **Legendary** (Orange) - Exceptional achievements

**Badge Scope**

- **Game-Specific**: Badge is only available for the current game
- **Global**: Badge is available across all games

**Awarding Criteria**
Select how the badge is earned:

- **Points Threshold**: Awarded when a player reaches a certain point total
    - Enter the minimum points required (e.g., 100)
- **Accuracy Threshold**: Awarded when a player achieves a certain accuracy percentage
    - Enter the minimum accuracy percentage (e.g., 80)
    - Requires at least 1 prediction to be eligible
- **Participation Threshold**: Awarded when a player participates in a certain number of questions
    - Enter the minimum number of questions (e.g., 10)
- **Perfect Game**: Awarded when a player gets all predictions correct in a game
    - No additional value required
- **Manual**: Badge must be awarded manually by you
    - Use this for special recognition or custom achievements

**Points Reward** (Optional)

- Enter bonus points to award when the badge is earned (e.g., 50)

#### Step 3: Create the Badge

1. Review all information
2. Click **"Create Badge"** to save
    - OR click **"Cancel"** to close without creating

### Managing Badges

#### Viewing Badges

The Badge Manager displays all badges in a grid layout showing:

- Badge icon and name
- Description
- Rarity level (color-coded)
- Scope (game or global)
- Number of times the badge has been earned
- Action buttons (Edit, Award, Delete)

#### Editing a Badge

1. Click the **Edit** icon (pencil) on the badge card
2. Modify the badge details in the modal
3. Click **"Update Badge"** to save changes

> **Note**: You can only change the scope of a badge if it hasn't been earned yet.

#### Deleting a Badge

1. Click the **"Delete"** button on the badge card
2. Confirm the deletion in the dialog
3. The badge will be permanently removed

### Awarding Badges

#### Automatic Awarding

Badges with criteria (points, accuracy, participation, perfect game) are automatically checked and awarded when:

1. You click the **"Check & Award Badges"** button in the Badge Manager
2. The system checks all players against badge criteria
3. Players who meet the criteria automatically receive the badge
4. A success message confirms the check is complete

> **Tip**: It's recommended to check badges periodically during the game and especially before ending the game.

#### Manual Awarding

For badges with "Manual" criteria type:

1. Click the **"Award"** button on the badge card
2. Select a player from the dropdown list
3. Click **"Award Badge"** to assign the badge
4. The badge is immediately assigned to the selected player

### Badge Statistics

The Badge Manager displays:

- **Total Badges**: Number of badges created for this game
- **Awarded**: Total number of badge assignments (players who earned badges)

### Important Notes for Badges

- **Automatic Checking**: Badges are not checked automatically in real-time. Use "Check & Award Badges" to update awards.
- **Game-Specific vs Global**: Game-specific badges only apply to the current game. Global badges apply across all games.
- **Badge Rarity**: Rarity affects visual styling but doesn't impact functionality.
- **Points Rewards**: Bonus points from badges are added to the player's total score.
- **Multiple Badges**: Players can earn multiple badges in a single game.

---

## Template Builder

### Overview

The Template Builder allows you to create and manage question sets (templates) that can be reused across multiple games. This feature helps you organize your questions into logical groups and makes it easier to prepare questions before a game starts.

### Accessing Template Builder

![Template Builder Navigation](images/home-page.png)

1. From the Home Page, click **"Template Builder"** in the left sidebar
2. You will see the Template Builder page with all your question sets

### Template Builder Page Layout

![Template Builder Page](images/template-builder.png)

The Template Builder page displays:

- **Header**: "Sets" title and "+ Create Set" button
- **Sets Grid**: All your question sets displayed as cards
- **Set Cards**: Each card shows:
    - Set name
    - Number of questions in the set

### Creating a New Set

#### Step 1: Open Create Set Modal

1. Click the **"+ Create Set"** button in the header
2. A modal dialog will appear

#### Step 2: Enter Set Name

![Create Set Modal Step 1](images/create-set-step1.png)

1. Enter a descriptive name for your set (e.g., "Football", "Basketball", "Baseball")
2. Set names must be:
    - Between 1 and 50 characters
    - Unique (cannot duplicate existing set names)
3. Click **"Next"** to proceed

#### Step 3: Create First Question

![Create Set Modal Step 2](images/create-set-step2.png)

1. Enter the question text (up to 200 characters)
2. Add 2-6 answer options:
    - Enter option text (up to 100 characters)
    - Set points value (1-100)
    - Click **"+ Add Option"** to add more options
    - Click **×** to remove an option
3. Click **"Create Set"** to save

> **Note**: The first question is automatically added to the new set. You can add more questions later from the Set Dashboard.

### Managing Sets

#### Viewing a Set

![Set Card](images/set-manager.png)

1. Click on any set card to open the Set Dashboard
2. You will see all questions in that set

#### Renaming a Set

1. Open the Set Dashboard for the set you want to rename
2. Click the **"Rename"** button next to the set name
3. Enter the new name (1-50 characters)
4. Click **"Save"** to confirm
    - OR click **"Cancel"** to discard changes

> **Warning**: Renaming a set updates all questions in that set. This action affects all games using questions from this set.

#### Deleting a Set

1. Open the Set Dashboard for the set you want to delete
2. Scroll to the bottom of the page
3. Click the **"Delete Set"** button
4. Confirm the deletion in the dialog

> **Warning**: Deleting a set will:
> - Remove the set from all questions that belong to it
> - Delete questions that belong ONLY to this set
> - This action cannot be undone

#### Adding Questions to a Set

1. In the Set Dashboard, scroll to the question list
2. Click **"+ Add Question"** button
3. Fill in the question details:
    - Question text
    - Answer options (2-6 options)
    - Points for each option
4. Click **"Create Question"** to save

#### Editing Questions

1. Find the question you want to edit in the list
2. Click the **"Edit"** button on the question card
3. Modify the question text or options
4. Click **"Update Question"** to save changes

#### Deleting Questions

1. Find the question you want to delete
2. Click the **"Delete"** button on the question card
3. Confirm the deletion in the dialog

> **Note**: Deleting a question removes it from the set and all future games. It does not affect questions already used in past games.

---

## Game History

### Overview

The Game History page allows you to view all your past games, see game statistics, and access detailed information about completed game sessions.

### Accessing Game History

1. From the Home Page, click **"History"** in the left sidebar
2. You will see the Game History page with all your ended games

### Game History Page Layout

![Game History Page](images/history-main.png)

The Game History page displays:

- **Header**: "Game History" title
- **Games List**: All your ended games displayed in a table or list format
- **Game Information**: Each game shows:
    - Game name
    - Date ended
    - Number of questions asked
    - Number of players
    - Status (ended)

### Viewing Game Details

1. Click on any game in the history list
2. You will be taken to the Game Detail page

### Game Detail Page

![Game Detail Page](images/history-page.png)

The Game Detail page shows comprehensive information about a specific game:

- **Game Information**:
    - Game name
    - Creation date
    - End date
    - Duration
    - Status
- **Statistics**:
    - Total questions asked
    - Total players
    - Player participation rates
- **Questions List**: All questions asked during the game
- **Player Activity**: Overview of player engagement
---

## Audit Logs

### Overview

The Audit Logs feature provides a comprehensive audit trail of all administrative actions performed in the system. This helps track changes, maintain accountability, and troubleshoot issues.

### Accessing Audit Logs

1. From the Home Page, click **"Audit Logs"** in the left sidebar
2. You will see the Audit Logs page with all administrative actions

### Audit Logs Page Layout

![Audit Logs Page](images/audit-hide-filter.png)

The Audit Logs page displays:

- **Header**: "Audit Logs" title and filter toggle button
- **Filters Section**: (Expandable) Filter options for actions, entity types, and admins
- **Audit Logs Table**: All logged actions displayed in a table format

### Understanding Audit Log Entries

Each audit log entry contains:

- **Timestamp**: When the action occurred
- **Action**: Type of action (CREATE, UPDATE, DELETE)
- **Entity Type**: What was modified (game, badge, question, user, etc.)
- **Entity ID**: Unique identifier of the affected item
- **Admin**: Who performed the action (email and name)
- **Changes**: Before/after values (if applicable)
- **Reason**: Description of the action

### Filtering Audit Logs

![Audit Logs Filters](images/audit-show-filter.png)

#### Step 1: Show Filters

1. Click the **"Show Filters"** button in the header
2. The filters section will expand

#### Step 2: Apply Filters

You can filter by:

- **Action**: CREATE, UPDATE, DELETE, or All Actions
- **Entity Type**:
    - Game
    - Badge
    - Badge Definition
    - Badge Assignment
    - Question
    - Question Template
    - User
    - Or All Types
- **Admin**: Current User or All Admins

#### Step 3: Clear Filters

1. Click the **"Clear Filters"** button (X icon) to remove all active filters
2. The table will show all audit logs again
---

## Keyboard Hotkeys

### Overview

Keyboard hotkeys allow you to quickly perform common actions without using the mouse. This can significantly speed up your workflow during active games.

### Available Hotkeys

#### Number Keys (1-9, 0)

**Function**: Select a question template from the list

**How to Use**:

- Press **1** through **9** to select the first through ninth question template
- Press **0** to select the tenth question template
- The question is immediately created and activated

**When Available**:

- Always available when viewing the Game Controls panel
- Works even when typing in form fields

**Example**:

- Press **3** to quickly activate the third question template in your list

#### Spacebar

**Function**: Close the active play window

**How to Use**:

- Press **Space** when a question is active (status: "Predictions OPEN")
- The play window will close, allowing you to select answers

**When Available**:

- Only works when there is an active question with status "active"
- Prevents default scrolling behavior

**Example**:

- After players have submitted predictions, press **Space** to close the question window

#### Enter Key

**Function**: Send selected answers

**How to Use**:

- Select one or more answer options
- Press **Enter** to submit the selected answers
- Answers are sent to all players immediately

**When Available**:

- Only works when you have selected at least one answer
- Works in form fields and throughout the interface

**Example**:

- After closing a question and selecting the correct answer, press **Enter** instead of clicking "Send Answers"

### Hotkey Reference Table

| Hotkey    | Action                             | When Available            |
| --------- | ---------------------------------- | ------------------------- |
| **1-9**   | Select question template (1st-9th) | Always                    |
| **0**     | Select question template (10th)    | Always                    |
| **Space** | Close play window                  | When question is active   |
| **Enter** | Send selected answers              | When answers are selected |

---

## Ending a Game

### Before You End the Game

Ensure you have:

- ✓ Asked all planned questions
- ✓ Announced final results
- ✓ Rewarded top players
- ✓ Checked and awarded achievement badges (click "Check & Award Badges" in Badge Manager)

### Step 1: Click End Game Button

![End Game Button](images/end-game.png)

1. In the top navigation bar, click **"End Game"** button
2. A confirmation dialog will appear

### Step 2: Confirm Game Termination

![Confirm End Game](images/end-game-modal.png)

The dialog will show:

- Game name: "[Game Name] will be ended"
- Warning: "This action cannot be undone"
- Confirmation buttons: **"Cancel"** or **"Confirm"**

> **Warning**: Ending a game cannot be reversed. All active questions will be closed.

### Step 3: Game Ended

![Game Ended Success](images/ended-game.png)

After confirmation:

- You are redirected to the Home Page

---

## FAQ

### General Questions

**Q: Can I use Play by Play Admin on mobile devices?**  
A: While the application may be accessible on mobile, it's optimized for desktop/laptop use. A tablet may work well for testing purposes.

### Game Management

**Q: How long can a game session last?**  
A: As long as you need. Games can run for hours. Just remember to click "End Game" when finished.

**Q: What happens if I accidentally close the browser during a game?**  
A: Log back in immediately. Your game should still be active, and you can resume. Player data is preserved.

**Q: Can I have multiple games running simultaneously?**  
A: No, you can only have one active game at a time as an admin. You must end the current game before starting a new one.

**Q: Can I create questions that aren't in the template list?**  
A: Yes! Use the "+ Custom Question" button to create questions on-the-fly. You can optionally save them as templates for future use.

**Q: How do badges get awarded to players?**  
A: Badges with automatic criteria (points, accuracy, participation, perfect game) are awarded when you click "Check & Award Badges". Manual badges must be awarded by clicking the "Award" button on the badge.

**Q: Can I use keyboard shortcuts to speed up my workflow?**  
A: Yes! Press number keys (1-9, 0) to select questions, Space to close play windows, and Enter to send answers. See the [Keyboard Hotkeys](#keyboard-hotkeys) section for details.

**Q: What's the difference between game-specific and global badges?**  
A: Game-specific badges only apply to the current game. Global badges are available across all games and can be earned by players in any game session.

**Q: How do I organize my questions into sets?**  
A: Use the Template Builder feature to create question sets. You can organize questions by sport, event type, or any other category. See the [Template Builder](#template-builder) section for details.

**Q: Can I reuse questions from previous games?**  
A: Yes! Questions created in the Template Builder can be reused across multiple games. When creating a game, you can select a template set to pre-populate questions.

**Q: How do I view my past games?**  
A: Click "History" in the sidebar to see all your ended games. You can view detailed statistics and information about each game. See the [Game History](#game-history) section for details.

**Q: What are audit logs and why are they important?**  
A: Audit logs track all administrative actions in the system, including who performed what action and when. This helps maintain accountability and troubleshoot issues. See the [Audit Logs](#audit-logs) section for details.

**Q: Can I edit or delete audit logs?**  
A: No, audit logs are read-only and cannot be modified or deleted. They serve as a permanent record of all administrative actions.

**Q: How do I rename a question set?**  
A: Open the Set Dashboard for the set you want to rename, click the "Rename" button, enter the new name, and save. Note that this updates all questions in the set. See the [Template Builder](#template-builder) section for details.

---

## Document Information

**Last Updated**: February 3, 2026
**Version**: 4.0  
**For**: Play by Play Admin Users

### Version History

- **Version 3.0** (December 2025): Added Template Builder, Game History, and Audit Logs features
- **Version 2.0** (Previous): Achievement Badge System and Custom Questions
- **Version 1.0** (Initial): Core game management features
