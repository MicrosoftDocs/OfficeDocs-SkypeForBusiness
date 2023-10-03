---
title:  Install and prerequisites for the Microsoft new Teams for the Mac
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 08/31/2023
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
description: Learn about installing and meeting prerequisites for the new Microsoft Teams desktop client for the Mac
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# New Teams for Mac - Overview and prerequisites

>[!Note]
> The features described in this article are available to [**Teams Public preview**](/microsoftteams/public-preview-doc-updates) and [**Microsoft 365 Targeted release**](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide#targeted-release) customers only. Features and content are subject to change. Check back for updates.


The new Teams for Mac has been reimagined from the ground up with performance in mind, providing a faster, simpler, and more flexible experience. The new Teams client installs and loads faster, letting you launch the app and join meetings more quickly, giving you more time to focus on the business tasks.

The new Teams ensures more efficient use of device resources. Whether you have users on multiple accounts or tenants, the new Teams can help eliminate the silos and bring them together in one place, giving them more extensibility and scale.


## How to try new Teams: App Switcher 

- Launch the Teams app and turn on **Try the new Teams** toggle on the upper-left corner of the desktop app to switch to new Teams. 
- Opt-in by selecting the **Try the new Teams** toggle and select “Get it now”.  To switch back, just flip the toggle.

>[!Note]
>This experience is currently optimized for non-EDU users. If you are an EDU user, you will see the App switcher and are welcome to try it out, but we do not recommend you use it for primary scenarios yet.


## Prerequisites

### Minimum Mac and Teams versions 

- You must be running macOS Big Sur (11) or higher, including macOS Monterey (12) and macOS Ventura (13). 

- To see the “Try the new Teams” toggle, your current Teams app must be running version 1.6.00.12303 or higher. If you are at a lower version, select on the overflow menu (…) and select on check for updates, update, and restart your app. If you still don't see the App Switcher, please Report a Problem.  

- To install the new Teams client, the user needs admin privileges for their computer. If the user doesn't have admin privileges, admins can user their MDM (or whatever other way they deploy and install software on devices without admin privileges) and use this [**PKG**](https://statics.teams.cdn.office.net/production-osx/enterprise/webview2/lkg/MicrosoftTeams.pkg).  


### Turn ON System Notification 

After installing the new client, if users don't choose to Allow Notifications with the initial macOS Alert about notifications settings, then users must turn on the "Allow Notifications” from system settings  

1. Open macOS System Preferences. 
2. Go to Notifications & Focus > Under App Notifications, select Microsoft Teams. 
3. Switch the “Allow notifications” toggle to turn on notifications 

:::image type="content" source="media/new-teams-mac-notifications.png" alt-text="new teams for mac notifications"::: 


### Turn on Screen Sharing 

Users can enable screen sharing for sharing content on call and in meetings using the regular in-app flow when they first try to screen share, but this requires they restart new Teams. The user needs to drop from the meeting. Alternatively, users can turn on permissions for screen recording under system settings. 
For Monterey OS: 

1. Open macOS System Preferences. 
2. Go to Security & Privacy > Privacy tab > Screen Recording. 
3. Select the **+** sign to add Microsoft Teams (work Preview) to allow recording content of your screen.

 :::image type="content" source="media/new-teams-mac-security.png" alt-text="new teams mac security page":::

 
#### For macOS Ventura
 
1. Go to Privacy & Security > Screen Recording.  
2. Switch the toggle for Microsoft Teams (work preview) to Allow recording of the content of your screen.   

:::image type="content" source="media/new-teams-mac-screen-recording.png" alt-text="new teams mac screen recording page":::


## Troubleshooting and error handling

### App Switcher Toggle

- Relaunch your current client before turning the “Try the new Teams” toggle ON to ensure that you have latest changes.

- If you’re not seeing the toggle for new Teams, make sure you have the minimum required versions for Mac and Teams:

  - macOS Big Sur (11) or above (including macOS Monterey (12) and macOS Ventura (13) and
  - Microsoft Teams (work or school) version 1.6.00.12303 or higher. 

- After you successfully switched to new Teams, if you can't find the toggle on the top left to switch between new Teams and Microsoft Teams (work or school), you can start the version you want by searching in Launchpad for Teams.   
 
:::image type="content" source="media/new-teams-mac-switch-using-launchpad.png" alt-text="switchusing launchpad":::

## How to uninstall new Teams Client

You can uninstall the new Teams client just like any other Mac app.

### How to clear cache
1.	Command + Space and enter Terminal.
2.	rm -rf ~/Library/Group Containers/UBF8T346G9.com.microsoft.teams
3.	rm -rf ~/Library/Containers/com.microsoft.teams2


## Features currently not available
 
All the features available in new Teams Windows client are supported on Mac client except:

- Cameo (weather person) in PPT
- Green Screen
- NDI   

## Enhancements in new Teams

Below issues from classic Teams are now fixed in new Teams

- CMD+Tab issue
- Mac Native Shortcuts for text editing
- Call notifications not coming through when in Full-Screen
