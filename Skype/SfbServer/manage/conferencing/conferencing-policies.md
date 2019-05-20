---
title: "Manage conferencing policies in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 34ec5e41-6fe6-450b-81b0-0d17b9989839
description: "Summary: Learn how to manage conferencing policies in Skype for Business Server."
---

# Manage conferencing policies in Skype for Business Server
 
**Summary:** Learn how to manage conferencing policies in Skype for Business Server.
  
This topic describes how to manage conferencing policies. For more information about how to plan and deploy conferencing, see [Plan for conferencing in Skype for Business Server](../../plan-your-deployment/conferencing/conferencing.md) and [Deploy conferencing in Skype for Business Server](../../deploy/deploy-conferencing/deploy-conferencing.md).
  
Conferencing policies allow you to define a wide variety of scheduling and participation options, ranging from whether a meeting can include IP audio and video to the maximum number of people who can attend. You can use conferencing policies to manage security, bandwidth, and legal aspects of meetings.
  
You can define conferencing policy on three levels: global scope, site scope, and user scope. Settings apply to a specific user from the narrowest scope to the widest scope. If you assign a policy to a user, those settings take precedence. If you do not assign a user policy, site settings apply. If no user or site policies apply, global policy provides the default settings.
  
A global policy exists by default, so you cannot create a new global policy. You also cannot delete the existing global policy, but you can change the existing global policy to customize your default settings.
  
## Manage conferencing policies by using Skype for Business Server Control Panel

To manage conferencing policies by using Skype for Business Server Control Panel:
  
1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Conferencing Policy**.
    
## Manage conferencing policies by using Skype for Business Server Management Shell

To manage meetings by using Skype for Business Server Management Shell, use the following cmdlets:
  
**Conferencing policy settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/get-csconferencingpolicy?view=skype-ps) <br/> |Returns information about the conferencing policies that have been configured for use in your organization.  <br/> |
|[Grant-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csconferencingpolicy?view=skype-ps) <br/> |Assigns a conferencing policy at the per-user scope.  <br/> |
|[New-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/new-csconferencingpolicy?view=skype-ps) <br/> |Creates a new conferencing policy for use in your organization.  <br/> |
|[Remove-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/remove-csconferencingpolicy?view=skype-ps) <br/> |Removes the specified conferencing policy.  <br/> |
|[Set-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csconferencingpolicy?view=skype-ps) <br/> |Modifies an existing conferencing policy.  <br/> |
   

