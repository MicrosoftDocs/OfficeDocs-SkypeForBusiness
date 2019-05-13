---
title: "Use the Microsoft Teams Rooms recovery tool"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.reviewer: davgroom
ms.date: 4/17/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
ms.collection: M365-voice
localization_priority: Normal
description: "This article discusses how to use the recovery tool for Microsoft Teams Rooms, which you would use to bring an out of date system into a supported state."
---

# Use the Microsoft Teams Rooms recovery tool
 
This article discusses how to use the recovery tool for Microsoft Teams Rooms, which you would use to bring an out of date system into a supported state. You would use this tool when the Microsoft Teams Rooms console shows a "system config out of date" error.
  

<a name="Prerequisites"> </a>  
## Prerequisites

Download the latest [Microsoft Teams Rooms installation package](https://go.microsoft.com/fwlink/?linkid=851168) and extract it to a USB memory stick or network share accessible to the Microsoft Teams Rooms device.

You may also need to install [KB4089848](http://download.windowsupdate.com/d/msdownload/update/software/updt/2018/03/windows10.0-kb4089848-x64_db7c5aad31c520c6983a937c3d53170e84372b11.msu).

<a name="Windows-ver"> </a>
## Verify Windows Version 

1. Login to an admin account by going to **Settings> Windows Setting> Admin Sign In** from the Microsoft Teams Rooms device. This option brings you to the login screen.
2. Sign into an admin account, the default admin account being `admin` with the password `sfb`.
3. Click on the start menu and type `winver.exe` into the search box and click **Run Command* on the result.
4. Make note of the number after 'Version' on the second line of the info pane.

>[!NOTE]
>If the Version shown is 1607 or earlier, follow the steps in the <a href="#Windows-up">Update Windows before recovery</a> steps before proceding to the <a href="#Perform">Perform a recovery</a> steps. If the Version shown is greater than 1607, follow only the steps in <a href="#Perform">Perform a recovery</a>.

<a name="Windows-up"> </a>
## Update Windows before recovery (if needed)

1. While still logged in as an admin user, launch an elevated Powershell prompt.
2. Run the command `Remove-Item -Path 'c:\Recovery\OEM\$oem$\$1\Rigel' -Force -Recurse`.
3. Run Windows Update and install the update for Windows 1709.
4. After the update to 1709 is complete sign back into admin account and install [KB4089848](http://download.windowsupdate.com/d/msdownload/update/software/updt/2018/03/windows10.0-kb4089848-x64_db7c5aad31c520c6983a937c3d53170e84372b11.msu). The update may be done from the link or using Windows Update.
5. As an optional step, install any additional updates available from Windows Update.

<a name="Perform"> </a>
## Perform a recovery

1. Sign in to the admin account on your Microsoft Teams Rooms device, and launch an elevated command prompt.
2. Verify from the Microsoft Teams Rooms device that you are able to access the `RecoveryTool.ps1` file, which is included in the files extracted from the Microsoft Teams Rooms installation package. The kit can be found on the network share or USB drive used when preparing prerequisites.
3. Run the Powershell.exe command `-ExecutionPolicy Unrestricted -File "<path to RecoveryTool.ps1>"`.
4. When prompted by the script select option `1:"Repair System"`.
5. Upon completion, reboot the Microsoft Teams Rooms device. It will reboot again automatically and come up fully recovered the second time.



<a name="See"> </a>  
## See also
 
[Microsoft Teams Rooms help](https://support.office.com/en-us/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Manage Microsoft Teams Rooms](skype-room-systems-v2.md)
