---
title:  Known issues in the new Microsoft Teams desktop client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 01/03/2024
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

- PowerPoint Live Standout isn't yet available.
- Language-aware spell checking is currently not available in the new Teams. The team is focusing on this issue with a high priority. Check back for updates.
- On Windows, spell checking is limited to English (United States) dictionaries. Until this feature is fixed, users can disable spell checking from the settings page.
- Some spell checker suggestions for English can be inaccurate. A Windows fix is pending, with an estimated rollout date of January. Users can choose to disable spell checking from the settings page until then.
- Scheduling a Teams Live Event will redirect to the classic Teams web experience currently. By late March, scheduling a Teams Live Event will redirect to the new Teams web experience.
- Producing a Teams Live Event will be available in the new Microsoft Teams Desktop client in March. Until then, you need to switch back to classic Teams to produce a Teams Live Event.
- Users are unable to see the presence of other users under the Organization tab in 1:1 chats. Restart your new Teams client or browser window to resolve. Still an issue for offline contacts.
- New Teams client isn't respecting the date time formats set in the OS. This affects both 12h/24h time formatting and date formatting in the product. A fix is pending; check back for updates.
- Support for NDI, SDI, and ISO streaming of Teams media content.
- The app will crash if users hit enter instead of clicking the *Create* button after entering the team name in the team creation wizard.
- Newly created private channels won't show up in the left rail until the page is reloaded or users move to another screen and come back.
- The calendar icon will show an error message for users not licensed with Exchange Online. A fix to hide the calendar icon for these users is expected soon.
- Report a Problem is missing in the help menu for users in the public preview channel.
- Custom Announcement Backgrounds are only available in the AMER region. Pending availability of the full Designer backed AI capabilities in other regions, we're working to provide the option for users to upload their own images.
- [Cross Cloud Guest Access (CCGA) accounts](https://techcommunity.microsoft.com/t5/microsoft-teams-support/cross-cloud-meeting-amp-cross-cloud-guest-access-between-ww/ba-p/3990829) aren't yet shown on the Web client. Until this feature is available, users can use CCGA meeting-join links or navigate directly to the cloud-specific URL in a new tab.
- If using classic Teams for Web to open a [Cross Cloud Meeting (CCM)](https://techcommunity.microsoft.com/t5/microsoft-teams-support/cross-cloud-meeting-amp-cross-cloud-guest-access-between-ww/ba-p/3990829) link into a cloud where the user is opted into new Teams for web, the meeting join will fail. Until a fix is ready, users can navigate directly to the cloud-specific URL to join their meeting.
- [A website doesn't load in the new Teams desktop](/microsoftteams/troubleshoot/tabs/websites-not-loaded-new-teams).
- [The new Teams desktop app fails to render video](/microsoftteams/troubleshoot/meetings/new-teams-desktop-app-fail-render-video)
- Collaborative Notes is only available in public clouds.

## Issues specifically for the new Microsoft Teams for Education

>[!Note]
>Issues in the first section of this article also may affect EDU. If your issue isn't on either list, file a support ticket at: [**aka.ms/EduSupport**](https://aka.ms/edusupport).
>  
>The desktop clients will be updated as issues are fixed and functionality added. Check back here for the latest information.

- In some scenarios, the channel isn't deleted when a team owner selects delete channel. A fix is expected in the end of January.
  
- The Edit class team dialogue shows sensitivity labels but this isn't supported in class teams and a fix is expected in the end of January.

- Weekly digest mail settings are missing.

- When navigating to Teams from microsoft365.com, the top navigation bar isn't working as expected and both search and profile menu are missing. The plan is to fix this issue by February.</br>**Workaround:** Use a taskbar shortcut or navigate directly to *teams.microsoft.com* to avoid the issue.

- Students are able to reply to posts by bots like the Assignment bot in the General channel even if channel moderation is enabled.</br>**Workaround:** Publish assignments in another channel where channel moderation is enabled or in channel settings where you have enabled **Allow bots to submit channel messages**.

- In some scenarios, students or teachers in your tenant, with the correct policy assigned, still might not be automatically moved to New Teams. Encourage them to use the toggle to switch to New Teams.

- If the toggle to switch to New Teams is greyed out with an error message, see: [**Troubleshooting installation issues**](new-teams-troubleshooting-installation.md).
- Support for external Shared Channels when using *Grid view* isn't available.</br>**Workaround:** Use *List view*.  

## What features are changing?

As we improved the client, the experience also improved to align with similar features. Learn more: [**Features that are changing in the new Microsoft Teams**](new-teams-whats-changing.md)
