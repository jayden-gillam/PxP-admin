# For Future Teams

## Known Issues

### 1. Group Leaderboard Not Updating from Admin
The group leaderboard does not update  when actions are performed through the Web Admin dashboard.  
This occurs because the leaderboard update logic is shared between the mobile application and the admin application, but is not fully triggered or synchronized from the admin side.

### 2. Powerups Not Implemented in Admin
Powerups functionality is not currently available in the Admin dashboard.  

---

## Future Improvements

### 1. Backend Support for Prediction Overlay
The prediction overlay is currently implemented as a UI-only feature.  
A backend implementation is required to:
- Store prediction data
- Sync with the database
- Ensure consistency between mobile and admin applications

### 2. Improve Data Synchronization Between Admin and Mobile
Enhance how shared functions (such as leaderboard updates) are handled to ensure:
- Real-time updates across platforms
- Proper event triggering from both admin and mobile sides

### 3. Expand Admin Feature Parity
Ensure all features available in the mobile application (such as powerups) are also accessible and manageable through the Admin dashboard.

---

## Suggestions for Future Teams

- Clearly separate shared logic between mobile and admin systems to avoid unintended side effects
- Ensure Firebase/Firestore triggers are consistently tested across both platforms
- Maintain strong test coverage, especially for shared services and real-time updates
- Document any cross-platform dependencies early in development
- Test admin-triggered actions thoroughly, not just mobile interactions
