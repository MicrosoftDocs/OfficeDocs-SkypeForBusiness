---
title: Deploy Microsoft Teams for Surface Hub
author: ChuckEdmonson
ms.author: chucked
manager: serdars
ms.date: 12/04/2018
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: jatpatel
description: Configure admin settings for Microsoft Teams for Surface Hub.
localization_priority: Normal
search.appverid: MET150
ms.custom:
- Devices
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Deploy Microsoft Teams for Surface Hub
======================================

Before you install Teams for Surface Hub, be sure to do the following:

 □ Make sure hardware, operating system, and other requirements are met. For more information, see the [Microsoft Surface Hub admin guide](https://docs.microsoft.com/surface-hub/).<br>
 □ Make sure the minimum operating system update required for Teams is installed - [KB4343889](https://support.microsoft.com/help/4343889).<br>
 □ Assign a Teams license to the Hub device account.<br>
 □ If you are transitioning from Skype for Business Online, confirm that a Teams license is assigned to the user.

## Install Teams for Surface Hub from the Microsoft Store 

These instructions are for installing Teams for Surface Hub from the Microsoft Store. 
 
1. Start the Microsoft Store:<br>
   a. Tap **Start** > **All Apps** > **Settings**.<br> 
   b. Tap **Surface Hub Device account, management**.<br>
   c. On the left, tap the **Apps & Features** tab.<br> 
   d. On the right, tap the **Open Store** button. 
2. From the Microsoft Store, search for *Microsoft Teams*. The **Microsoft Teams for Surface Hub** will be displayed. Tap the **Get the app** button to install.  
3. When the installation is complete, restart the Surface Hub. 

> [!NOTE]
> Do not tap **Launch** from the Store listing page.

## Make Teams the default calling and meetings application
 
There are two options for configuring the default calling and meetings application policy: 

- **Option 1**: Configure via USB key. 
- **Option 2**: Configure via MDM such as Intune.
 
### Option 1: Configure via USB key 
 
The packages can be found on this [download page](https://1drv.ms/f/s!ArcnbnREun0Vnp9Wps9MlWB-UJZw3g). Pick the appropriate one for the package that you're planning to install and copy it to a USB key. The correct .ppkg file to use depends on the default application policy you'd like to apply as follows: 

|Number  |Description  |
|---------|---------|
|0     | Skype preferred app on the Start Screen, Teams Meetings available        |
|1     | Teams preferred app on the Start Screen, Skype Meetings available        |
|2     | Teams exclusive app on the Start screen (Skype app not available)        |
 
1. Attach the USB key to the Surface Hub device. 
2. Open the **Settings** app on a Surface Hub device. 
3. Open **Surface Hub Device Account Management**.
4. Open **Device Management**. 
5. Click **Add or Remove a provisioning package**. 
6. Click **Add Package**.
7. Select the **Removable Media** option from the drop-down menu. 
8. Add the appropriate <strong>TeamsRTMMode*.ppkg</strong> package that was previously copied to the USB key. 
9. Restart the Surface Hub device. 
10. After the device restarts, you should be able to start the Teams app from the Start screen and join a meeting from the calendar. 

### Option 2: Configure via MDM such as Intune 

Use the following to configure the default calling and meetings application policy via Intune. Also see the blog, [Deploy the Microsoft Teams for Surface Hub app using Intune](https://y0av.me/2018/07/16/deploy-the-microsoft-teams-for-surface-hub-app-using-intune/).

|Setting   |Value    |Description    |
|----------|---------|---------|
|Path      | ./Vendor/MSFT/SurfaceHub/Properties/SurfaceHubMeetingMode        |
|Data Type | integer (0-2)   |0 - Skype preferred app on the Start Screen, Teams Meetings available<br>1 - Teams preferred app on the Start Screen, Skype Meetings available<br>2 - Teams exclusive app on the Start screen (Skype app not available) |
|Operations| Get, Set        |

|Setting   |Value    |
|----------|---------|
|Path      | ./Vendor/MSFT/SurfaceHub/Properties/VtcAppPackageId        |
|Data Type | string - set string to Teams application package ID as **Microsoft.MicrosoftTeamsforSurfaceHub_8wekyb3d8bbwe!Teams** |
|Operations| Get, Set        |

Restart the Surface Hub device. After the device restarts, you should be able to start the Teams app from the Start screen and join a meeting from the calendar.

