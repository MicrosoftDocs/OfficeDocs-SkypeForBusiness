---
title: "Managing users and user account properties in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.assetid: 5d13ab15-0e12-4bd0-a970-f130de980404

description: "The following cmdlets manage Skype for Business Online user accounts."
---

# Managing users and user account properties in Skype for Business Online
[]
The following cmdlets manage Skype for Business Online user accounts.
  
|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsOnlineUser](get-csonlineuser.md) <br/> |Returns information about users who have accounts homed with your Skype for Business Online tenant.  <br/> |
|[Get-CsUserAcp](get-csuseracp.md)          [Remove-CsUserAcp](remove-csuseracp.md)          [Set-CsUserAcp](set-csuseracp.md) <br/> |Enables you to assign, modify, or unassign an audio conferencing provider to individual users.  <br/> An audio conferencing provider is a third-party company that provides organizations with conferencing services, including high-end services such as live translation, transcription, and live per-conference operator assistance.  <br/> These cmdlets do not return information about the audio providers available to be assigned to those users. For that information, run this command instead:  <br/> ```Get-CsAudioConferencingProvider```|
   
> [!CAUTION]
> The Set-CsUser cmdlet is also included in the set of cmdlets available to Skype for Business Online administrators. However, Set-CsUser cannot currently be used to manage Skype for Business Online, except for setting the AudioVideoDisabled parameter. If you attempt to run the cmdlet with any other parameter, it will fail along with an error message similar to this: > Unable to set "SipAddress". This parameter is restricted within Remote Tenant PowerShell." 
  
Audio conferencing providers can also be assigned to (or unassigned from) user accounts by using the Skype for Business Online admin center:
  
![Lync admin center dial-in conferencing properties](media/LyncOnlinePowerShell_Assign_ACP.png)
  
## See also

#### 

[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)
  
[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

