---
title: "Manage the Audio Conferencing settings for a user"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 0f39dc9d-eb60-4c5a-9ae3-e34a01834d9b
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Priority
f1keywords: None
ms.custom:
- Audio Conferencing
description: "As an Office 365 admin, you can edit the Audio Conferencing settings—such as the provider, default toll or toll-free number, conference ID, or PIN—for an individual user in your organization. If you want to edit settings for your organization, see Manage the Audio Conferencing settings for my organization."
---

# Manage the Audio Conferencing settings for a user

As an Office 365 admin, you can edit the Audio Conferencing settings—such as the provider, default toll or toll-free number, conference ID, or PIN—for an individual user in your organization. If you want to edit settings for your organization, see [Manage the Audio Conferencing settings for my organization](manage-the-audio-conferencing-settings-for-my-organization.md).

![teams-logo-30x30.png](../images/teams-logo-30x30.png) **Using the Microsoft Teams and Skype for Business Admin Center**

1. In the left navigation, click **Users**, and then select the user from the list of available users.

2. At the top of the page, click **Edit**.

3. Under **Audio Conferencing**, modify any of the following:

|**Setting**|**Description**|
|:-----|:-----|
|**Audio conferencing**|To turn audio conferencing on or off for the user, click **Edit** next to **Audio Conferencing**, and then in the **Audio Conferencing** pane, toggle **Audio conferencing** On or Off.|
|**Send conference info in email**  |Click this link only if you want to immediately send an email to the user with his or her conference ID and phone number. (This email does not include the PIN.) See [Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information.md).  |
|**Conference ID**  |Click **Reset conference ID** if you need to reset the conference ID for the user. For more information, see [Reset a conference ID for a user](reset-a-conference-id-for-a-user.md).  |
|**PIN** |Click **Reset PIN** if you need to reset the PIN for the user. For more information, see [Reset the Audio Conferencing PIN](reset-the-audio-conferencing-pin.md). |
|**Default conferencing toll phone number** (required) |These will be numbers that are set on the audio conferencing bridge. Format the numbers as you want them to appear in Skype for Business and Microsoft Teams meeting requests. To change the default toll number, click **Edit** next to **Audio Conferencing** and in the the **Audio Conferencing** pane, select a number under **Toll number**. |
|**Invites from this user can include toll-free number**|To change this setting, click **Edit** next to **Audio Conferencing** and in the **Audio Conferencing** pane, toggle **Include toll-free numbers in meeting requests from this user** On or Off. |
|**Dial-out permissions**|To change this setting, click **Edit** next to **Audio Conferencing** and in the **Audio Conferencing** pane, choose an option under **Dial-out permission from meetings**.|

 
![sfb-logo-30x30.png](../images/sfb-logo-30x30.png) **Using the Skype for Business admin center**
 
1. Sign in to Office 365 with your work or school account.
    
2. Choose **Admin centers** > **Skype for Business**.
    
3. In the Skype for Business admin center, choose **Users**.
    
4. Select the user for whom you want to manage settings, and then in the Action pane, click **Edit**![Shows the Edit icon](../images/4d8bea48-be68-4e0e-a54c-73decf7ea4ec.png).
    
5. Choose **Audio conferencing** in the left navigation, and then on the **Properties** page for the user, modify any of the following:
    
|**Setting**|**Description**|
|:-----|:-----|
|**Provider name** <br/> |Choose your provider from the list.  <br/><br/> **Note:** The remaining settings in this table apply only if you select Microsoft as the audio conferencing provider.           |
|**Default toll number** (required) <br/> |For a third-party providers, these phone numbers are the ones you received from the audio conferencing provider. If the user is using Microsoft as the audio conferencing provider, these will be numbers that are set on the audio conferencing bridge. Format the numbers as you want them to appear in Skype for Business and Microsoft Teams meeting requests.  <br/> |
|**Default toll-free umber** <br/> |For a third-party providers, these phone numbers are the ones you received from the audio conferencing provider. If the user is using Microsoft as the audio conferencing provider, these will be numbers that are set on the audio conferencing bridge. Format the numbers as you want them to appear in Skype for Business and Microsoft Teams meeting requests.  <br/> |
|**Allow using toll-free numbers in the Microsoft bridge of your organization to join the meetings of this user** <br/> |Select this option if you want to allow the user of toll-free numbers for joining meetings.  <br/> |
|**Send conference info via email** <br/> |Click this link only if you want to immediately send an email to the user with his or her conference ID and phone number. (This email does not include the PIN.) See [Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information.md).  <br/> |
|**Conference ID** <br/> |Select **Reset** if you need to reset the conference ID for the user. For more information, see [Reset a conference ID for a user](reset-a-conference-id-for-a-user.md).  <br/> |
|**PIN** <br/> |Select **Reset** if you need to reset the PIN for the user. For more information, see [Reset the Audio Conferencing PIN](reset-the-audio-conferencing-pin.md).  <br/> |
|**Allow unauthenticated callers to be the first people in a meeting** <br/> |Select this option to allow unauthenticated callers to be the first to join meetings.  <br/> |
|**Restrictions to dial-outs from meetings of this user** <br/> |Select an option in this list if you want to restrict dial-outs to domestic only, or if you want to prevent all dial-outs from meetings.  <br/> |
  
![Shows the Audio Conferencing Properties page for a user](../images/228550f7-92be-416d-9ab1-7c2ef54dd4e6.png)

> [!Note]
> [!INCLUDE [updating-admin-interfaces](../includes/updating-admin-interfaces.md)]

## Related topics

[Manage the Audio Conferencing settings for my organization](manage-the-audio-conferencing-settings-for-my-organization.md)

[Audio Conferencing common questions](audio-conferencing-common-questions.md)
