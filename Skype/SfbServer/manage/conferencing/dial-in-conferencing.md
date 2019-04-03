---
title: "Manage dial-in conferencing in Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 85644a2d-7694-4573-8301-aa6490b43ff4
description: "Summary: Learn how to manage dial-in conferencing in Skype for Business Server."
---

# Manage dial-in conferencing in Skype for Business Server
 
**Summary:** Learn how to manage dial-in conferencing in Skype for Business Server.
  
This topic describes how to manage dial-in conferencing. For more information about how to plan and configure dial-in conferencing at deployment, see [Plan for dial-in conferencing in Skype for Business Server](../../plan-your-deployment/conferencing/dial-in-conferencing.md) and [Configure dial-in conferencing in Skype for Business Server](../../deploy/deploy-conferencing/dial-in-conferencing.md).
  
You can perform the following tasks to manage dial-in conferencing: enable or disable dial-in conferencing, manage access numbers, manage PIN policies for dial in conferencing, manage conference join and leave announcements, modify key mappings for DTMF commands, and welcome users to dial-in conferencing. 
  
For more information about managing dial plans, see [Create or modify a dial plan in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
  
For more information about PSTN usage, see [Configure voice policies, PSTN usage records, and voice routes in Skype for Business](../../deploy/deploy-enterprise-voice/voice-and-pstn.md).
  
## Manage dial-in conferencing by using Skype for Business Server Control Panel

To manage information about dial-in conferencing:
  
1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**.
    
To manage information about dial plans and PSTN usage:
  
1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Voice routing**.
    
## Manage dial-in conferencing by using Skype for Business Server Management Shell

To manage dial-in conferencing by using Skype for Business Server Management Shell, use the following cmdlets:
  
**Dial-in configuration settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsConferenceDirectory](https://docs.microsoft.com/powershell/module/skype/get-csconferencedirectory?view=skype-ps) <br/> |Returns information about the conference directories configured for use in your organization. Conference directories are used to help dial-in conferencing users locate conference information.  <br/> |
|[Get-CsDialInConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencingconfiguration?view=skype-ps) <br/> |Retrieves information about how Skype for Business Server responds when users join or leave a dial-in conference.  <br/> |
|[Get-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencingaccessnumber?view=skype-ps) <br/> |Returns information about all the dial-in conferencing access numbers configured for use in your organization.  <br/> |
|[Get-CsDialInConferencingDtmfConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencingdtmfconfiguration?view=skype-ps) <br/> |Returns the dual-tone multi-frequency (DTMF) signaling settings used for dial-in conferencing. DTMF enables users who dial in to a conference to control conference settings (such as muting and unmuting themselves or locking and unlocking the conference) by using the keypad on their telephone.  <br/> |
|[Get-CsDialInConferencingLanguageList](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencinglanguagelist?view=skype-ps) <br/> |Returns a list of languages, including regional/minority languages, supported for use with Skype for Business Server dial-in conferences. These languages are used to relay audio messages and instructions to users participating in a conference by using a telephone.  <br/> |
|[Get-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/get-csdialplan?view=skype-ps) <br/> |Returns information about the dial plans used in your organization.  <br/> |
|[Grant-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/grant-csdialplan?view=skype-ps) <br/> |Assigns a dial plan to one or more users or groups.  <br/> |
|[Import-CsLegacyConferenceDirectory](https://docs.microsoft.com/powershell/module/skype/import-cslegacyconferencedirectory?view=skype-ps) <br/> |Imports conference directories from Microsoft Office Communications Server 2007 R2 to Skype for Business Server. This helps provide interoperability between Skype for Business Server and Office Communications Server 2007 R2.  <br/> |
|[Move-CsConferenceDirectory](https://docs.microsoft.com/powershell/module/skype/move-csconferencedirectory?view=skype-ps) <br/> |Moves an existing conference directory from one pool to another.  <br/> |
|[New-CsConferenceDirectory](https://docs.microsoft.com/powershell/module/skype/new-csconferencedirectory?view=skype-ps) <br/> |Creates a new conference directory for use in your organization.  <br/> |
|[New-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/new-csdialinconferencingaccessnumber?view=skype-ps) <br/> |Creates a new dial-in conferencing access number.  <br/> |
|[New-CsDialInConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csdialinconferencingconfiguration?view=skype-ps) <br/> |Creates a new collection of dial-in conferencing configuration settings. These settings determine how Skype for Business Server responds when users join or leave a dial-in conference. In particular, information is returned regarding whether or not participants are required to record their name when joining a conference, and how (or if) the system announces that someone has joined or left the call.  <br/> |
|[New-CsDialInConferencingDtmfConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csdialinconferencingdtmfconfiguration?view=skype-ps)  <br/> |Creates a new collection of dual-tone multi-frequency (DTMF) signaling settings used for dial-in conferencing.  <br/> |
|[New-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/new-csdialplan?view=skype-ps) <br/> |Creates a new dial plan.  <br/> |
|[Remove-CsConferenceDirectory](https://docs.microsoft.com/powershell/module/skype/remove-csconferencedirectory?view=skype-ps) <br/> |Removes an existing conference directory.  <br/> |
|[Remove-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/remove-csdialinconferencingaccessnumber?view=skype-ps) <br/> |Removes an existing dial-in conferencing access number.  <br/> |
|[Remove-CsDialInConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csdialinconferencingconfiguration?view=skype-ps) <br/> |Removes one or more collections of dial-in conferencing configuration settings. These settings determine how Skype for Business Server responds when users join or leave a dial-in conference.  <br/> |
|[Remove-CsDialInConferencingDtmfConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csdialinconferencingdtmfconfiguration?view=skype-ps) <br/> |Removes an existing collection of dual-tone multi-frequency (DTMF) signaling settings used for dial-in conferencing.  <br/> |
|[Set-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/set-csdialinconferencingaccessnumber?view=skype-ps) <br/> |Modifies the property values of an existing dial-in conferencing access number.  <br/> |
|[Set-CsDialInConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csdialinconferencingconfiguration?view=skype-ps) <br/> |Modifies settings that determine how Skype for Business Server responds when users join or leave a dial-in conference.  <br/> |
|[Set-CsDialInConferencingDtmfConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csdialinconferencingdtmfconfiguration?view=skype-ps) <br/> |Modifies the dual-tone multifrequency (DTMF) signaling settings used for dial-in conferencing.  <br/> |
|[Set-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/set-csdialplan?view=skype-ps) <br/> |Modifies an existing dial plan.  <br/> |
   
**PIN policy settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/get-cspinpolicy?view=skype-ps) <br/> |Returns information about the client personal identification number (PIN) policies configured for use in your organization. PIN authentication enables users to access Skype for Business Server by providing a PIN instead of a user name and password.  <br/> |
|[Grant-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/grant-cspinpolicy?view=skype-ps) <br/> |Assigns a client personal identification number (PIN) policy to a user or group of users.  <br/> |
|[New-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/new-cspinpolicy?view=skype-ps) <br/> |Creates a new client personal identification number (PIN) policy.  <br/> |
|[Remove-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/remove-cspinpolicy?view=skype-ps) <br/> |Removes the specified personal identification number (PIN) policy.  <br/> |
|[Set-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/set-cspinpolicy?view=skype-ps) <br/> |Modifies one or more existing client personal identification number (PIN) policies.  <br/> |
   

