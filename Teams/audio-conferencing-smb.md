---
title: Set up Audio Conferencing for small and medium businesses
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: jonorton, tonysmit
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - M365-collaboration
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Audio Conferencing
description: Learn how to set Audio Conferencing in your small or medium business for people who need to use a phone to call in to meetings. 
---

# Set up Audio Conferencing for small and medium businesses

With Audio Conferencing, people can call in to Teams meetings using a phone instead of using the Teams app on their mobile device or from their computer.  

If you're a small or medium-sized business with up to 300 users and you currently don’t have any Audio Conferencing licenses, you can get Audio Conferencing free for one year. This free offer is available starting October 1, 2020.

The Audio Conferencing add-on license can be applied to users who have Microsoft 365 Business Basic, Business Standard, Business Premium, Enterprise E1, or Enterprise E3 licenses. To learn more, see [Teams add-on licenses](teams-add-on-licensing/microsoft-teams-add-on-licensing.md)

> [!NOTE]
> If you have Enterprise E5 or Microsoft 365 Business Voice, you won't be able to use the free Audio Conferencing offer because these licenses already include Audio Conferencing.

In this article, we'll walk you through how to set up Audio Conferencing. You only need to set up Audio Conferencing for people who plan to schedule or lead meetings. Meeting attendees who call in to meetings don't need licenses or other setup. To learn more, see [Audio Conferencing](audio-conferencing-in-office-365.md).

## Set up Audio Conferencing

When you set up Audio Conferencing, a phone number is automatically assigned to your conferencing bridge so that it can be used in meeting invitations. The phone number that's assigned as the default number of your conferencing bridge will be one from the country or region of your organization. This phone number is a toll number, in which long-distance charges may apply.

> [!NOTE]
> You can also use a toll-free number, which requires a few additional steps. To learn more about phone numbers for your conferencing bridge, see [Audio Conferencing phone numbers](#audio-conferencing-phone-numbers) later in this article.

### Step 1: Get Audio Conferencing licenses

Get one Audio Conferencing license for each person who will lead meetings. Use the Microsoft 365 admin center to do this.

1. In the Microsoft 365 admin center, go to **Billing** > **Purchase services**, and then at the bottom of the page, select **Add-ons**.
2. Select **Microsoft 365 Audio Conferencing Adoption Promo** > **Details**, and then select **Get now**.
3. Enter the number of licenses you need for your meeting organizers, and then complete your order.

    :::image type="content" source="media/audio-conferencing-smb-add.png" alt-text="Screenshot of Audio Conferencing Adoption Promo license.":::

    > [!NOTE]
    > Clear or select the **Automatically assign to all of your users with no licenses**, depending on whether you want to automatically assign an Audio Conferencing license to all users who don't have this license.

### Step 2: Assign an Audio Conferencing license to users who lead meetings

Assign a license to each person who will lead meetings. Use the Microsoft 365 admin center to do this.

#### Assign a license to one user

1. In the Microsoft 365 admin center, go to **Users** > **Active users**.  
2. Select the row of the user you want to assign the license to, and then in the pane, select **Licenses and Apps**.
3. Select the **Microsoft 365 Audio Conferencing** check box, and then select **Save changes**.

#### Assign a license to multiple users

1. In the Microsoft 365 admin center, go to **Users** > **Active users**.  
2. Select the circles next to the users you want to assign the license to, and then select **Manage product licenses**.
3. In the **Manage product licenses** pane, select **Assign more**.
4. Select the **Microsoft 365 Audio Conferencing** check box, and then select **Save changes**.  

> [!IMPORTANT]
> It can take up to 24 hours for the assigned phone numbers to show up on your meeting invite. If you aren't seeing updated numbers appear, please wait at least 24 hours before contacting support.

## Schedule Teams meetings in Outlook

Your meeting organizers can now schedule meetings in Outlook. In Outlook, go to **Calendar**, and then select the **New Teams meeting** button. The meeting dial-in numbers and the conference ID are automatically added to the meeting invitation that's sent to meeting attendees. To learn more, see [Schedule a Teams meeting in Outlook](https://support.microsoft.com/office/schedule-a-teams-meeting-from-outlook-883cc15c-580f-441a-92ea-0992c00a9b0f).

> [!NOTE]
> If you want, you can customize meeting invitations to add your company logo, links to your support website and legal disclaimer, and a text-only footer. To learn more, see [Customize meeting invitations](meeting-settings-in-teams.md#customize-meeting-invitations).

## Audio Conferencing phone numbers

There are two types of numbers that you can use for your conferencing bridge. You can use either **shared numbers** (as in the [Set up Audio Conferencing](#set-up-audio-conferencing) section earlier in this article) or **dedicated numbers**. Here's more information about each.

### Shared numbers

A shared number is a number that's shared across all organizations. Shared numbers are toll numbers and are automatically assigned when you set up Audio Conferencing.

To see the default number that's assigned to your conferencing bridge, in the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Conference bridges**, and then find the number for the location that's nearest to you.

### Dedicated numbers

A dedicated number is a number that's available only to your users. A dedicated number can be a toll number or a toll-free number. To use a dedicated number, you'll have to first get the number, assign it to your conferencing bridge, and then assign the number to each person who will lead meetings.

There are a couple ways to get a dedicated number. You can get a number from Microsoft or transfer (port) an existing number from your current service provider to Microsoft. To learn more about how to do this, see [Getting service numbers](getting-service-phone-numbers.md).

Keep in mind that if you use a toll-free number, you have to first assign a Communications Credits license to each person who will lead meetings. To learn more, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).

After you have your number, assign it to your conference bridge. Use the Microsoft Teams admin center to do this.

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Conference bridges**.
2. Select **Add**, and then select **Toll number** or **Toll-free number**.
3. In the **Add phone number** pane, select the number, and then select **Apply**.

#### Assign dial-in phone numbers for users who lead meetings

Refer to [Set the phone numbers included on invites in Microsoft Teams](set-the-phone-numbers-included-on-invites-in-teams.md).

> [!NOTE]
> You can also set phone numbers by adding them to the *TeamsAudioconferencingpolicy* and assigning the policy to your users. Toll and toll-free phone numbers added to the policy take precedence over the phone numbers set individually for users via the audio conferencing settings pane. If no phone numbers are added to the *Teamsaudioconferencingpolicy*, then the phone number set individually for users via the audio conferencing settings pane will be displayed in Microsoft Teams meeting requests. [Audio Conferencing policy settings for toll and toll-free numbers](audio-conferencing-toll-free-numbers-policy.md) has more information.

## Related topics

- [Audio Conferencing](audio-conferencing-in-office-365.md)
- [Set up Audio Conferencing for Teams](set-up-audio-conferencing-in-teams.md)
- [Phone numbers for Audio Conferencing](phone-numbers-for-audio-conferencing-in-teams.md)
- [Audio Conferencing common questions](audio-conferencing-common-questions.md)
- [Getting service numbers](getting-service-phone-numbers.md)
- [Teams add-on licenses](teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users)
