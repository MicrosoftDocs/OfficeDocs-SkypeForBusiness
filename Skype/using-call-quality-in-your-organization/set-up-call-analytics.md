---
title: "Set up Skype for Business Call Analytics"
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.date: 12/15/2017
ms.topic: article
ms.assetid: fbf7247a-84ae-46cc-9204-2c45b1c734cd 
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
ms.appliesto: Skype for Business, Microsoft Teams
localization_priority: Normal
ROBOTS: None
f1keywords: None
ms.custom:
- Setup
ms.assetid: 
description: "Set up and use Call Analytics to identify and troubleshoot Skype for Business and Microsoft Teams call quality problems."
---

# Set up Skype for Business Call Analytics

As a Skype for Business Online admin, you can use Call Analytics to troubleshoot Skype for Business and Microsoft Teams call quality and connection problems. You may find it useful to set up the following capabilities in Call Analytics:
  
- Set permissions that let other personnel, such as helpdesk agents, use Call Analytics but prevent them from accessing the rest of the Skype for Business admin center. 
    
- Add building, site, and tenant information to Call Analytics by uploading a .tsv or .csv data file.
    
> [!NOTE]
> Call Analytics is currently in preview. Text and images described here may not match your experience. 
  
## Set Call Analytics permissions
<a name="BKMK_SetCAPerms"> </a>

As the admin, you get full access to all the features of Call Analytics. In addition, you can use a helpdesk model in Call Analytics that includes Tier 1 and Tier 2 permission groups. Users with Tier 1 permissions can access only a limited view of Call Analytics. Users with Tier 2 permissions can access the full functionality of Call Analytics. Both permission levels prevent access to the rest of the Skype for Business admin center. You can grant access to the tiers by adding a group that contains the user to either the Tier 1 or the Tier 2 section of the Permissions page. For details, see [Set up tiered permissions in Call Analytics](set-up-skype-for-business-call-analytics.md#BKMK_SetUpTier).
  
Tier 1 helpdesk agents handle basic call-quality problems. Tier 1 agents don't investigate issues with meetings; they collect related information and then escalate to a Tier 2 agent. Tier 2 agents see information in detailed call logs that's hidden from Tier 1 agents. The following table gives an overview of information available to agents using Call Analytics.


|**Activity**|**Information in Call Analytics**|**What the Tier 1 agent sees**|**What the Tier 2 agent sees**|
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
   
 **Set up tiered permissions in Call Analytics**
<a name="BKMK_SetUpTier"> </a>
  
1. Create Office 365 security groups for Tier 1 and Tier 2, and add the people you want to each group. You can also reuse existing security groups. For more information, see [Create, edit, or delete a security group in the Office 365 admin center](http://technet.microsoft.com/library/55c96b32-e086-4c9e-948b-a018b44510cb%28Office.14%29.aspx).
    
2. In the Office 365 admin center, go to **Admin centers** > **Skype for Business**.
    
    > [!NOTE]
    > If you land in the old Skype for Business admin center, go to the new version by clicking **Come try our new admin center**. 
  
3. In the new Skype for Business admin center, click **Permissions**.
    
4. Add the Office 365 security groups to the **Tier 1** and **Tier 2** boxes. You can add multiple groups to each role.
    
     ![Screenshot shows the Permissions for Call Analytics page with the options for Tier 1 and Tier 2 permissions.](../images/ed5b6b05-b407-4363-8cf0-a6e79027f64b.png)
  
 Users with either of these permission levels get to Call Analytics via the dedicated URL https://adminportal.services.skypeforbusiness.com.
  
## Upload a .tsv or .csv file to add building, site, and tenant information
<a name="BKMK_UploadFiles"> </a>

You can add building, site, and tenant information to Call Analytics by uploading a .csv or .tsv file. With all this information, Call Analytics can map IP addresses to physical locations. You or helpdesk agents might find this information useful to help spot trends in call problems. For example, why are many users in the same building having similar call quality issues? 
  
![Screenshot shows the Sites page with values for Number of sites and Number of subnets, and the Select file button to import site data by uploading a .tsv or a .csv file.](../images/b2f3a5cb-32b5-4f60-a9af-0691aa6ff1e8.png)
  
If you're a Skype for Business admin, you can use an existing data file from the Skype for Business Online Call Quality Dashboard. First, you download the file from Call Quality Dashboard, and then you upload it to Call Analytics. To download an existing data file, go to the **Skype for Business Admin center** > **Tools** > **Skype for Business Online Call Quality Dashboard** > **Upload now**. In the **My uploads** list, click **Download** next to the file you want.
  
If you're creating the .tsv or .csv file from scratch, see [Tenant data file format and Building data file structure](turning-on-and-using-call-quality-dashboard-for-microsoft-teams-and-skype-for-bu.md#BKMK_TenantDataFile).
  
## Related topics
<a name="BKMK_UploadFiles"> </a>

[Use Call Analytics to troubleshoot poor Skype for Business call quality](use-call-analytics-to-troubleshoot-poor-skype-for-business-call-quality.md)

[What's the difference between Call Analytics and Call Quality Dashboard?](what-s-the-difference-between-call-analytics-and-call-quality-dashboard.md)