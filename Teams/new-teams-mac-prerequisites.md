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
description: Learn about any known issues for the new Microsoft Teams desktop client for the Mac
appliesto: 
- Microsoft Teams
ms.localizationpriority: high

---
# New Teams for Mac - Installation and prerequisites




## How to try new Teams? – App Switcher 

1. Launch the Teams app and turn on “Try the new Teams” toggle on the upper-left corner of the desktop app to switch to new Teams. Note that you should be running: 

2. MacOS Big Sur (11) and above (including Monterey (12) and Ventura (13)) 

3. Opt-in by selecting the “Try the new Teams” toggle and hit “Get it now”, and if you ever need to switch back, just flip the toggle 

 
>[!Note]
>This experience is currently optimized for non-EDU users. If you are an EDU user, you will see the App switcher and are welcome to try it out, but we do not recommend you use it for primary scenarios yet.


## Prerequisites

### Minimum Mac and Teams versions 

- You must be running MacOS Big Sur (11) or above (including Monterey (12) and Ventura (13)) 

- To see the “Try the new Teams” toggle, your current Teams app must be running version 23182.303.2215.7823 or higher. If you are at a lower version, click on the overflow menu (…) and click on check for updates, update, and restart your app. If you still do not see the App Switcher, please Report a Problem.  

- To install the new Teams client, the user needs admin privileges for their computer. If the user does not have admin privileges, admins can user their MDM (or whatever other way they deploy and install software on devices without admin privileges) and use this PKG.  

 

### Turn ON System Notification 

After installing the new client, if users do not choose to Allow Notifications with the initial macOS Alert about notifications settings, then users must turn on the "Allow Notifications” from system settings  

1. Open macOS System Preferences. 
2. Go to Notifications & Focus > Under App Notifications, select Microsoft Teams. 
3. Switch the “Allow notifications” toggle to turn on notifications 

:::image type="content" source="media/new-teams-mac-notifications.png" alt-text="new teams for mac notifications"::: 


### Turn on Screen Sharing 

Users can enable screen sharing for sharing content on call and in meetings using the regular in-app flow when they first try to screenshare, but this will require that they restart Teams so the user will need to drop from the meeting. Alternatively, users can turn on permissions for screen recording under system settings. 
For Monterey OS: 

1. Open macOS System Preferences. 
2. Go to Security & Privacy > Privacy tab > Screen Recording. 
3. Select the **+** sign to add Microsoft Teams (work Preview) to allow recording content of your screen.

 :::image type="content" source="media/new-teams-mac-security.png" alt-text="new teams mac security page":::

 
## For Ventura OS: 
 
1. Go to Privacy & Security > Screen Recording.  
2. Switch the toggle for Microsoft Teams (work preview) to Allow recording of the content of your screen.   

:::image type="content" source="media/new-teams-mac-screen-recording.png" alt-text="new teams mac screen recording page":::


## Troubleshooting and error handling

### App Switcher Toggle

- Relaunch your current client before turning the “Try the new Teams” toggle ON to ensure that you have latest changes. Also, if there is any Windows update pending, please install them before you try new Teams.

- If you’re not seeing the toggle for new Teams, please make sure you have the minimum required versions for Mac and Teams
  - MacOS Big Sur (11) or above (including Monterey (12) and Ventura (13)) and
  - Microsoft Teams (work or school) version 23182.303.2215.7823  or higher. 

- After you successfully switched to new Teams, if you can't find the toggle on the top left to switch between new Teams and Microsoft Teams (work or school), you can start the version you want by searching in Launchpad for Teams.   
 
:::image type="content" source="media/new-teams-mac-switch-using-launchpad.png" alt-text="switchusing launchpad":::

## How to uninstall new Teams Client

You can uninstall the new Teams client just like any other Mac app.

### How to clear cache
1.	Command + Space and enter Terminal.
2.	rm -rf ~/Library/Group Containers/UBF8T346G9.com.microsoft.teams
3.	rm -rf ~/Library/Containers/com.microsoft.teams2


## Features currently not available in new Teams for Mac
 
All the features available in new Teams Windows client are supported on Mac client except:

- Cameo (weather person) in PPT
- Green Screen
- NDI   

## Enhancements in new Teams

Below issues from classic Teams are now fixed in new Teams

- CMD+Tab issue
- Mac Native Shortcuts for text editing
- Call notifications not coming through when in Full-Screen
