## Actors
- **Game Master (GM)**  
  Responsible for creating and managing games. They will choose/create prediction questions, open/close prediction windows, select play presets, mark correct answers, monitor the video stream feed, and perform operational workflows during a live session (including optional messaging/moderation tasks when enabled).

- **Ad Master (AM)**  
  Manages the shown advertisements. They will upload ad assets, preview the ads, and schedule the ads.

- **Player (User)**  
  Target demographic is 19–35. Players interact by predicting plays. Players can earn points, compete on the leaderboard, and receive rewards.

- **System (PxP Platform / Firebase backend)**  
  Provides real-time updates, persistence, authentication, and authorization for admin workflows.

---

## UseCases

### UC1: Create Game
The Game Master must be able to create a new live or taped game.  
This will be done by entering a video stream URL.

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM logs into the PxP dashboard.  
2. GM selects "Create Game."  
3. GM enters game details (name, feed URL).  
4. System validates and stores details in Firebase.  
5. Game session becomes available for live or taped scoring.  

**Requirement Link:** FR1  

---

### UC2: Manage Prediction Windows
The prediction window will allow players to guess outcomes in real time. This will be controlled and set by a preset the Game Master selects.  

**Actors:**  
- Game Master  
- System  
- Player  

**Flow:**  
1. GM selects a prediction preset during a play.  
2. Players receive the window and select their prediction.  
3. GM closes the window.  
4. GM selects the correct outcome.  
5. System stores player responses.  

**Requirement Link:** FR2  

---

### UC3: Create and Select Prediction Questions
GMs can select templates or add new questions to give players choices for each play.  

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM selects a template or creates a custom question.  
2. System saves the question.  
3. GM links it to an upcoming prediction window.  

**Requirement Link:** FR3  

---

### UC4: Mark Correct Answer
After each play, the GM must identify and select the correct outcome of the play so that the system can award points to Players.  

**Actors:**  
- Game Master  
- System  
- Player  

**Flow:**  
1. GM identifies outcome of the play.  
2. GM selects the correct answer.  
3. System awards points to correct players.  

**Requirement Link:** FR4  

---

### UC5: Upload Ads
The Ad Master must upload ad assets which will display to players.  

**Actors:**  
- Ad Master  
- System  

**Flow:**  
1. AM goes to "Upload Ad."  
2. AM uploads an image/asset.  
3. System stores ad data in Firebase.  

**Requirement Link:** FR5  

---

### UC6:  Manage Ads
Ads should appear during the right times. The Ad Master can manage when they will appear during games.  

**Actors:**  
- Ad Master  
- System  
- Player  

**Flow:**  
1. AM selects an uploaded ad.   
2. System displays ads on players’ screens.  

**Requirement Link:** FR6  

---

### UC7: Preview Ads
The Ad Master should preview ads to ensure that sizing and formatting is correct.  

**Actors:**  
- Ad Master  
- System  

**Flow:**  
1. AM selects an uploaded ad.  
2. System displays a preview.  
3. AM approves or re-uploads.  

**Requirement Link:** FR7  

---

### UC8: Activate Legend Mode
GMs can run Legend Mode. This is a pre-recorded game. These games are scored similarly to live games but are based on pre-recorded taped footage.  

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM selects Legend Mode.  
2. GM selects a pre-recorded game.  
3. Players interact as if it were a live game.  

**Requirement Link:** FR8  

---

### UC9: Save and Resume Game Setup (Drafts)
The Game Master must be able to save partial game setup work and return later without losing configuration progress.

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM starts creating a game (details, template selection, stream configuration, etc.).  
2. GM saves a draft (explicitly or via autosave behavior, depending on product implementation).  
3. System persists draft state.  
4. GM later resumes the draft and continues setup.  

**Requirement Link:** FR20  

---

### UC10: Reorder Questions Within a Game Session
The Game Master must be able to change the ordering of upcoming questions/plays to match the real broadcast when the planned order shifts.

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM opens the game’s question/play list.  
2. GM reorders items (drag/drop or equivalent).  
3. System persists the new ordering for the session.  

**Requirement Link:** FR21  

---

### UC11: Configure Hotkey Combinations for Frequent Controls
The Game Master must be able to bind frequent actions to keyboard shortcuts (including multi-key combinations where supported) to operate faster during live games.

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM opens hotkey settings.  
2. GM assigns actions to shortcut combinations.  
3. System stores preferences and applies them in the live controls UI.  

**Requirement Link:** FR22  

---

### UC12: Export Operational Data (CSV/JSON)
Administrators must be able to export datasets from key operational screens for analysis, reporting, and record keeping.

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM navigates to an export-capable screen (e.g., game history, audit logs, leaderboards—depending on product scope).  
2. GM applies filters/search as needed.  
3. GM exports results as CSV and/or JSON.  
4. System generates a downloadable file consistent with the current UI filters.  

**Requirement Link:** FR23  

---

### UC13: Search, Filter, and Review Past Games (Game History)
The Game Master must be able to locate prior games quickly and review relevant session metadata.

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM opens Game History.  
2. GM searches/filters by relevant fields (e.g., name/status/date—exact fields depend on implementation).  
3. System returns matching games for review/navigation.  

**Requirement Link:** FR24  

---

### UC14: Moderate Player Chat (When Enabled)
When player chat is enabled for a session, operators must be able to review messages, apply moderation actions, and reduce risk of abusive content during live play.

**Actors:**  
- Game Master  
- System  
- Player  

**Flow:**  
1. Player sends chat messages during a game session (if enabled).  
2. GM opens moderation tools for the session.  
3. GM reviews messages and flags/profanity/AI-assisted signals (depending on configuration).  
4. GM takes moderation actions consistent with policy (e.g., hide/remove/ban workflows as implemented).  
5. System applies updates and reflects changes to clients as designed.  

**Requirement Link:** FR25  

---

### UC15: Preview the Player Experience (AppView Emulation)
The Game Master must be able to preview how key player UI states render without requiring a separate physical device workflow for every check.

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM opens AppView preview/emulation in the admin dashboard.  
2. GM selects a representative player UI context/state.  
3. System renders a faithful preview for operational validation.  

**Requirement Link:** FR26  

---

### UC16: Use an In-App AI Assistant (Optional)
The Game Master may use an optional AI assistant to answer operational questions and accelerate common workflows when an AI provider is configured.

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM opens the AI assistant panel.  
2. GM asks a question or selects a suggested workflow prompt.  
3. System returns guidance via the configured provider.  
4. If AI is disabled/unconfigured, the product should not block core admin functionality.  

**Requirement Link:** FR27  

---

### UC17: Track Administrative Changes (Audit Logs)
The system should support reviewing administrative actions for accountability and incident follow-up.

**Actors:**  
- Game Master  
- System  

**Flow:**  
1. GM opens audit logs.  
2. GM filters to a relevant time range/entity/action type (as implemented).  
3. System displays a chronological record of administrative changes.  

**Requirement Link:** FR28  
