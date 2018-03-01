---
title: "Moving a user's audio conferencing provider to Microsoft"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.date: 01/22/2018
ms.topic: article
ms.assetid: 3a518241-1ecc-406a-93a1-d2653eecc0f5
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords:
- ms.lync.lac.PSTNConferencingEnableUsers
ms.custom:
- Strat_SB_PSTN
- Audio Conferencing
description: "Change your Skype for Business users from third-party audio conferencing providers (ACP) to a Microsoft dial-in conferencing provider. "
---

# Moving a user's audio conferencing provider to Microsoft

To use Audio Conferencing in Office 365 with Skype for Business and Microsoft Teams, users in your organization need to have an **Audio Conferencing** license assigned to them and their audio conferencing provider must be set to Microsoft. See [Try or purchase Audio Conferencing in Office 365](try-or-purchase-audio-conferencing-in-office-365.md) to get more information on licensing and how much it costs.
  
## To move a user's audio conferencing provider to Microsoft

If an **Audio Conferencing** license is assigned to a user who doesn't have an audio conferencing provider, the user's provider will be automatically set to Microsoft and you don't have to do anything else. If the user already had an audio conferencing provider, you must change the user's provider to Microsoft after assigning them an **Audio Conferencing** license.
  
To set Microsoft as the audio conferencing provider for a user that has an **Audio Conferencing** license assigned but is using another audio conferencing provider, do this:
  
1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
3. In the **Skype for Business admin center**, go to **Audio conferencing**.
    
4. If you see a banner notifying you that there are users who have an **Audio Conferencing** license assigned but don't have Microsoft set as their audio conferencing provider yet, click **Click here to move them**. If you don't see the banner, in the **Skype for Business admin center** click **Users**, and then select the **Users ready to be moved to Audio Conferencing** filter.
    
5. Select the users you want to move, and then in the Action pane, click **Edit**.
    
6. Select **Microsoft** in the **Provider name** list.
    
    > [!NOTE]
    > When the audio conferencing provider of a user is changed to Microsoft, the audio conferencing information of the user will change. If you need to keep this information, please record it somewhere before changing the provider of any of the users. 
  
7. Click **Save**.
    
## What else should I know?

- If you select the user in the list, you can view the default audio conferencing information of the user but you won't be able to see the audio conferencing PIN. You can reset the audio conferencing PIN of a user by clicking **Reset**.
    
- If you want to change audio conferencing settings for a user, you can select the user from the list and then click **Edit** and make your changes on the **Properties** page. 
    
## Related topics

[Set up Audio Conferencing for Skype for Business and Microsoft Teams](set-up-audio-conferencing.md)
  

