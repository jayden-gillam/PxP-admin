# Domain Model

### **User:**
- Represents a person interacting with the system. 
- Users have roles that determine their abilities within the system (Game Master or Ad Master)

### **Game:** 
- The livestreaming system where users watch the event and participate in predictions. 
- Games are created by Game Masters and are the core unit to all of the other classes.

### **PredictionWindow:**
- A window controlled by Game Masters, where users can answer prediction questions surrounding the game.

### **PredictionQuestion:**
- The question shown during a Prediction Window. 
- Questions can be created from a predefined template or customized.

### **Ad:**
- An asset (image/link) uploaded by an Ad Master to be shown during a game. 
- Ad Masters can also schedule ads to appear at specific times, and can preview them before deployment to ensure they're correct.

### **Reward:**
- A system that displays and awards points.

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
    %% === RELATIONSHIPS ===
    User --> Game : creates
    Game --> PredictionWindow : has
    PredictionWindow --> PredictionQuestion : contains
    Game --> Ad : displays
    Game --> Reward : grants





  
