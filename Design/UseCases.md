## Actors
- **Game Master (GM)**
     Responsible for creating and managing games. They will choose/create prediction questions, open/close prediction windows, select         play presets, mark correct answers, and monitor the video stream feed.

- **Ad Master(AM)**
     Manages the shown advertisements. They will upload ad assets, preview the ads, and schedule the ads.

- **Player (User)**
     Target Demographic is 19-35. Players interact by predicting plays. Players can earn points, compete on the leaderboard, and recieve      rewards.

- **System (PxP Platform / Firebase backend)**
     Provides real-time updates

---
## UseCases
- **UC1: Create Game**
     The Gm must be able to create a new live or taped game.This will be done by entering a video stream URL.
     **Actors:** Game Master, System
     **Flow:**
          - GM logs into the PxP dashboard.
          - GM selects "Create Game."
          - GM enters game details (name, feed URL)
          - System validates and stores details in Firebase.
          - Game session becomes available for live or taped scoring.
     **Requirement Link:** FR1

- **UC2: Manage Prediction Windows**
The prediction window will allow players to guess outcomes in real time. This will be controlled and set by a preset the Game Master selects. 
**Actors:** Game Master, System, Player
**Flow:**
1. GM selects a prediction preset during a play.
2. Players recieve the window and select their prediction.
3. GM closes the window.
4. GM selects the correct outcome.
5. System stores player responses.
**Requirement Link:** FR2

- **UC3: Create and Select Prediction Questions**
GMs can select templates or add new questions to give players choices for each play.
**Actors:** Game Master, System
**Flow:**
1. GM selects a template or creates a custom question.
2. System saves the question.
3. GM links it to an upcoming prediction window.
**Requirement Link:** FR3

- **UC4: Mark Correct Answer**
After each play, the GM must identify and select the correct outcome of the play so that the system can award points to Players. 
***Actors:** Game Master, System, Player
**Flow:**
1. GM identifies outcome of the play.
2. GM selects the correct answer.
3. System awards points to correct players.
**Requirement Link:** FR4

- **UC5: Upload Ads**
Ad Master must upload ad assets which will display to players. 
**Actors:** Ad Master, System
**Flow:**
1. AM goes to "Upload Ad."
2. AM uploads an image/asset.
3. System stores ad data in Firebase.
**Requirement Link:** FR5

- **UC6: Schedule and Manage Ads**
Ads should appear duing the right times. The Ad Master can schedule ads and manage when they will appear during games. 
**Actors:** Ad Master, System, Player
**Flow:**
1. AM selects an uploaded ad. 
2. AM assigns it to a schedule and sets the timing.
3. System displays ads on player's screens using the timing and duration the AM sets.
**Requirement Link:** FR6

- **UC7: Preview Ads**
The Ad master should preview ads to ensure that sizing and formatting is correct.
**Actors:** Ad master, System
**Flow:**
1. AM selects and uploaded ad. 
2. System displays a preview.
3. AM approves or re-uploads.
**Requirement Link:** FR7

- **UC8: Activate Legend Mode**
GMs can run Legend Mode. This is a pre-recorded game. These games are scored similarly to live games but are based on pre-recorded taped footage. 
**Actors:** Game Master, System
**FLow:**
1. GM selects Legend mode.
2. GM selects a pre-recorded game.
3. Players interact as if it were a live game.
**Requirement Link:** FR8
