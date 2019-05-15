---
title: "Archiving Configuration"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/27/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.MonArchSettingMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9c2fd164-a9b8-40e6-a1c4-423a7fe34aba
description: "You use Archiving configurations to control archiving options for your Skype for Business Server deployment, including enabling and disabling the following options:"
---

# Archiving Configuration
 
You use Archiving configurations to control archiving options for your Skype for Business Server deployment, including enabling and disabling the following options:
  
- Blocking of instant messaging (IM) or conferencing sessions if archiving fails
    
- Integration with Exchange 2013 storage, for users homed on Exchange 2013
    
- Purging of archived data
    
Archiving configurations include the global configuration and, optionally, one or more site and pool Archiving configurations:
  
- **Global configuration** The global configuration is created by default in all Skype for Business Server deployments. You edit the global configuration, but you cannot delete this Archiving configuration. If you try to delete it, all options are reset to the defaults.
    
- **Site configuration (optional)** You can specify one or more site Archiving configurations, each of which you can configure to control archiving options for a specific site. A site configuration overrides the global configuration, but only for the sites specified in the Archiving site configurations. You can edit or delete site configurations.
    
- **Pool configuration (optional)** You can specify one or more pool Archiving configuration, to control archiving options for a specific pool. A pool configuration overrides the global configuration and site configuration, but only for the pools specified in Archiving pool configurations. You can edit or delete pool configurations.
    
> [!NOTE]
> Archiving configurations apply to users homed on Skype for Business Server and, if you use Exchange to store archiving data in Microsoft Exchange, to users homed on Exchange 2013 but are implemented slightly differently for users homed on Exchange 2013. The differences are described in the next section. 
  
The **Archiving Configuration** page lists each Archiving policy that is configured for your deployment. It also shows the policy name, scope (global, site, or pool), and which archiving options are enabled for each Archiving configuration. From the **Archiving Configuration** page, you have the following options:
- **New** You can add one or more of each of the following optional Archiving configurations.
    
  - Site configuration
    
  - Pool configuration
    
- **Edit** You can change the options of any of the Archiving configurations listed on the page. Using this option, you can do the following:
    
  - **Show details** This option opens a dialog box in which you can change the archiving options for the selected Archiving configuration. You can only show details for one Archiving configuration at a time.
    
  - **Select all** This option selects all Archiving configurations in the list.
    
  - **Delete** This option deletes all selected Archiving configurations.
    
- **Action** You can use this option to quickly enable or disable archiving of IM sessions or web conferencing sessions in any configuration listed on the page, instead of editing the configuration. The options available under **Action** depend on what option is currently specified in the Archiving configuration. All options are available, except the option currently in effect for the Archiving configuration. Options include the following:
    
  - **Archive IM sessions**
    
  - **Archive IM and web conferencing sessions**
    
  - **Disable archiving**
    
- **Refresh** You can refresh the **Archiving Configuration** page to verify the status of the options of all Archiving configurations.
    
For details about the Archiving feature and capabilities, including Exchange integration, see [Plan for archiving in Skype for Business Server 2015](../../plan-your-deployment/archiving/archiving.md), [Deploy archiving for Skype for Business Server 2015](../../deploy/deploy-archiving/deploy-archiving.md), and [Manage archiving in Skype for Business Server 2015](../../manage/archiving/archiving.md).

