---
title: "Set up Audio Conferencing for Microsoft Teams"
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: d01954f1-4f37-4cf5-a636-20039e5c59e9
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - M365-collaboration
  - m365initiative-meetings
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
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

Go to [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md) and select your country or region to get availability information about Audio Conferencing, as well as information about Phone System, Calling Plans, toll and toll-free numbers, and Communications Credits.

## Step 2: Get and assign licenses

1. For Audio Conferencing, you need a license for each user who will set up dial-in meetings. To learn which licenses you need to buy for Audio Conferencing and how much they will cost, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

    >[!NOTE]
    > Audio Conferencing is included in Office 365 Enterprise E5 licenses and as an add-on.

2. After you buy the Audio Conferencing licenses, you will need to assign them to those people in your organization who are going to schedule or lead meetings. See [Assign licenses to users in Microsoft 365 or Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc) you purchased to the people in your organization who are going to schedule or lead meetings.

3. We also recommend that you assign Communications Credits licenses (they don’t cost anything) to the same people you assigned licenses to in the previous step. To learn how to set up Communications Credits, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).

   > [!NOTE]
   > You can also set up [pay-per-minute Audio Conferencing](audio-conferencing-pay-per-minute.md).

## Step 3: Get service numbers for your conferencing bridges

For Audio Conferencing, you can’t use phone numbers for users; you will need to get service numbers. You can get either toll or toll-free service numbers for your conferencing bridges. There are three ways to get toll and toll-free service numbers:
  
- **Use the Microsoft Teams admin center**. For some countries/regions, you can get service numbers for your conferencing bridges using the Microsoft Teams admin center. See [Getting service phone numbers](./getting-service-phone-numbers.md).

- **Port your existing service numbers**. To port or transfer existing numbers from your current service provider or phone carrier to Microsoft 365 or Office 365. You can see [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) for more information to help you do this.  
  
- **Use a request form for new numbers**. Sometimes (depending on your country/region) you won't be able to get your new service numbers using the Microsoft Teams admin center, or you will need specific phone numbers or area codes. If so, you will need to download a form and send it back to us. See [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) for more information.

## Step 4: Assign a service number to the conferencing bridge

Once you get your toll and/or toll-free phone numbers for your conferencing bridge, you need to assign the numbers so they can be used on meeting invitations.  

Follow these steps to assign a new phone number to your audio conferencing bridge.

 **Using the Microsoft Teams admin center**:

 1. From the Home, go to **Voice** > **Phone numbers**.
 2. Select the phone number, and click **Assign**.

For more details, see [Change the phone numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md).

## Step 5: Set the default and alternate languages for a conferencing bridge

Next, you want to [Set auto attendant languages for Audio Conferencing in Microsoft Teams](set-auto-attendant-languages-for-audio-conferencing-in-teams.md) that the conferencing auto attendant uses to greet callers when they dial in to a phone number for Audio Conferencing.

 **Using the Microsoft Teams admin center**:

1. From the Home, go to **Meetings** > **Conference bridges**.
2. Select the conferencing bridge phone number, click **Edit**, and then choose the default language.

## Step 6: Set your conferencing bridge settings

After setting up your conferencing bridge, verify that the default settings such as entry/exit notifications and PIN length are the ones you want to use; if they're not, you can change them.

 **Using the Microsoft Teams admin center**:

1. From the Home, go to **Meetings** > **Conference bridges**.
2. Select **Bridge settings**. This will open the **Bridge settings** pane.

For more details, see [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).

## Step 7: Assign dial-in phone numbers for users who lead meetings

Refer to [Set the phone numbers included on invites in Microsoft Teams](set-the-phone-numbers-included-on-invites-in-teams.md).

> [!NOTE]
> You can also set phone numbers by adding them to the *TeamsAudioconferencingpolicy* and assigning the policy to your users. Toll and toll-free phone numbers added to the policy take precedence over the phone numbers set individually for users via the audio conferencing settings pane. If no phone numbers are added to the *Teamsaudioconferencingpolicy*, then the phone number set individually for users via the audio conferencing settings pane will be displayed in Microsoft Teams meeting requests. [Audio Conferencing policy settings for toll and toll-free numbers](audio-conferencing-toll-free-numbers-policy.md) has more information.

> [!IMPORTANT]
> It can take up to 24 hours for the assigned phone numbers to show up on your meeting invite. If you aren't seeing updated numbers appear, please wait at least 24 hours before contacting support.

## Step 8: Set up meeting invitations (optional)

The dial-in numbers that are set for the user will be automatically added to the meeting invitations that are sent to meeting attendees. However, you can add your own help and legal links, a text message, and small company graphic if you want. See [Customize meeting invitations](meeting-settings-in-teams.md#customize-meeting-invitations).

## Related topics

[Audio Conferencing common questions](audio-conferencing-common-questions.md)
  
[Phone numbers for Audio Conferencing in Microsoft Teams](phone-numbers-for-audio-conferencing-in-teams.md)
  
[Set options for online meetings and conference calls](https://support.office.com/article/DCD1CA39-0C1F-466C-9573-F04138FEF5E2)
