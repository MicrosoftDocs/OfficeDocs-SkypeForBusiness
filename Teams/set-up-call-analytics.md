---
title: "Set up call analytics for Microsoft Teams"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.reviewer: mikedav, vkorlep
ms.topic: article
ms.assetid: fbf7247a-84ae-46cc-9204-2c45b1c734cd
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
search.appverid: MET150
audience: Admin
appliesto: 
    - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Reporting
description: "Set up per-user call analytics to identify and troubleshoot Microsoft Teams call quality problems."
---

# Set up call analytics for Microsoft Teams

As a Microsoft Teams admin, you can use per-user call analytics to troubleshoot Teams call quality and connection problems for **individual users**. To take full advantage of call analytics, set up the following:
  
- Assign specialized support roles to people, such as helpdesk agents, to let them view call analytics for users. These support roles can't access the rest of the Teams admin center. 
    
- Add building, site, and tenant information to per-user call analytics by uploading a .tsv or .csv data file.
    
When you're ready to start using per-user call analytics, read [Use per-user call analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md).
  
## Give permission to support and helpdesk staff

As the Teams admin, you have full access to call analytics information for all users. We've created some specialized Azure Active Directory roles that you can assign to support staff and helpdesk agents so they can also access per-user call analytics (without having access to the rest of the Teams admin center). Assign the **Teams communications support specialist** role to users who should have a limited view of per-user call analytics (Tier 1 support). Assign the **Teams communications support engineer** role to users who need full access to per-user call analytics (Tier 2 support). Neither role has access to the rest of the Teams admin center.

To learn what each of these roles does, read [What does each Teams Support role do](use-call-analytics-to-troubleshoot-poor-call-quality.md#what-does-each-teams-support-role-do)?

For more information about Teams admin roles, see [Use Teams admin roles to manage Teams](using-admin-roles.md). To learn how to assign admin roles in Azure Active Directory, see [View and assign roles in Azure Active Directory](/Azure/active-directory/users-groups-roles/directory-manage-roles-portal).

To learn how to assign administrative roles in Azure Active Directory, see [View and assign roles in Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

## Upload a .tsv or .csv file to add building, site, and tenant information

You can add building, site, and tenant information to per-user call analytics by uploading a .csv or .tsv file. With all this information, call analytics can map IP addresses to physical locations. Admins and helpdesk agents can use this information to help spot trends in call problems. For example, why are users in the same building having similar call quality problems? 

If you're a Teams or Skype for Business admin, you can use an existing tenant and building data file from the Teams or Skype for Business Call Quality Dashboard (CQD). First, you download the file from CQD, then upload it to call analytics. 

- To download an existing data file, go to **Microsoft Teams admin center** > **Analytics & reports** > **Call Quality Dashboard** > **Upload now**. In the **My uploads** list, click **Download** next to the file you want. 

- To upload the new file, see [Add and update reporting labels](/microsoftteams/learn-more-about-site-upload).
  
If you're creating the .tsv or .csv file from scratch, see [Upload tenant and building data](CQD-upload-tenant-building-data.md).
  
## Related topics

[Use per-user call analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)
