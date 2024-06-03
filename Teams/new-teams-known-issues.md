---
title:  Known issues in the new Microsoft Teams desktop client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 05/31/2024
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: microthk
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about any known issues for the new Microsoft Teams client. 
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Known issues for new Microsoft Teams

- Language-aware spell checking is currently not available in the new Teams. The team is focusing on this issue with a high priority. Check back for updates.
- New Teams client isn't respecting the date time formats set in the OS. This issue affects both 12h/24h time formatting and date formatting in the product. A fix is pending; check back for updates.
- The app will crash if users hit enter instead of clicking the *Create* button after entering the team name in the team creation wizard.
- The calendar icon will show an error message for users not licensed with Exchange Online. A fix to hide the calendar icon for these users is expected soon.
- [A website doesn't load in the new Teams desktop](/microsoftteams/troubleshoot/tabs/websites-not-loaded-new-teams).
- [The new Teams desktop app fails to render video](/microsoftteams/troubleshoot/meetings/new-teams-desktop-app-fail-render-video).
- Collaborative Notes is only available in public clouds, and not in EDU (Academic SKUs).
- Scheduling a Teams Live Event (TLE) redirects to the classic Teams web experience. This feature will continue to work even after the deprecation of classic Teams.
- When editing a TLE on the web, users can't use the **Join** and **Chat** buttons. Selecting these buttons doesn't take the user to the join or chat experiences.
- When editing a TLE on the web, users can't use the **Manage live event resources** link at the bottom of the page. Selecting the link redirects the user to a different page. Resources for the event, can be found at the top of the page.
- The **Manage live event resources** link in the calendar invite doesn't work outside of Teams. Users must open the invite in Teams calendar to edit the session and access event resources.
- If a user closes a TLE session on the web, the next time they open Teams on the web, Teams might try and relaunch the last TLE event the user was in.
- The app will crash on startup with the error APPLICATION_FAULT_c06d007e_PvDSSource64.ax if the Pleora Technologies eBUS SDK is installed. Update to the latest version of the SDK or uninstall.
- Town Halls do not yet support web users on Firefox or Safari browsers.

## Issues specifically for the new Microsoft Teams for Education

> [!NOTE]
> Issues in the first section of this article also may affect EDU. If your issue isn't on either list, file a support ticket at: [**aka.ms/EduSupport**](https://aka.ms/edusupport).
>
> The desktop clients will be updated as issues are fixed and functionality added. Check back here for the latest information.

We currently have no EDU-specific features, but this may change.

## What features are changing?

As we improved the client, the experience also improved to align with similar features. Learn more: [**Features that are changing in the new Microsoft Teams**](new-teams-whats-changing.md)
