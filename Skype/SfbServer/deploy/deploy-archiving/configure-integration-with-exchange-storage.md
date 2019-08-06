---
title: "Configure integration with Exchange storage for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8f48b87f-a57f-4ed8-8c79-5c75b316b696
description: "Summary: Read this topic to learn how to configure integration with Exchange storage in Skype for Business Server."
---

# Configure integration with Exchange storage for Skype for Business Server
 
**Summary:** Read this topic to learn how to configure integration with Exchange storage in Skype for Business Server.
  
If you use Microsoft Exchange integration for all users in your deployment, you don't need to configure Skype for Business Server archiving policies for your users. Instead, you configure Exchange In-Place Hold policies to support archiving for users homed on Exchange, with their mailboxes put on In-Place Hold. Before you configure integration with Exchange storage, read [Plan for archiving in Skype for Business Server](../../plan-your-deployment/archiving/archiving.md). For details about Exchange In-Place Hold policies, see the Exchange product documentation. 
  
## Configure integration with Microsoft Exchange storage

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. Click the name of the appropriate global, site, or pool configuration in the list of archiving configurations, click **Edit**, click **Show details**, and then do the following:
    
   - To enable integration with Exchange storage, select the **Microsoft Exchange integration** check box.
    
   - To disable integration with Exchange storage, clear the **Microsoft Exchange integration** check box.
    
5. Click **Commit**.
    
## When Skype for Business Server and Microsoft Exchange are deployed in different forests

If you use Microsoft Exchange integration and Microsoft Exchange Server is not deployed in the same forest as Skype for Business Server, you must make sure that the following Exchange Active Directory attributes are synchronized to the forest where Skype for Business Server is deployed:
  
- msExchUserHoldPolicies
    
- proxyAddresses
    
This is a multi-value attribute. When synchronizing this attribute, you need to merge the values, not replace them to ensure the existing values are not lost.
  

