---
ms.date: 03/17/2018
title: "Manage conference join and leave announcements in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: cb09f9c2-c6dc-4083-b45a-8b6773341373
description: "Summary: Learn how to manage conference join and leave announcements in Skype for Business Server."
---

# Manage conference join and leave announcements in Skype for Business Server
 
**Summary:** Learn how to manage conference join and leave announcements in Skype for Business Server.
  
When dial-in users join or leave a conference, the Conferencing Announcement application can announce their entrance or exit by playing a tone or saying their names. You can change how announcements work by using Skype for Business Server Management Shell and the **Set-CsDialinConferencing** cmdlet with the following parameters:
  
- EnableNameRecording - Determines whether anonymous participants are asked to record their name before entering the conference. The default value is "$true," which means that anonymous participants are prompted to state their name when joining a conference. (Authenticated participants don't record their name because their display name is used instead.)
    
- EntryExitAnnouncementsEnabledByDefault - Indicates whether announcements are turned on or off by default. The default value is "$false," which means that by default there are no announcements when participants join or leave a conference. The meeting organizer can override this setting when scheduling a meeting.
    
- EntryExitAnnouncementsType - Indicates the action taken whenever a participant joins or leaves a conference for which announcements are enabled. The default value is "UseNames," which means there's an announcement similar to the following: "Ken Myer has joined the conference" when announcements are turned on.
    
You can configure these settings at the global scope or at the site scope. Settings configured at the site scope take precedence over settings configured at the global scope.
   

### To modify the conference join and leave announcement behavior

1. Sign in to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the Cs-ServerAdministrator or CsAdministrator role.
    
2. Start the Skype for Business Server Management Shell: Select **Start**, select **All Programs**, select **Skype for Business 2015**, and then select **Skype for Business Server Management Shell**.
    
3. Run the following at the command prompt:
    
   ```PowerShell
   Get-CsDialinConferencingConfiguration
   ```

This cmdlet retrieves information about whether participants are required to record their name when joining a conference and how Skype for Business Server responds when participants join or leave a dial-in conference.
    
4. Run the following at the command prompt:
    
   ```PowerShell
   Set-CsDialinConferencingConfiguration -Identity <identity of dial-in conferencing settings to be modified>
   [-EnableNameRecording <$true | $false>]
   [-EntryExitAnnouncementsEnabledByDefault <$true | $false>]
   [-EntryExitAnnouncementsType <UseNames | ToneOnly]
   ```

In the following example, settings are configured at the site scope for Redmond. Announcements are turned on, but participants aren't prompted to say their name when they join a conference. A tone is played when participants enter or leave a conference:
  
```PowerShell
Set-CsDialinConferencingConfiguration -Identity site:Redmond
-EnableNameRecording $false
-EntryExitAnnouncementsEnabledByDefault $true
-EntryExitAnnouncementsType ToneOnly
```

For more information, including syntax and a complete list of parameters, see [Set-CsDialInConferencingConfiguration](/powershell/module/skype/set-csdialinconferencingconfiguration?view=skype-ps).

