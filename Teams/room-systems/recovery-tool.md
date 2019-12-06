---
title: "Use the Microsoft Teams Rooms recovery tool"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.reviewer: sohailta
ms.date: 4/17/2018
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: M365-voice
localization_priority: Normal
description: "This article discusses how to use the recovery tool for Microsoft Teams Rooms, which you would use to bring an out of date system into a supported state."
---

# Use the Microsoft Teams Rooms recovery tool
 
This article discusses how to use the recovery tool for Microsoft Teams Rooms, which you would use to bring an out of date system into a supported state. This tool should be applied when either the Microsoft Teams Rooms console shows a "system config out of date" error, or prior to performing a push button reset [factory restore](https://docs.microsoft.com/en-us/microsoftteams/room-systems/room-systems-v2-operations#microsoft-teams-rooms-reset-factory-restore). 
# Prerequisites 
Download the latest [Microsoft Teams Rooms installation package](https://go.microsoft.com/fwlink/?linkid=851168) and extract it to a USB memory stick or network share accessible to the Microsoft Teams Rooms device.

Note

Extracting the files from the MSI can be accomplished by many means. Any mechanism that extracts all the files and preserves their directory structure is acceptable. One such way is to use the command `msiexec /qn PathToMsi /qb TARGETDIR=PathToTarget` where `PathToMsi` represents the full path to the Microsoft Teams Room installation package, and `PathToTarget` represents the full path to the folder you would like the files extracted to. 

# Running the tool 
1) Sign in to the admin account on your Microsoft Teams Rooms device, and launch an elevated command prompt. 
2) Verify from the Microsoft Teams Rooms device that you are able to access the `RecoveryTool.ps1 file`, which is included in the files extracted from the Microsoft Teams Rooms installation package. The kit can be found on the network share or USB drive used when preparing prerequisites. 
3) Run `powershell.exe -ExecutionPolicy Unrestricted -File "<path to RecoveryTool.ps1>"`. 
4) If you are performing a factory restore… 
   - When prompted by the script select option 2:`"Reset"`. 
   - If BitLocker is on, follow the instructions provided at the end of the script output to disable it. 
   - Perform the factory restore. 
      - Open the **Settings** app, and select **Update & Security** 
      - Navigate to the **Recovery** tab. 
      - Beneath **Reset this PC**, select **Get started** 
      - Select **Remove everything**, then **Next** and **Reset** 
      - The system will reboot multiple times. When the reset is complete, the system will be at the Windows OOBE screen 
5) If you are repairing an “out of date” system… 
    - When prompted by the script select option 1:`"Repair"`. 
    - Upon completion, reboot the Microsoft Teams Rooms device. It will reboot again automatically and come up fully recovered the second time. 
 
Note

There is a known issue where the Microsoft Teams Rooms can become unusable if the  **Keep my files - Removes Apps and settings, but keeps your personal files** option is selected during the Windows Reset process. Do <i>not</i> use this option. 

## See also
 
[Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Manage Microsoft Teams Rooms](skype-room-systems-v2.md)
