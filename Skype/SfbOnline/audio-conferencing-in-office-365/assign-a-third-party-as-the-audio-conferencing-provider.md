---
title: "Assign a third-party as the audio conferencing provider"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.date: 01/22/2018
ms.topic: article
ms.assetid: 77f68ca7-c1cf-40d9-9c23-87a6b2abe9de
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
- ms.lync.lac.DialInExportImport
- ms.lync.lac.DialInProvider
ms.custom:
- Strat_SB_PSTN
- Audio Conferencing
description: "Learn how to set up a third-party as your dial-in conferencing provider with Skype for Business. "
---

# Assign a third-party as the audio conferencing provider

An audio conferencing provider supplies the *conference bridge*. The conference bridge provides the dial-in phone number, PINs, and conference IDs for meetings that are created. You only need to assign an audio conferencing provider to people who are going to schedule or lead Skype for Business or Microsoft Teams meetings.
  
> [!NOTE]
> For Microsoft Teams, a user can't use a third-party audio conferencing provider, they must use Audio Conferencing in Office 365, which sets the audio conferencing provider to Microsoft. 
  
## Steps to do BEFORE you can assign a third-party audio conferencing provider

1. Depending on your Office 365 plan, you might need to buy **Audio Conferencing** add-on licenses for the people in your organization who are going to schedule or lead Skype for Business or Microsoft Teams meetings using Audio Conferencing. To learn more, see [Skype for Business and Microsoft Teams add-on licensing](../skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing.md).
    
2. If you purchased **Audio Conferencing** add-on licenses, assign them to the people in your organization who are going to schedule or lead meetings that use Audio Conferencing. See [Assign Skype for Business and Microsoft Teams licenses](../skype-for-business-and-microsoft-teams-add-on-licensing/assign-skype-for-business-and-microsoft-teams-licenses.md).
    
    > [!NOTE]
    > If you assign an **Audio Conferencing** license to someone **AFTER** you assign them a third-party audio conferencing provider, that person will automatically be set to use Microsoft as their audio conferencing provider instead! If this happens, you will need to first remove Microsoft as the audio conferencing provider before you can assign a third-party audio conferencing provider to them.
  
3. Find a third-party audio conferencing provider at [Microsoft PinPoint](https://go.microsoft.com/fwlink/?LinkId=797530). Contact them and find out how to get things set up with them.
    
    They will give you:
    
  - **Dial-in numbers (toll)** and toll-free numbers if they are available.
    
  - **Conference IDs** that are used for each person who schedules meetings. Some ACPs call these conference passcodes.
    
    > [!NOTE]
    > If you have done the initial set up for an third-party ACP but you now need to make changes, at the bottom of the **Microsoft Bridge** page **Click here to configure a third-party audio conferencing provider**. 
  
    > [!NOTE]
    > When you enable a person for audio conferencing, and assign them a third-party audio conferencing provider, the audio numbers and conference IDs (passcodes) are automatically added to any **new** Skype for Business Online meetings that they create.
  
## How to assign a third-party audio conferencing provider to a user

1. In the **Skype for Business admin center**, choose **Users**. Select the user from the list and click **Edit** in the action pane.
    
2. On the user's properties page, click **Audio conferencing** and enter this information:
    
  - **Provider name** Select the third-party provider from the list.
    
  - **Default toll number** This is required.
    
  - **Default toll-free number** This not required.
    
  - **Conference ID** This is provided by your audio conferencing provider.
    
3. Click **Save**.
    
4. Send each person the PIN you received from the audio conferencing provider. The PIN may be required to call in as the conference call organizer or leader.
    
    > [!NOTE]
    > When you use a third-party audio conferencing provider, there isn't a way for you to see or set PINs on behalf of meeting organizers. 
  
## How to assign a third-party audio conferencing provider to many people at the same time

1. In the **Skype for Business admin center**, choose **Audio conferencing** > **Microsoft bridge**. At the bottom of the page, click the link in **If you would like to configure a third-party audio conferencing provider instead, click here**.
    
    > [!NOTE]
    > If you have done the initial set up for an third-party ACP but you now need to make changes, at the bottom of the **Microsoft Bridge** page, **Click here to configure a third-party audio conferencing provider**. 
  
2. On the **Configure a third party audio conferencing provider** page, under **Import and export users**, click **Export wizard**, and then follow the steps in the **Export Users wizard**. When you finish, you'll have a file that lists the people you want to set up for audio conferencing.
    
3. Send the file you created to your third-party audio conferencing provider. They will add audio conferencing information for the people listed in the file, and then return the file to you.
    
4. Double-check that the returned file has the right information in it. We've heard of instances where not everyone listed in the file got the right information.
    
5. On the **Configure a third-party audio conferencing provider page**, under **Import and export users**, click **Import wizard**, and then follow the steps in the **Import Users wizard**
    
6. Send each person the PIN you received from the audio conferencing provider. The PIN may be required to call in as the conference call organizer, or leader.
    
    > [!NOTE]
    > When you use a third-party audio conferencing provider, there isn't a way for you to see or set PINs on behalf of meeting organizers. 
  
## When to use a third-party audio conferencing provider

If you are in a country or region where Audio Conferencing in Office 365 isn't available, the service quality isn't great because of its location, or you have an existing contract with a third-party audio conferencing provider, we recommend using a third-party audio conferencing provider. Otherwise, we recommend using Microsoft as your audio conferencing provider.
  
## Automate assigning the third-party audio conferencing provider by using Windows PowerShell

- To save time or automate this, you can use the [Set-CsUserAcp](https://go.microsoft.com/fwlink/?LinkId=716851) cmdlet.
    
    > [!NOTE]
    > To change the audio provider from Microsoft to a third-party audio conferencing provider, you must remove Microsoft as the audio conferencing provider. To do this, use the [Disable-CsOnlineDialInConferencingUser](https://go.microsoft.com/fwlink/?LinkId=617692 ) cmdlet.
  
- For more information about using Windows PowerShell, see [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038).
    
## What else do I need to know?

A person in your organization can only use one audio conferencing provider. To change a person's audio conferencing provider to Microsoft, see [Assign Microsoft as the audio conferencing provider](assign-microsoft-as-the-audio-conferencing-provider.md).
  
## Related Topics
  
[Set up Skype for Business Online](../set-up-skype-for-business-online/set-up-skype-for-business-online.md)

