# Domain Model

### **User:**
- Represents a person interacting with the system. 
- Users have roles that determine their abilities within the system (Game Master or Ad Master)

### **Game:** 
- The livestreaming system where users watch the event and participate in predictions. 
- Games are created by Game Masters and are the core unit to all of the other classes.

### **GameDraft (GameSetupDraft):**
- A persisted in-progress configuration for creating or editing a game before it is finalized/launched (operator workflow support).

### **PredictionWindow:**
- A window controlled by Game Masters, where users can answer prediction questions surrounding the game.

### **PredictionQuestion:**
- The question shown during a Prediction Window. 
- Questions can be created from a predefined template or customized.

### **QuestionOrdering / PlayOrdering:**
- The operator-controlled ordering of upcoming questions/plays within a session (so the admin UI can match the real broadcast).

### **HotkeyProfile:**
- Operator-specific keyboard shortcut bindings for frequent live controls (including combination shortcuts when supported).

### **Ad:**
- An asset (image/link) uploaded by an Ad Master to be shown during a game. 
- Ad Masters can also schedule ads to appear at specific times, and can preview them before deployment to ensure they're correct.

### **Reward:**
- A system that displays and awards points.

### **PlayerChatMessage (ChatMessage):**
- A message sent by a player during a session when chat is enabled.

### **OperatorBroadcastMessage:**
- A message sent by operators to players (broadcast-style messaging, depending on product configuration).

### **ModerationAction:**
- An operator action taken on chat content (e.g., hide/remove/ban workflows as implemented) with audit implications.

### **AuditLogEntry:**
- A record of a meaningful administrative change for accountability and incident review.

### **ExportRequest (client-generated):**
- A downloadable export artifact generated from the current UI dataset + filters (CSV/JSON), even if generation is performed entirely client-side.

```mermaid
classDiagram
    class User {
      +String id
      +String email
      +String name
      +Role role
    }
    class Game {
      +String id
      +String name
      +String videoUrl
      +DateTime createdAt
      +DateTime endedAt
      +String status
    }
    class GameDraft {
      +String id
      +DateTime updatedAt
      +String draftJson
    }
    class PredictionWindow {
      +String id
      +DateTime openTime
      +DateTime closeTime
    }
    class PredictionQuestion {
      +String id
      +String text
      +String correctAnswer
      +List~String~ options
      +Integer order
    }
    class HotkeyProfile {
      +String id
      +String userId
      +String bindingsJson
    }
    class Ad {
      +String id
      +String imageUrl
      +String redirectUrl
      +DateTime scheduledTime
    }
    class Reward {
      +String id
      +String description
      +Integer points
    }
    class PlayerChatMessage {
      +String id
      +String gameId
      +String userId
      +String text
      +DateTime sentAt
    }
    class OperatorBroadcastMessage {
      +String id
      +String gameId
      +String authorId
      +String text
      +DateTime sentAt
    }
    class ModerationAction {
      +String id
      +String gameId
      +String moderatorId
      +String actionType
      +DateTime createdAt
    }
    class AuditLogEntry {
      +String id
      +String actorId
      +String actionType
      +String entityType
      +String entityId
      +DateTime createdAt
      +String diffJson
    }
    %% === RELATIONSHIPS ===
    User --> Game : creates
    User --> HotkeyProfile : owns
    User --> GameDraft : edits
    Game --> GameDraft : may_have
    Game --> PredictionWindow : has
    PredictionWindow --> PredictionQuestion : contains
    Game --> Ad : displays
    Game --> Reward : grants
    Game --> PlayerChatMessage : contains
    Game --> OperatorBroadcastMessage : contains
    User --> ModerationAction : performs
    ModerationAction --> PlayerChatMessage : targets
    User --> AuditLogEntry : performs
    AuditLogEntry --> Game : references





  
