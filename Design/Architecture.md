# Architecture

```mermaid
flowchart TB
    subgraph Presentation_Layer["Presentation Layer"]
        UI["React + TypeScript Web Client<br/>(Admin Dashboard)"]
        GMUI["Game Master Dashboard"]
        AMUI["Ad Master Dashboard"]
    end

    subgraph Business_Layer["Business Logic Layer"]
        GMService["Game Management Module"]
        PredService["Prediction Management Module"]
        AdService["Ad Management Module"]
        RewardService["Reward & Legend Mode Module"]
    end

    subgraph Data_Interface_Layer["Data Interface Layer"]
        FirebaseSDK["Firebase SDK / Firestore API"]
        Auth["Firebase Authentication"]
    end

    subgraph Database_Layer["Database Layer"]
        Firestore[(Firestore Collections)]
        subgraph Collections["Collections"]
            Games[(Games)]
            Predictions[(Predictions)]
            Ads[(Ads)]
            Users[(Users)]
            Rewards[(Rewards)]
        end
    end

    %% Communication arrows
    UI --> GMService
    UI --> PredService
    UI --> AdService
    UI --> RewardService

    GMService --> FirebaseSDK
    PredService --> FirebaseSDK
    AdService --> FirebaseSDK
    RewardService --> FirebaseSDK

    FirebaseSDK --> Firestore
    Auth --> Users


