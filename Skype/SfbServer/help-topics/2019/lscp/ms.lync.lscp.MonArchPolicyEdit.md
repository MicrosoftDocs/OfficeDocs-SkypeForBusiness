---
title: "Archiving Policy Create New or Edit Existing"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.MonArchPolicyEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a4f948e7-e8f6-449a-8907-f61c5b143c05
ROBOTS: NOINDEX, NOFOLLOW
description: "You use Archiving policies to control archiving of internal and external communications in your deployment for users who are homed on Skype for Business Server. Archiving policies include the global policy, and, optionally, one or more site and user policies:"
---

# Archiving Policy: Create New or Edit Existing
 
You use Archiving policies to control archiving of internal and external communications in your deployment for users who are homed on Skype for Business Server. Archiving policies include the global policy, and, optionally, one or more site and user policies:
  
- **Global policy** The global policy is created by default in all Skype for Business Server deployments. You can edit the global policy, but you cannot delete this policy. If you try to delete it, all options are reset to the defaults.
    
- **Site policies (optional)** You can specify one or more site Archiving policies, each of which you can configure to enable and disable archiving of internal or external communications for a specific site. A site policy overrides the global policy, but only for the sites specified in Archiving policies. You can edit or delete site policies.
    
- **User policies (optional)** You can specify one or more user Archiving policies, each of which you can configure to enable and disable archiving for internal or external communications for a specific user. A user policy overrides the global policy and site policies, but only for the user(s) to whom you assign a user policy. You can edit or delete user policies.
    
> [!NOTE]
> If you use Exchange integration to store archiving data in Microsoft Exchange, then Exchange policies control archiving for users homed on Exchange. To enable archiving for those users, the user's mailbox must be placed on In-Place Hold. 
  
To configure the settings for a new or existing Archiving policy, you specify the following options:
- **Name** Each Archiving policy requires a name. The name is determined by the type of policy that you are adding or editing:
    
  - **Global policy** The default name is Global. You can change it to a more descriptive name. For example, Contoso North American Organization.
    
  - **Site policy** The sites listed in this dialog box include all available sites in your deployment. Click a single site to select it. For example, Redmond Data Center.
    
  - **User policy** Specify an appropriate name, such as the name of a specific user or the name of a user group or team in your organization. For example, Legal Department.
    
- **Description** This is optional. Use it to provide additional details, such as the scope or use of the policy. For example, Coordinate with Legal Departments of Other Sites.
    
- **Archive internal communications** Select this check box to enable archiving of communications on your internal network. By default, this is not enabled in any policy.
    
- **Archive external communications** Select this check box to enable archiving of communications that include external users, such as remote users, (including anonymous and PIC-setting users), and federated partners. By default, this is not enabled in any policy.
    
For details about the Archiving feature and capabilities, including Exchange integration, see [Plan for archiving in Skype for Business Server](../../../plan-your-deployment/archiving/archiving.md), [Deploy archiving for Skype for Business Server](../../../deploy/deploy-archiving/deploy-archiving.md), and [Manage archiving in Skype for Business Server](../../../manage/archiving/archiving.md).

