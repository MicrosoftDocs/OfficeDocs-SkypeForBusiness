---
title:  New Teams for Web - Overview and prerequisites
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 12/11/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: sburkman
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about new Teams for Web - Overview and prerequisites
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# New Teams for Web - Overview and prerequisites

The new Teams for Web is reimagined from the ground up with performance in mind, providing a faster, simpler, and more flexible experience. The new Teams client installs and loads faster, letting you launch the app and join meetings more quickly, giving you more time to focus on the business tasks.

## New Teams for Web rollout schedule

General availability of New Teams for Web for Chrome and Microsoft Edge was announced earlier in November, and the following details provide further clarity on the timelines for the availability and update progress for New Teams for Web.

>[!Note]
>Education, Special Cloud, GCC, GCC-High, and DOD customer segments operate on separate timelines than what is presented here.

### Availability on Microsoft Edge and Chrome browsers on Windows and macOS

|Date                            |Availability|
|:-------------------------------|:-----------|
|Nov 15, 2023 to<br>Jan 15, 2024 |<ul><li>Chrome and Microsoft Edge users receive classic Teams for Web by default when navigating to https://teams.microsoft.com.<li>These users see a toggle to switch to new Teams for Web unless the [tenant’s upgrade policy](/microsoftteams/new-teams-deploy-using-policies?tabs=teams-admin-center#set-the-policies-to-upgrade-to-the-new-teams-client) is set to ‘Not enabled’.</li><li>Users who have switched to new Teams for Web can switch back to Classic Teams at any time.</li></ul>|
|Jan 15, 2024                    | <ul><li>Teams for Web begins honoring all [Teams upgrade policies](/microsoftteams/new-teams-deploy-using-policies). Changes to these policies affect both the web client and desktop client.</li><li>The policy **”Classic Teams as default”** continues providing the current experience where users receive classic Teams for Web with a toggle to update to new Teams for Web.</li><li>The policy **“New Teams as default”** automatically updates Web users to new Teams for Web as their default experience.</li><li>The policy **“Microsoft Controlled”** allows Microsoft to manage the updating of Web users to new Teams.<br>We anticipate first updating users in the public preview program and Targeted release program to new Teams for Web in stages beginning January 15, 2024. <br>We anticipate updating all regular users with the “Microsoft Controlled” policy afterwards, beginning January 29, 2024. <br>Microsoft will control how long these users may switch back to classic Teams. We anticipate retiring the switch-back option for or all users in April 2024 in following the overall timeline in [this article](teams-classic-client-end-of-availability.md).</li><li>The policy **“New Teams only”** will automatically update Web users to new Teams for Web as their only experience. We anticipate slowly rolling out this policy enforcement on web clients beginning April 8th, 2024.</li><li>The policy **“Not enabled”** will continue to restrict users to classic Teams with no toggle to update to new Teams through March 31, 2024.</li></ul> |
|After March 31, 2024            |<ul><li>Any classic Teams for Web users that haven’t updated to new Teams for Web will be automatically updated to new Teams along with desktop clients. [See this announcement for details.](/microsoftteams/new-teams-automatic-upgrade-announced) |

### Availability on Firefox and Safari browsers, and Linux

|Date                           |Availability                                                                                         |
|:------------------------------|:----------------------------------------------------------------------------------------------------|
|April 1 through April 15, 2024 |<ul><li>New Teams for Web is currently rolling out to general audiences for these clients:</li><li>New Teams for Web on Firefox browser on Windows, macOS, and Linux</li><li>New Teams for Web on Safari browser on macOS</li><li>Microsoft Edge and Chrome browsers with Progressive Web App (PWA) support on Linux</li></ul> |

## How to try new Teams: App Switcher

1. Navigate to the Teams web client at https://teams.microsoft.com using Microsoft Edge or Chrome browsers.
2. Select the **Try the new Teams** toggle on the upper-left corner of the app to switch to new Teams.

## Prerequisites

### Minimum Browser versions

New Teams for Web follows the same browser requirements as classic Teams for Microsoft Edge and Chrome Browsers:

- The browser must be configured to allow third-party cookies.
- The browser runs on a desktop computer.
- The browser is updated to one of the three most-recent versions of Microsoft Edge or Chrome.

The new Teams web client offers near feature parity with the new Desktop client thanks to a new, cross-client infrastructure.

## Features currently not available

The following notable features aren't available on new Teams or classic Teams clients:

- Simultaneous availability and notifications across multiple accounts and tenants.
- Popout windows for chat and channel content.
- Avatars and video background effects, except for background blur.

New Teams for Web supports the same features available on classic Teams for Web with the exception of the changes listed in [Features that are changing in the new Microsoft Teams](new-teams-whats-changing.md).

## Enhancements in new Teams

The following issues from classic Teams Web are now fixed in new Teams Web:

- Support for more than two concurrent Teams tabs.
- Screen reader challenges with notifications.
- Various stability and performance issues.
