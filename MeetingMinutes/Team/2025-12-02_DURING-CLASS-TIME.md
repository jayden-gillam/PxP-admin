# Team Meeting — December 02, 2025
**Date:** December 02, 2025  
**Meeting Start Time:** 10:00 PM EST  
**Meeting End Time:** 10:55 PM EST  
**Location/Medium:** Zoom (During Class Time)  
**Present:** Shristi, Nzenwata  
**Minute Recorder:** Shristi Khadka  

---

### Things Clarified

- Template-based questions were showing fallback images even when no image existed.  
  Custom questions were functioning correctly (text-only).  
  **Decision:** If a template image is missing, show text instead. Shristi will update the PR today.

- Quarter-based leaderboard clarifications:  
  Our team only triggers/manages quarters in Game Master.  
  We do **not** build or display leaderboard features for Iteration 2.

- Reconfirmed modularity rules:  
  **No Firebase calls allowed in UI components.**  
  All data logic must go through services.  
  Shristi will create a modular architecture diagram.

---

### Topics Discussed

1. **Template Image Bug & Fix**  
   - Confirmed root cause: fallback images shown even when template image missing.  
   - Fix: show text instead of fallback image.  
   - Shristi will update PR.

2. **Quarter Logic**  
   - Team only implements quarter triggering.  
   - Leaderboard logic is not part of our iteration.  
   - Quarter IDs not required for Iteration 2.

3. **Score Tracking**  
   - Discussed future use of quarter IDs.  
   - Not necessary for current iteration.  
   - Game Master functionality unaffected.

4. **Modularity & Code Structure**  
   - Reaffirmed strict modularity rules.  
   - No direct Firebase usage in UI.  
   - All logic flows through services layer.  
   - Shristi will create architecture diagram tonight.

5. **Thursday Presentation Prep**  
   - Presenter: Sinclair
   - Includes modular diagram + Google Slides deck.  
   - Slides link will be posted on Discord.

6. **Assignments, Testing, and Submission Plan**  
   - Merge all completed work into main.  
   - Create release tag.  
   - Fix mobile app issue.  
   - Achieve 90–100% test coverage.  
   - Submit meeting notes.  
   - Ask Matt during 3:30 meeting about third iteration expectations.  
   - Any required changes will be moved into second iteration updates.

7. **Process Improvements**  
   - Agreed to enable all meeting notes going forward.  
   - Shristi identified and will fix template image logic issue.  
   - Will finalize modular diagram and update PR.  
   - Will rebuild Google Slides presentation.  
   - Will merge all changes to main today and create release tag.  
   - Nzenwata will complete documentation for new features and shortcuts.  
   - Will verify testing coverage and development expectations.

---
