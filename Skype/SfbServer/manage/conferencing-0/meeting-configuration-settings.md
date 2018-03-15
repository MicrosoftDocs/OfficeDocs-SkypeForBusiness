---
title: "Manage meeting configuration settings in Skype for Business Server 2015"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2e6c4f48-464e-4b8e-b7f4-68cdc1ae4ad9
description: "Summary: Learn how to manage meeting configuration settings in Skype for Business Server 2015."
---

# Manage meeting configuration settings in Skype for Business Server 2015
 
**Summary:** Learn how to manage meeting configuration settings in Skype for Business Server 2015.
  
This topic describes how to manage meeting configuration settings. For more information about how to plan and deploy conferencing, see [Plan for conferencing in Skype for Business Server 2015](../../plan-your-deployment/conferencing/conferencing.md) and [Deploy conferencing in Skype for Business Server 2015](../../deploy-1/deploy-conferencing/deploy-conferencing.md).
  
Meeting configuration settings dictate the type of meetings that users can create, in addition to controlling how (or even if) anonymous users and dial-in conferencing users can join these meetings. Note that these settings only affect scheduled meetings; they do not affect ad-hoc meetings created by clicking the Meet Now option in Skype for Business.
  
Meeting configuration settings define the following:
  
- Whether users dialing in from the public switched telephone network (PSTN) go to the lobby
    
- Who can be a presenter
    
- Whether conference type is assigned by default
    
- Whether anonymous (unauthenticated) users are admitted by default
    
You can define characteristics of meetings by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell. 
  
You can specify meeting settings at the global level (created by default), site level, or pool level. By default, the global settings define the meeting experience. If you create pool-level settings, those settings apply to all meetings hosted by that pool. If you do not create pool-level settings, site-level settings apply, if they exist. If you do not define site-level settings, the global settings apply to all meetings.
  
## Manage meeting settings by using Skype for Business Server Control Panel

To manage meeting settings by using Skype for Business Server Control Panel:
  
1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Meeting Configuration**.
    
## Manage meeting settings by using Skype for Business Server Management Shell

To manage meetings by using Skype for Business Server Management Shell, use the following cmdlets:
  
**Meeting configuration settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsMeetingConfiguration](../../manage/management-shell/get-csmeetingconfiguration.md) <br/> |Returns information about the meeting configuration settings currently in use in your organization.  <br/> |
|[New-CsMeetingConfiguration](../../manage/management-shell/new-csmeetingconfiguration.md) <br/> |Creates a new collection of meeting configuration settings at the site or service scope.  <br/> |
|[Remove-CsMeetingConfiguration](../../manage/management-shell/remove-csmeetingconfiguration.md) <br/> |Deletes an existing collection of meeting configuration settings.  <br/> |
|[Set-CsMeetingConfiguration](../../manage/management-shell/set-csmeetingconfiguration.md) <br/> |Modifies the meeting configuration settings currently in use in your organization.  <br/> |
   

