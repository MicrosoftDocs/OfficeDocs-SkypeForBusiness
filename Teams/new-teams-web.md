---
title:  New Teams for Web - Overview and prerequisites
ms.author: jhendr
author: JoanneHendrickson
manager: jtremper
ms.topic: article
ms.date: 12/11/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: smylavarapu
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


## New Teams on Web rollout schedule
General availability of New Teams on web for Chrome and Microsoft Edge was announced earlier in November, and the following details provide further clarity on the timelines for the availability and update progress for New Teams on Web. 

>[!Note] 
>Education, Special Cloud, GCC, GCC-High, and DOD customer segments operate on separate timelines than what is presented here.

### Availability on Microsoft Edge and Chrome browsers

|Date|Availability| 
|:-----|:-----| 
|Nov 15, 2023 to<br>Jan 15, 2024|<ul><li>Chrome and Microsoft Edge users receive classic Teams on Web by default when navigating to https://teams.microsoft.com.<li>These users see a toggle to switch to New Teams on web unless the [tenant’s upgrade policy](/microsoftteams/new-teams-deploy-using-policies?tabs=teams-admin-center#set-the-policies-to-upgrade-to-the-new-teams-client) is set to ‘Not enabled’.</li><li>Users who have switched to New Teams on web can switch back to Classic Teams at any time.</li></ul>| 
|Jan 15, 2024| <ul><li>Teams on web begins honoring all [Teams upgrade policies](microsoftteams/new-teams-deploy-using-policies?tabs=teams-admin-center). Changes to these policies affect both the web client and desktop client.</li><li>The policy **”Classic Teams as default”** continues providing the current experience where users receive classic Teams on Web with a toggle to update to New Teams on web. Users who switch to New Teams on web can switch back to Teams Classic through March 31, 2024.</li><li>The policy **“New Teams as default”** automatically updates Web users to New Teams on Web as their default experience. Users on New Teams on Web can switch back to Teams Classic through March 31, 2024.</li><li>The policy **“Microsoft Controlled”** allows Microsoft to manage the updating of Web users to New Teams.<br>We anticipate first updating users in the public preview program and Targeted release program to New Teams on Web in stages beginning January 15, 2024. <br>We anticipate updating all regular users with the “Microsoft Controlled” policy afterwards, beginning January 29, 2024. <br>Microsoft will control how long these users may switch back to Teams classic. We anticipate retiring the switch-back option for preview-program users on January 29, 2024, and for regular users on February 26, 2024.</li><li>The policy **“Not enabled”** will continue to restrict users to Teams Classic with no toggle to update to new Teams through March 31, 2024.</li></ul>|
|After March 31, 2024|<ul><li>Any classic Teams on Web users that haven’t updated to new Teams on web will be automatically updated to new Teams along with desktop clients. [See this announcement for details.](/microsoftteams/new-teams-automatic-upgrade-announced)

### Availability on Firefox, Safari, and Progressive Web App (PWA)
|Date|Availability| 
|:-----|:-----|
|1st Quarter, 2024|<ul><li>New Teams on web for Firefox and Safari.</li><li>Progressive Web App (PWA) support on Linux|

More-specific dates and details for Firefox, Safari, and PWA on Linux will be shared at a later date. 

## How to try new Teams: App Switcher  

1. Navigate to the Teams web client at https://teams.microsoft.com using Microsoft Edge or Chrome browsers. 
2. Select the **Try the new Teams** toggle on the upper-left corner of the app to switch to new Teams. 


## Prerequisites 

### Minimum Browser versions 

New Teams for Web follows the same browser requirements as classic Teams for Microsoft Edge and Chrome Browsers: 
  
- The browser must be configured to allow third-party cookies 
- The browser runs on a desktop computer 
- The browser is updated to one of the three most-recent versions of Microsoft Edge or Chrome 

  
The new Teams web client offers near feature parity with the new Desktop client thanks to a new, cross-client infrastructure.  
  
## Features currently not available 
  
The following notable features aren't available on new Teams or classic Teams clients: 
  
- Simultaneous availability and notifications across multiple accounts and tenants 
- Popout windows for chat and channel content 
- Avatars and video background effects, except for background blur 
  
## Enhancements in new Teams 

The following issues from classic Teams Web are now fixed in new Teams Web: 
  
- Support for more than two concurrent Teams tabs 
- Screen reader challenges with notifications 
- Various stability and performance issues 