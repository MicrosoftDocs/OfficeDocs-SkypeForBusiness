---
title: Manage conferencing policies in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 34ec5e41-6fe6-450b-81b0-0d17b9989839
---


# Manage conferencing policies in Skype for Business Server 2015
[] **Summary:** Learn how to manage conferencing policies in Skype for Business Server 2015.
This topic describes how to manage conferencing policies. For more information about how to plan and deploy conferencing, see  [Plan for conferencing in Skype for Business Server 2015](plan-for-conferencing-in-skype-for-business-server-2015.md) and [Deploy conferencing in Skype for Business Server 2015](deploy-conferencing-in-skype-for-business-server-2015.md).
  
    
    

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
  
    
    

|
|
|**Cmdlet**||
|:-----|:-----|
|**Conferencing policy settings**|**Description**|
|:-----|:-----|
| [Get-CsConferencingPolicy](get-csconferencingpolicy.md) <br/> |Returns information about the conferencing policies that have been configured for use in your organization.  <br/> |
| [Grant-CsConferencingPolicy](grant-csconferencingpolicy.md) <br/> |Assigns a conferencing policy at the per-user scope.  <br/> |
| [New-CsConferencingPolicy](new-csconferencingpolicy.md) <br/> |Creates a new conferencing policy for use in your organization.  <br/> |
| [Remove-CsConferencingPolicy](remove-csconferencingpolicy.md) <br/> |Removes the specified conferencing policy.  <br/> |
| [Set-CsConferencingPolicy](set-csconferencingpolicy.md) <br/> |Modifies an existing conferencing policy.  <br/> |
   

