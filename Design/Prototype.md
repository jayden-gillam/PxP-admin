
# Prototype

> **Note (April 2026)**: This page preserves the **early interactive prototype** reference from the beginning of the project. The production admin application and workflows have evolved substantially since then. For the current operator experience, see `Documentation/User.md`.

This document contains the interactive prototype for our project.  
The prototype demonstrates the **Game Master Admin Panel** for a football play-by-play prediction platform.  

---

## 🔗 Prototype Link
You can view the interactive prototype here:  
[View Prototype on Lovable](https://gamemaster-playhub.lovable.app/games)

---

## 📺 Prototype Video
We created a walkthrough video that explains the prototype and demonstrates its features.  
You can watch it below:

[![Prototype Video](https://img.youtube.com/vi/ls1_hzfA9Jw/0.jpg)](https://www.youtube.com/watch?v=ls1_hzfA9Jw)

---

## ⚠️ Known Issue
There is currently a small error in the **login flow**:  
- After login, the app incorrectly routes to a `404 error` page.  
- As a temporary workaround, clicking on **Home** in the navigation will take you to the correct dashboard page.  
- This may or may not still reproduce; treat this section as **historical prototype notes**, not a statement about the current production deployment.

---

## ℹ️ Notes
- This prototype is meant to simulate the **admin panel** experience for the Game Master.  
- It covers:
  - Game creation  
  - Play presets and outcomes  
  - Opening and closing plays  
  - Assigning rewards to top users  
  - Ads management with 3-column placement  

The prototype was designed in **Lovable** (approved by prof. Ergin as an alternative to Figma).

## Relationship to current documentation

- **Current workflows + screenshots**: `Documentation/User.md`
- **Engineering onboarding + module map**: `Documentation/Development.md`
