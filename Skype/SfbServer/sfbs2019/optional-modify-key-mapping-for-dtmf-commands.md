---
title: "(Optional) Modify key mapping for DTMF commands in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d753b78d-400c-4df2-957f-e7576b2019c2
description: "Dial-in conferencing users can press keys on the telephone keypad to perform dual-tone multi-frequency (DTMF) commands. DTMF commands enable users who dial in to a conference to control conference settings (such as muting and unmuting themselves or locking and unlocking the conference) by using the keypad on their telephone. You can use cmdlets to modify the keys used for the DTMF commands. This step is optional."
---

# (Optional) Modify key mapping for DTMF commands in Lync Server 2013
[]
Dial-in conferencing users can press keys on the telephone keypad to perform dual-tone multi-frequency (DTMF) commands. DTMF commands enable users who dial in to a conference to control conference settings (such as muting and unmuting themselves or locking and unlocking the conference) by using the keypad on their telephone. You can use cmdlets to modify the keys used for the DTMF commands. This step is optional.
  
> [!NOTE]
> For details about these cmdlets and the possible DTMF options, see Lync Server Management Shell documentation or Lync Server Management Shell command-line Help. 
  
### To modify the key mapping of DTMF commands

1. Log on to the computer as a member of the **RTCUniversalServerAdmins** group, or as a member of the **Cs-ServerAdministrator** or **CsAdministrator** role. 
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run the following at the command prompt:
    
  ```
  Get-CsDialinConferencingDtmfConfiguration
  ```

    This cmdlet returns the DTMF settings used for dial-in conferencing.
    
4. Run the following cmdlet and specify the key to be pressed for each option that you want to change:
    
  ```
  Set-CsDialinConferencingDtmfConfiguration [-Identity <global or site collection to be changed>]
  [-AdmitAll <default key is 8>] [-AudienceMuteCommand <default key is 4>]
  [-CommandCharacter <* (default) | #>] [-EnableDisableAnnouncementsCommand <default key is 9>]
  [-HelpCommand <default key is 1>] [-LockUnlockConferenceCommand <default key is 7>]
  [-MuteUnmuteCommand <default key is 6>] [-PrivateRollCallCommand <default key is 3>]
  ```

    This cmdlet modifies the DTMF settings used for dial-in conferencing.
    
    For example:
    
  ```
  Set-CsDialinConferencingDtmfConfiguration -EnableDisableAnnouncementsCommand 4 -AudienceMuteCommand 9
  ```

    This example swaps the key that is pressed to enable or disable announcements and the key that is pressed to mute and unmute all participants. Because no Identity is specified, these changes apply to the global DTMF settings.
    
5. (Optional) To create additional sets of DTMF commands for specific sites, use the **New-CsDialinConferencingDtmfConfiguration** cmdlet with a site identity. When you create new DTMF settings for sites, the site settings take precedence over the global settings. For details, see Lync Server Management Shell documentation or Lync Server Management Shell command-line Help. 
    

