---
title: "Archiving Policy"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/27/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.MonArchPolicyMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9b69f1fa-8f3b-450e-aa89-91fd462f198d
description: "You use Archiving policies to enable and disable archiving for users homed on Skype for Business Server. In each Archiving policy, you can enable or disable archiving for either or both of the following:"
---

# Archiving Policy
 
You use Archiving policies to enable and disable archiving for users homed on Skype for Business Server. In each Archiving policy, you can enable or disable archiving for either or both of the following:
  
- Internal communications
    
- External communications (communications that include at least one user outside your internal network)
    
Archiving policies include the global policy, and, optionally, one or more site and user Archiving policies:
  
- **Global policy** The global policy is created by default in all deployments. You can edit the global policy, but you cannot delete this policy. If you try to delete it, all options are reset to the defaults.
    
- **Site policy (optional)** You can specify one or more site Archiving policies, each of which you can configure to enable and disable archiving of internal or external communications for a single site. A site policy overrides the global policy, but only for the sites specified in your Archiving site policies. You can edit or delete site policies.
    
- **User policy (optional)** You can specify one or more user Archiving policies, each of which you can configure to enable and disable archiving of internal or external communications for a specific user or user group. A user policy overrides the global policy and site policies, but only for the users and user groups to whom you assign user-level Archiving policies. You can edit or delete user policies.
    
> [!NOTE]
> Archiving policies apply only to users homed on Skype for Business Server. If you use Exchange integration to store archiving data in Microsoft Exchange, then Exchange 2013 policies control archiving for users homed on Exchange 2013. To enable archiving for those users, the user's mailbox must be placed on In-Place Hold. 
  
The **Archiving Policy** page lists each Archiving policy that is configured for your deployment. It also shows the policy name, scope (global, site, or user), and which archiving options are enabled for each Archiving policy. From the **Archiving Policy** page, you have the following options:
- **New** You can add one or more of each of the following optional Archiving policies:
    
  - Site policy
    
  - User policy
    
- **Edit** You can change the options of any of the Archiving policies listed on the page. Using this option, you can do the following:
    
  - **Show details** This option opens a dialog box in which you can change the archiving options for an Archiving policy.
    
  - **Select all** This option selects all Archiving policies in the list.
    
  - **Delete** This option deletes all selected Archiving policies.
    
- **Action** You can use this option to quickly enable or disable archiving of internal or external communications in any policy listed on the page, instead of editing the policy. The options available under **Action** depend on what option is currently specified in the Archiving policy. All options are available, except the option currently in effect for the Archiving policy. Options include the following:
    
  - **Enable Archiving of internal communications**
    
  - **Disable Archiving of internal communications**
    
  - **Enable Archiving of external communications**
    
  - **Disable Archiving of external communications**
    
- **Refresh** You can refresh the **Archiving Policy** page to verify the status of the options of all Archiving policies.
    
For details about the Archiving feature and capabilities, including Exchange integration, see [Plan for archiving in Skype for Business Server 2015](../../plan-your-deployment/archiving/archiving.md), [Deploy archiving for Skype for Business Server 2015](../../deploy/deploy-archiving/deploy-archiving.md), and [Manage archiving in Skype for Business Server 2015](../../manage/archiving/archiving.md).

