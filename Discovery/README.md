# Discovery Meeting | 9/19/2025 9:00am

## Quick recap

The meeting began with introductions from team members, Matt, Abeeb, and Mike Foss, the CEO of Play by Play, who discussed their partnership with Ball State University. The team explored a prediction game show concept focused on football, with discussions around the Game Master's functionality and implementation of features like Firebase as the backend. Technical challenges were addressed, particularly regarding video synchronization and resync issues, with the team agreeing to prioritize fixing these problems before the October 4th game date while establishing project management tools and timelines.
## Next steps

- Shristi to connect with Dr. Ergin immediately to get access to the repository for the team.
- Shristi to email Mike/Matt/Abeed later today with an update after speaking with Dr. Ergin.
- Team to implement the resync functionality using the code suggestions provided earlier.
- Team to prepare for a test of the resync functionality by Tuesday.
- Team to set up GitHub issues for project management tracking.
- Team to add Matt/Abeed to the Game Masters repository once created.
- Team to focus on fixing the resync issue before October 4th deadline.
- Team to begin work on the web-based Game Master interface after October.
## Summary

### Game Master and Ad Master Goals

The meeting began with introductions from Shristi, Jayden, Andrew, Sinclair, Abeed, and Matt who were joined by Mike Foss, the president and CEO of Play by Play, a startup focused on live sports broadcasting. Mike shared his background in sports broadcasting and expressed gratitude for the partnership with Ball State University. Matt then provided his background in design and his experience working with ESPN. The group discussed the purpose of the meeting, which was to understand the goals for the Game Master and Ad Master sections of the project, with Shristi emphasizing the importance of aligning the new phase with the old build.
### Prediction Game Show Development

Matt introduced a prediction game show concept where players compete against the host for points, currently focusing on football, with no wagers involved. Abeed, based in the UK, shared his background in aerospace engineering and computer science, highlighting his experience in numerical simulations and consulting across various industries. Shristi and Matt discussed the need to provide a basic overview of the Game Master's core functionality, as some team members had not reviewed the app or repository. Matt mentioned having a tutorial available but faced technical difficulties sharing his screen during the meeting.
### Play-by-Play App Demo Overview

Matt demonstrated the Play-by-Play app, explaining its features for fans to predict game outcomes and earn points. He outlined various prediction options, including rushes, passes, touchdowns, and turnovers, as well as specific scenarios like punts, field goals, and kickoffs. Shristi and Abeed discussed the Game Master's role in managing the app, including cuing prediction buttons, executing play actions, and potentially using a Resync feature.
### Gaming Project Vision and Development

The team discussed the long-term vision for their gaming project, which includes developing computer vision and text-to-speech capabilities to automate game management. For the immediate future, they focused on creating an engaging gameplay experience for users, with plans to implement features like wildcard predictions and power-ups. The team decided to use Firebase as the backend for all applications, including the Game Master and Admin interfaces, at least for the initial phase. They also addressed an ongoing issue with resync problems, which needs to be resolved before the first game on October 4th. Shristi expressed interest in working on backend and database development, while Matt highlighted the urgency of fixing the resync issue.
### Live Streaming Synchronization Challenges

Abeed discussed challenges with synchronizing video feeds and event streams across different client devices during a live streaming session. He explained that there was a 15-20 second drift between video playback on different devices, which affected gameplay timing. To address this, Abeed suggested forcing a resync of the video player every minute or two, which would create a slight jerk in the video but ensure that predictions and video were in line. He also mentioned that more sophisticated techniques, such as speeding up playback or using animations to mask delays, could be implemented later.
### Code Testing and Project Management

The team discussed the implementation of code for testing and debugging, with a focus on meeting upcoming deadlines. Shristi agreed to connect with Dr. Ergin to clarify next steps and timeline for implementation, aiming to have a test ready by Tuesday. The group also addressed the need for project management tools, deciding to use GitHub issues and potentially add team members to relevant repositories. Michael emphasized the importance of meeting deadlines and maintaining accountability, highlighting the urgency of the project from a business perspective.
