---
title: "Set up per-user call analytics for Microsoft Teams"
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.reviewer: mikedav, wlooney
ms.topic: article
ms.assetid: fbf7247a-84ae-46cc-9204-2c45b1c734cd
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
search.appverid: MET150
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom: 
  - Reporting
description: "Set up per-user call analytics for to identify and troubleshoot Microsoft Teams and Skype for Business call quality problems."
---

# Set up per-user call analytics for Microsoft Teams

As a Microsoft Teams or Skype for Business Online admin, you can use per-user call analytics to troubleshoot Teams and Skype for Business Online call quality and connection problems. To take full advantage of call analytics, set up the following:
  
- Assign specialized support roles to people, such as helpdesk agents, to let them view call analytics for users. These support roles can't access the rest of the Teams admin center. 
    
- Add building, site, and tenant information to per-user call analytics by uploading a .tsv or .csv data file.
    
When you're ready to start using per-user call analytics, read [Use per-user call analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md).
  
## Give permission to support and helpdesk staff
<a name="BKMK_SetCAPerms"></a>

As the Teams admin, you have full access to call analytics information for all users. We've created some specialized Azure Active Directory roles that you can assign to support staff and helpdesk agents so they can also access per-user call analytics (without having access to the rest of the Teams admin center). Assign the **Teams communications support specialist** role to users who should have a limited view of per-user call analytics (Tier 1 support). Assign the **Teams communications support engineer** role to users who need full access to per-user call analytics (Tier 2 support). Neither role has access to the rest of the Teams admin center.

For more information about Teams admin roles, see [Use Teams admin roles to manage Teams](using-admin-roles.md). To learn how to assign admin roles in Azure Active Directory, see [View and assign roles in Azure Active Directory](https://docs.microsoft.com/Azure/active-directory/users-groups-roles/directory-manage-roles-portal).
  
## What does each Teams Support role do?

The **Teams communications support specialist** (Tier 1 support) handles basic call-quality problems. They don't investigate issues with meetings. Instead, they collect related information and then escalate to a communications support engineer. 

The **Teams communications support engineer** (Tier 2 support) sees information in detailed call logs that are hidden from the Teams communications support specialist. The table below lists the information available to each Teams communication support role.

|**Activity**|**Information**|What the communications support **specialist** sees|What the communications support **engineer** sees|
|:-----|:-----|:-----|:-----|
|**Calls** <br/> |Caller name  <br/> |Only the name of the user for whom the agent searched.  <br/> |User name.  <br/> |
||Recipient name  <br/> |Shows as Internal User or External User.  <br/> |Recipient name.  <br/> |
||Caller phone number  <br/> |Entire phone number except last three digits are obfuscated with asterisk symbols. For example, 15552823***.  <br/> |Entire phone number except last three digits are obfuscated with asterisk symbols. For example, 15552823***.  <br/> |
||Recipient phone number  <br/> |Entire phone number except last three digits are obfuscated with asterisk symbols. For example, 15552823***.  <br/> |Entire phone number except last three digits are obfuscated with asterisk symbols. For example, 15552823***.  <br/> |
||**Call Details** > **Advanced** tab <br/> |Information not shown.  <br/> |All details shown, such as device names, IP address, subnet mapping, and more.  <br/> |
||**Call Details** > **Advanced** > **Debug** tab <br/> |Information not shown.  <br/> |All details shown, such as DNS suffix and SSID.  <br/> |
|**Meetings** <br/> |Participant names  <br/> |Only the name of the user for whom the agent searched. Other participants identified as Internal User or External User.  <br/> |All names shown.  <br/> |
||Participant count  <br/> |Number of participants.  <br/> |Number of participants.  <br/> |
||Session details  <br/> |Session details shown with exceptions. Only the name of the user for whom the agent searched is shown. Other participants identified as Internal User or External User. Last three digits of telephone number obfuscated with asterisk symbols.  <br/> |Session details shown. User names and session details shown. Last three digits of telephone number obfuscated with asterisk symbols.  <br/> |
||||

## Upload a .tsv or .csv file to add building, site, and tenant information
<a name="BKMK_UploadFiles"> </a>

You can add building, site, and tenant information to per-user call analytics by uploading a .csv or .tsv file. With all this information, per-user call analytics can map IP addresses to physical locations. Admins and helpdesk agents can use this information to help spot trends in call problems. For example, why are users in the same building having similar call quality problems? 

If you're a Teams or Skype for Business admin, you can use an existing data file from the Teams or Skype for Business Call Quality Dashboard. First, you download the file from Call Quality Dashboard, and then you upload it to per-user call analytics. 

- To download an existing data file, go to **Microsoft Teams admin center** > **Call Quality Dashboard** > **Upload now**. In the **My uploads** list, click **Download** next to the file you want.

- To upload the new file, go to **Microsoft Teams admin center** > **Locations**, and then select **Upload location data** or **Replace location data**.
  
If you're creating the .tsv or .csv file from scratch, see [Tenant data file format and Building data file structure](turning-on-and-using-call-quality-dashboard.md#BKMKTenantDataFile).
  
## Related topics
<a name="BKMK_UploadFiles"> </a>

[Use per-user call analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)


  
 
