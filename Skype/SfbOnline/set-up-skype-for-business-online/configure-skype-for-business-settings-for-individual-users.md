---
title: "Admins Configure Skype for Business settings for individual users"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: 77b26eac-8228-4161-ba9f-733b187bd836
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1_keywords:
- ms.lync.lac.UsersExternalAccess
- ms.lync.lac.UsersGeneralOptions
- ms.lync.lac.UsersLyncToPhoneMoreInfo
ms.custom:
- Setup
- LIL_Placement
description: "Learn how to change the Skype for Business settings for individual users such as: Audio and video conferencing, recording of calls and meetings. "
---

# Admins: Configure Skype for Business settings for individual users

This article explains how admins configure Skype for Business for a small number of users. To do these steps in bulk, we've included links to the Windows PowerShell cmdlets you can use.
  
To allow (or block) everyone in your business to communicate with external people, see:
  
- [Allow users to contact external Skype for Business users](allow-users-to-contact-external-skype-for-business-users.md): You can let your organization use advanced Skype for Business features (share desktops, look for who's online, etc.) to communicate with people in a specific trusted (federated) business. The article also explains how to block communication with specific domains.
    
- [Let Skype for Business users add Skype contacts](let-skype-for-business-users-add-skype-contacts.md). You can let your organization use Skype for Business to search for and IM people who use Skype, the free app.
    
## Configure general settings for one user
<a name="__toc325019204"> </a>

You must have [admin permissions](https://support.office.com/en-us/article/da585eea-f576-4f55-a1e0-87090b6aaa9d) to perform these steps.

![sfb-logo-30x30.png](../images/sfb-logo-30x30.png) **Using the Skype for Business admin center**
  
1. Sign in to Office 365 with your work or school account.
    
2. Choose **Admin centers** > **Skype for Business**.
    
3. Choose **Users**.
    
    ![In the Skype for Business admin center, choose Users.](../images/7c80eeb3-6555-4fc8-91f4-61b493581e9e.png)
  
4. Choose which users you want to edit.
    
5. In the right panel, choose **Edit**.
    
    ![Choose the edit icon.](../images/5dd7c5bc-b8fa-4201-b6a6-1436ad8f88fb.png)
  
6. On the **General** options page, select or clear the check box next to the features you want to change, and then choose **Save**.
    
|**Option**|**Details**|
|:-----|:-----|
|Audio and HD video  <br/> |Allow this person to record audio meetings, audio and video meetings, or don't allow them to schedule any meetings (none).  <br/> |
|Record conversations and meetings  <br/> |Choose what this person is allowed to record.  <br/> This option is not available with Skype for Business Basic.  <br/> |
|For compliance, turn off non-archived features  <br/> | Choose this option if you're legally required to preserve electronically stored information. <br/>  Selecting this option turns off features that aren't captured when you have an [In-Place Hold](https://technet.microsoft.com/en-us/library/ff637980%28v=exchg.150%29.aspx) set up in the Exchange admin center. It turns off the following features: <br/>  File transfer using instant messaging <br/>  Shared OneNote pages <br/>  PowerPoint annotations <br/> |
   
To configure these settings in bulk, use PowerShell. See [Set up your computer for Windows PowerShell](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md).
  
## Block external communications
<a name="__toc325019206"> </a>

After you [Let Skype for Business users add Skype contacts](let-skype-for-business-users-add-skype-contacts.md) for everyone in your company, you can selectively block external communications for specific individuals using these steps.
  
1. Choose **Users**, select the users whose settings you want to disable, and then choose **Edit** ![Edit](../images/2f8948c1-e4f3-4022-b9cd-37fed066056e.png).
    
2. Choose **External communications**, and then clear the options as appropriate:
    
   - **External Skype for Business users**: Clear this box if you don't want the user to be able to communicate with Skype for Business users in federated domains.
    
   - **External Skype users**: Clear this box if you don't want the user to be able to communicate with people who are using the freeSkype app.
    
3. Click **Save**.
    
To configure these settings in bulk, use PowerShell. See [Set up your computer for Windows PowerShell](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md).
  
## Edit audio conferencing settings for one user
<a name="__toc314837483"> </a>

1. Choose **Users**, select the user whose audio conferencing settings you wan to edit, ,and then choose **Edit** ![Edit](../images/2f8948c1-e4f3-4022-b9cd-37fed066056e.png).
    
2. Choose **Audio conferencing**, select your audio conferencing provider, type or change the requested information, and then click **Save**.
    
|**Audio conferencing setting**|**Description**|
|:-----|:-----|
|**Provider name** <br/> |Choose your provider from the list.  <br/> |
|**Toll number** (required) <br/> |For a third-party ACP, these phone numbers are the ones you received from the audio conferencing provider. If the user is using Microsoft as the audio conferencing provider, these will be numbers that are set on the audio conferencing bridge. Format the numbers as you want them to appear in Skype for Business and Microsoft Teams meeting requests.  <br/> |
|**Toll-free number** <br/> |For a third-party ACP, these phone numbers are the ones you received from the audio conferencing provider. If the user is using Microsoft as the audio conferencing provider, these will be numbers that are set on the audio conferencing bridge. Format the numbers as you want them to appear in Skype for Business and Microsoft Teams meeting requests.  <br/> |
|**Conference ID and PIN** (required) <br/> |The participant PIN, or conference code, used to join meetings that are scheduled by this user and are provided from a third-party audio conferencing provider. If the user is using Microsoft as the audio conferencing provider, this won't be required.  <br/> |
   
To configure these settings in bulk, use PowerShell. See [Set the phone numbers included on invites](../audio-conferencing-in-office-365/set-the-phone-numbers-included-on-invites.md) [Set up your computer for Windows PowerShell](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md).


[!INCLUDE [LinkedIn Learning Info](../../common/office/linkedin-learning-info.md)]
  
   
## Related topics 

[Set up Skype for Business Online](set-up-skype-for-business-online.md)

[Skype for Business and Microsoft Teams add-on licensing](../skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing.md)
  
  
 
