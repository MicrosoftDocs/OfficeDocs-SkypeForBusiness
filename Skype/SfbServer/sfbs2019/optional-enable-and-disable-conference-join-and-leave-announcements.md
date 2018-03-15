---
title: "(Optional) Enable and disable conference join and leave announcements in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c9529568-e66c-48d8-aef2-9072f9c336ff
description: "When dial-in users join or leave a conference, the Conferencing Announcement application can announce their entrance or exit by playing a tone or saying their names. You can change how announcements work by running cmdlets. This step is optional."
---

# (Optional) Enable and disable conference join and leave announcements in Lync Server 2013
[]
When dial-in users join or leave a conference, the Conferencing Announcement application can announce their entrance or exit by playing a tone or saying their names. You can change how announcements work by running cmdlets. This step is optional.
  
### To modify the conference join and leave announcement behavior

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-ServerAdministrator** or **CsAdministrator** role. 
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run the following at the command prompt:
    
  ```
  Get-CsDialinConferencingConfiguration
  ```

    This cmdlet retrieves information about whether participants are required to record their name when joining a conference and how Lync Server responds when participants join or leave a dial-in conference.
    
4. Run the following at the command prompt:
    
  ```
  Set-CsDialinConferencingConfiguration -Identity <identity of dial-in conferencing settings to be modified>
  [-EnableNameRecording <$true | $false>]
  [-EntryExitAnnouncementsEnabledByDefault <$true | $false>]
  [-EntryExitAnnouncementsType <UseNames | ToneOnly]
  ```

    **EnableNameRecording** Determines whether anonymous participants are asked to record their name before entering the conference. The default value is "$true," which means that anonymous participants are prompted to state their name when joining a conference. (Authenticated participants do not record their name because their display name is used instead.) 
    
    **EntryExitAnnouncementsEnabledByDefault** Indicates whether announcements are turned on or off by default. The default value is "$false," which means that by default there are no announcements when participants join or leave a conference. The meeting organizer can override this setting when scheduling a meeting. 
    
    **EntryExitAnnouncementsType** Indicates the action taken whenever a participant joins or leaves a conference for which announcements are enabled. The default value is "UseNames," which means there is an announcement similar to the following: "Ken Myer has joined the conference" when announcements are turned on. 
    
    You can configure these settings at the global scope or at the site scope. Settings configured at the site scope take precedence over settings configured at the global scope.
    
    For example:
    
  ```
  Set-CsDialinConferencingConfiguration -Identity site:Redmond
  -EnableNameRecording $false
  -EntryExitAnnouncementsEnabledByDefault $true
  -EntryExitAnnouncementsType ToneOnly
  ```

    In this example, settings are configured at the site scope for Redmond. Announcements are turned on, but participants are not prompted to say their name when they join a conference. A tone is played when participants enter or leave a conference.
    

