# Requirements

## Functional Requirements

- **FR1: Create Game**
  The system must allow Game Masters to create new games by entering game details such as game name and video stream URLs.  
  - Use Case: UC1  
  - Priority: HIGH  

- **FR2: Manage Prediction Windows**
  Game Masters must be able to open and close prediction windows during a live game session.  
  - Use Case: UC2  
  - Priority: HIGH  

- **FR3: Create and Select Prediction Questions**
  Game Masters must be able to select prediction questions from predefined templates or create custom questions.  
  - Use Case: UC3  
  - Priority: HIGH  

- **FR4: Mark Correct Answer**
  After a play ends, Game Masters must be able to select the correct answer so the system can award points.  
  - Use Case: UC4  
  - Priority: HIGH  

- **FR5: Upload Ads**
  Ad Masters must be able to upload advertisements, including an image/asset and a URL.  
  - Use Case: UC5  
  - Priority: LOW

- **FR6: Manage Ads**
  Ad Masters must be able to manage ads during live games and control when they appear.  
  - Use Case: UC6  
  - Priority: LOW

- **FR7: Preview Ads**
  Ad Masters must be able to preview uploaded ads before deploying them in live games.  
  - Use Case: UC7  
  - Priority: LOW 

- **FR8: Activate Legend Mode**
  Game Masters must be able to convert a game into “Legend Mode,” (initially hard-coded).  
  - Use Case: UC8  
  - Priority: LOW 

- **FR9: Quarter-by-Quarter Leaderboard**  
  The system must allow the Game Master to start a new quarter and display leaderboards for each quarter separately from the full-game leaderboard.
  - Priority: HIGH  

- **FR10: On-the-Fly Question Creation**  
  The system must allow the Game Master to create or edit questions during a live game session without restarting the game.
  - Priority: HIGH  

- **FR11: Hotkeys for Game Controls**  
  The system must support keyboard shortcuts for frequent Game Master actions (e.g., start round, next question, reveal answers).
  - Priority: HIGH  

- **FR12: Player Screen**  
  The system must support displaying player screen in the Game Master interface.
  - Priority: HIGH
  
- **FR13: Achievement Badges (Reward System)**  
  The system must replace Uber Eats rewards with visual achievement badges that can be earned during gameplay.
  - Priority: MEDIUM 

- **FR14: Test HLS Link Before Game Activation**  
  The system must allow the Game Master to preview or test the live HLS link before making a game active, ensuring the stream works correctly before it appears in the Games tab on mobile.
  - Priority: HIGH  

- **FR15: UI Fixes and Figma Alignment**  
  The system’s interface must be refined to match the updated Figma design.  
  This includes improving spacing, typography, button styling, and layout consistency across pages such as the Game Master dashboard, Create Game screen, and leaderboard view.
  - Priority: MEDIUM
    
- **FR16: Sync Status Indicator**  
  The system must display how many players are behind in the stream (e.g., “8% ~2.3 seconds”).  
  It should also suggest when a resync may be needed, but resync remains fully manual.  
    - Priority: MEDIUM

- **FR17: Custom Question Image Support**  
  The system must allow Game Masters to upload optional images when creating custom questions.   
  Saved templates should retain their associated images.  
    - Priority: HIGH

- **FR18: Template Builder Page**  
  The system must provide a dedicated page for creating, editing, and managing template sets (e.g., Football Set, Basketball).  
    - Priority: HIGH

- **FR19: Game Template Selection**  
  The system must allow Game Masters to choose a template set when creating a new game.  
  Once selected, the system automatically loads all questions from that template set.  
    - Priority: MEDIUM

- **FR20: Game Setup Drafts**  
  The system must allow Game Masters to save and resume partial game setup (drafts) without losing in-progress configuration.  
  - Use Case: UC9  
  - Priority: HIGH  

- **FR21: Question Reordering**  
  The system must allow Game Masters to reorder upcoming questions/plays during a session to match the real broadcast flow.  
  - Use Case: UC10  
  - Priority: HIGH  

- **FR22: Hotkey Combination Configuration**  
  The system must allow Game Masters to configure keyboard shortcuts (including multi-key combinations where supported) for frequent live controls.  
  - Use Case: UC11  
  - Priority: HIGH  

- **FR23: Data Exports (CSV/JSON)**  
  The system must support exporting operational datasets from relevant admin screens, respecting the operator’s current filters/search scope.  
  - Use Case: UC12  
  - Priority: MEDIUM  

- **FR24: Game History Search & Filtering**  
  The system must provide search/filter capabilities for reviewing prior games and locating sessions quickly.  
  - Use Case: UC13  
  - Priority: MEDIUM  

- **FR25: Player Chat Moderation**  
  When player chat is enabled, the system must provide moderation workflows for operators to review and act on chat content according to implemented policy/controls.  
  - Use Case: UC14  
  - Priority: HIGH  

- **FR26: AppView / Player UI Preview**  
  The system must provide an in-admin preview of player-facing UI states to validate layout and messaging during operations.  
  - Use Case: UC15  
  - Priority: MEDIUM  

- **FR27: Optional AI Assistant**  
  The system may provide an optional in-app AI assistant for operator guidance when configured; core gameplay/admin operation must remain usable when AI is disabled or unavailable.  
  - Use Case: UC16  
  - Priority: LOW  

- **FR28: Audit Logs**  
  The system must record and expose administrative changes in an auditable log view for operational accountability.  
  - Use Case: UC17  
  - Priority: MEDIUM  



---

## Non-Functional Requirements


- **NR1: Performance**
  The system must update game and ad management actions with minimal delay so that Game Masters and Ad Masters can interact in real time.  
  - Priority: HIGH  

- **NR2: Security**
  Only authorized users (Game Masters and Ad Masters) should be able to access the web interface. Data must be stored securely in Firebase.  
  - Priority: HIGH  

- **NR3: Usability**
  The web dashboards must be intuitive and easy to use, with clear workflows for creating games, managing ads, and handling prediction questions.  
  - Priority: MEDIUM  

- **NR4: Reliability**
  The system must remain available during live games without unexpected crashes or downtime.  
  - Priority: HIGH  

- **NR5: Auditability**
  Administrative actions that affect live operations should be traceable for accountability and incident review (see FR28).  
  - Priority: MEDIUM  

- **NR6: Safety for live moderation**
  Chat moderation features should be designed to reduce operational risk during live events (clear states, confirm destructive actions where appropriate, and avoid blocking core game operation when chat features are disabled).  
  - Priority: MEDIUM  

- **NR7: Data portability**
  Operators should be able to export key operational datasets for offline analysis (see FR23).  
  - Priority: MEDIUM  
 
