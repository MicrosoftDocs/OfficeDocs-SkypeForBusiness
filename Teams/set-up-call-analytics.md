---
title: "Set up Call Analytics"
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.reviewer: mikedav, wlooney
ms.topic: article
ms.assetid: fbf7247a-84ae-46cc-9204-2c45b1c734cd 
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
search.appverid: MET150
audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Reporting
description: "Set up and use Call Analytics to identify and troubleshoot Skype for Business and Microsoft Teams call quality problems."
---

# Set up Call Analytics

As a Teams or Skype for Business Online admin, you can use Call Analytics to troubleshoot Skype for Business and Microsoft Teams call quality and connection problems. You may find it useful to set up the following capabilities in Call Analytics:
  
- Set permissions that let other personnel, such as helpdesk agents, use Call Analytics, but prevent them from accessing the rest of the Microsoft Teams admin center. 
    
- Add building, site, and tenant information to Call Analytics by uploading a .tsv or .csv data file.
    
**Call Analytics is now available in the Microsoft Teams admin center**. To see all the call information and data for a user, use the **Call History** tab. You can do this by looking on the user's profile page by doing one of the following:

- Search for the user from the dashboard.
  
   ![Screenshot of User Search on dashboard](media/set-up-call-analytics-image-1.png)

-  Select **Users** in the left navigation.

   ![Screenshot of left navigation](media/set-up-call-analytics-image-2.png)
  
## Set Call Analytics permissions
<a name="BKMK_SetCAPerms"></a>

As the admin, you have full access to all the features of Call Analytics. In addition, you can assign Azure Active Directory roles to support staff. Assign the Teams communications support specialist role to users who should have a limited view of Call Analytics. Assign the Teams communications support engineer role to users who need access to the full functionality of Call Analytics. Both permission levels prevent access to the rest of the Microsoft Teams admin center.

> [!NOTE]
> The communications support specialist role is equivalent to tier 1 support and the communications support engineer role is equivalent to tier 2 support.

For more information about Teams admin roles, see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md). 
  
Communications support specialists handle basic call-quality problems. They don't investigate issues with meetings. Instead, they collect related information and then escalate to a communications support engineer. Communications support engineers see information in detailed call logs that's hidden from communications support specialists. The following table gives an overview of information available to communications support specialists and communications support engineers when they use Call Analytics.

|**Activity**|**Information in Call Analytics**|**What the communications support specialist sees**|**What the communications support engineer sees**|
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
   
 ### Set up permissions by assigning admin roles
<a name="BKMK_SetUpTier"> </a>

To learn how to assign administrative roles in Azure Active Directory, see [View and assign roles in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

## Upload a .tsv or .csv file to add building, site, and tenant information
<a name="BKMK_UploadFiles"> </a>

You can add building, site, and tenant information to Call Analytics by uploading a .csv or .tsv file. With all this information, Call Analytics can map IP addresses to physical locations. You or helpdesk agents might find this information useful to help spot trends in call problems. For example, why are many users in the same building having similar call quality issues? 

If you're a Teams and Skype for Business admin, you can use an existing data file from the Teams & Skype for Business Call Quality Dashboard. First, you download the file from Call Quality Dashboard, and then you upload it to Call Analytics. 

- To download an existing data file, go to **Microsoft Teams admin center** > **Call Quality Dashboard** > **Upload now**. In the **My uploads** list, click **Download** next to the file you want.

- To upload the new file, go to **Microsoft Teams admin center** > **Locations**, and then select **Upload location data** or **Replace location data**.
  
If you're creating the .tsv or .csv file from scratch, see [Tenant data file format and Building data file structure](turning-on-and-using-call-quality-dashboard.md#BKMKTenantDataFile).
  
## Related topics
<a name="BKMK_UploadFiles"> </a>

[Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Call Analytics and Call Quality Dashboard](difference-between-call-analytics-and-call-quality-dashboard.md)

  
 
