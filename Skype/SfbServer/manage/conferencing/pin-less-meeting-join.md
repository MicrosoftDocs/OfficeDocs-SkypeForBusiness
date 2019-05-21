---
title: "Configure PIN-less meeting join in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c21e8861-bb75-45e8-8485-38daa3b8121c
description: "Summary: Learn how to configure the PIN-less meeting join option in Skype for Business Server."
---

# Configure PIN-less meeting join in Skype for Business Server
 
**Summary:** Learn how to configure the PIN-less meeting join option in Skype for Business Server.
  
When a dial-in caller attempts to join a meeting, the Conference Auto Attendant (CAA) service places the caller in a holding pen that is different from the Lobby &#x2014; if a presenter is not already on a call, and the dial-in caller has not entered a leader PIN. The PIN-less meeting join option allows dial-in callers to join a meeting without entering a leader PIN even if they are the first person on a call. 
  
Keep the following in mind when configuring this feature:
  
- Applies to private meetings only.
    
- Allows PSTN callers to stay in private meetings without the presence of authenticated users.
    
- After the setting is changed, it applies to all existing and new private meetings.
    
- Can be enabled either at the site of the organizer or at the global level.
    
- Options for who can bypass the lobby can be set for either of the following: 
    
  - **Anyone from my Organization with Callers get in directly**
    
  - **Anyone (no restrictions) with Callers get in directly** (This is the default setting.)
    
- When configured to enable PIN-less join, the CAA service still prompts for a leader PIN. Users can join the meeting whether or not a PIN is entered. However, retaining the ability to enter a leader PIN allows a dial-in caller to authenticate as a leader and manage the meeting if necessary.
    
## Configure PIN-less meeting join

To enable PIN-less meeting join for your users, use the [Set-CsDialInConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csdialinconferencingconfiguration?view=skype-ps) cmdlet with the AllowAnonymousPstnActivation parameter as follows:
  
```
Set-CsDialInConferencingConfiguration -Identity  < global or site:sitename>  -AllowAnonymousPstnActivation $True
```

For example, the following command enables PIN-less meeting join for the site Redmond:
  
```
Set-CsDialInConferencingConfiguration -Identity site:Redmond -AllowAnonymousPstnActivation $True
```

For security purposes, when PIN-less meeting join is turned on, you might want to restrict anonymous users from dialing out by ensuring the ConferencingPolicy is set as follows:
  
```
Set-CsConferencingPolicy [-Identity <XdsIdentity>] -AllowAnonymousUsersToDialOut $False
```

For more information, see [Set-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csconferencingpolicy?view=skype-ps).
  

