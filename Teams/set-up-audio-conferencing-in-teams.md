---
title: "Set up Audio Conferencing for Microsoft Teams"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: d01954f1-4f37-4cf5-a636-20039e5c59e9
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
audience: Admin
appliesto:
- Microsoft Teams 
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
- LIL_Placement
description: "Learn how to set up dial-in or Audio Conferencing for the people in your business who need to use a phone to join conference calls. "
---

# Set up Audio Conferencing for Microsoft Teams

Sometimes people in your organization will need to use a phone to call in to a meeting. Microsoft Teams includes the audio conferencing feature for just this situation! People can call in to Teams meetings using a phone, instead of using the Teams app on a mobile device or PC. 
  
You only need to set up Audio Conferencing for people who plan to schedule or lead meetings. Meeting attendees who dial in don't need any licenses assigned to them or other setup.
  
For frequently asked questions about Audio Conferencing, see [Audio Conferencing common questions](audio-conferencing-common-questions.md).

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
  
## Step 1: Find out if Audio Conferencing is available in your country/region
<a name="__top"> </a>

Go to [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md) and select your country or region to get availability information about Audio Conferencing, as well as information about Phone System, Calling Plans, toll and toll-free numbers, and Communications Credits. 
 
## Step 2: Get and assign licenses
 
1. For Audio Conferencing, you need a license for each user who will set up dial-in meetings. To learn which licenses you need to buy for Audio Conferencing and how much they will cost, see [Microsoft Teams add-on licensing](teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

    >[!NOTE] 
    > Audio Conferencing is included in Office 365 Enterprise E5 licenses and as an add-on.
        
2. After you buy the Audio Conferencing licenses, you will need to assign them to those people in your organization who are going to schedule or lead meetings. See [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc) you purchased to the people in your organization who are going to schedule or lead meetings.
    
3. We also recommend that you assign Communications Credits licenses (they don’t cost anything) to the same people you assigned licenses to in the previous step. To learn how to set up Communications Credits, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).
    
> [!NOTE]
> You can also set up [pay-per-minute Audio Conferencing](audio-conferencing-pay-per-minute.md).

## Step 3: Get service numbers for your conferencing bridges
<a name="__top"> </a>

For Audio Conferencing, you can’t use phone numbers for users; you will need to get service numbers. You can get either toll or toll-free service numbers for your conferencing bridges. There are three ways to get toll and toll-free service numbers: 
  
- **Use the Microsoft Teams admin center**. For some countries/regions, you can get service numbers for your conferencing bridges using the Microsoft Teams admin center. See [Getting service phone numbers](/microsoftteams/getting-service-phone-numbers).
    
- **Port your existing service numbers**. To port or transfer existing numbers from your current service provider or phone carrier to Office 365. You can see [Transfer phone numbers to Office 365](transfer-phone-numbers-to-office-365.md) or [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) for more information to help you do this.  
  
- **Use a request form for new numbers**. Sometimes (depending on your country/region) you won't be able to get your new service numbers using the Microsoft Teams admin center, or you will need specific phone numbers or area codes. If so, you will need to download a form and send it back to us. See [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) for more information. 
    
## Step 4: Assign a service number to the conferencing bridge
<a name="__top"> </a>

Once you get your toll and/or toll-free phone numbers for your conferencing bridge, you need to assign the numbers so they can be used on meeting invitations.  

Follow these steps to assign a new phone number to your audio conferencing bridge.

![sfb-logo-30x30.png](media/sfb-logo-30x30.png) **Using the Skype for Business admin center:**

 1. Go to the **Microsoft 365 admin center** > **Admin centers** > **Teams** > **Legacy portal**.
 2. Select **Voice** > **Phone numbers**.
 3. Select the phone number, and click **Assign**.

For more details, see [Change the phone numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md).

## Step 5: Set the default and alternate languages for a conferencing bridge
<a name="__top"> </a>
Next, you want to [Set auto attendant languages for Audio Conferencing in Microsoft Teams](set-auto-attendant-languages-for-audio-conferencing-in-teams.md) that the conferencing auto attendant uses to greet callers when they dial in to a phone number for Audio Conferencing. 

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**:

1. From the Dashboard, go to **Meetings** > **Conference bridges**.
2. Select the conferencing bridge phone number, click **Edit**, and then choose the default language.

## Step 6: Set your conferencing bridge settings
<a name="__top"> </a>
    
After setting up your conferencing bridge, verify that the default settings such as entry/exit notifications and PIN length are the ones you want to use; if they're not, you can change them. 

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**:

1. From the Dashboard, go to **Meetings** > **Conference bridges**.
2. Select **Bridge settings**. This will open the **Bridge settings** pane. 

For more details, see [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).

## Step 7: Assign dial-in phone numbers for users who lead meetings

After you have created an Audio Conferencing bridge, you need to set the toll and toll-free numbers for your users.

You will need to do this for all of the people in your organization who lead or schedule meetings. 

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**:

1. From the Dashboard, click **Users**, select the user from the list, and select **Edit**.
2. Select **Edit** next to **Audio Conferencing**, and then in the **Audio Conferencing** pane, choose a number in the **Toll number** and **Toll-free** number lists.

If you need more details, see [Assign Microsoft as the audio conferencing provider](/skypeforbusiness/audio-conferencing-in-office-365/assign-microsoft-as-the-audio-conferencing-provider).


## Step 8: Set up meeting invitations (optional)
<a name="__top"> </a>
 
The dial-in numbers that are set for the user will be automatically added to the meeting invitations that are sent to meeting attendees. However, you can add your own help and legal links, a text message, and small company graphic if you want. See [Customize meeting invitations](customize-meeting-invitations.md).
   
## Related topics

[Audio Conferencing common questions](audio-conferencing-common-questions.md)
  
[Phone numbers for Audio Conferencing in Microsoft Teams](phone-numbers-for-audio-conferencing-in-teams.md)
  
[Set options for online meetings and conference calls](https://support.office.com/article/DCD1CA39-0C1F-466C-9573-F04138FEF5E2)
