---
title: "Set up Audio Conferencing for small and medium businesses"
ms.author: v-lanac
author: lanachin
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
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 
  - Audio Conferencing
description: "Learn how to set Audio Conferencing in your small or medium business for people who need to use a phone to call in to meetings. "
---

# Set up Audio Conferencing for small and medium businesses

Your users might sometimes need to use a phone to call in to a meeting. Microsoft Teams includes the Audio Conferencing feature for just this situation! With Audio Conferencing, people can call in to Teams meetings using a phone instead of using Teams app on their mobile device or from their computer.  

If you're a small or medium-sized business with up to 300 users and you currently don’t have any Audio Conferencing licenses or you're a new customer, you'll get Audio Conferencing for free!

If your users have a Microsoft 365 Business license or an Enterprise E1 or E3 license without Audio Conferencing, you can assign the free Audio Conferencing license to them. The free Audio Conferencing offer is available to small and medium businesses of up to 300 users for 12 months, starting October 1, 2020. To learn more, see [Teams add-on licenses](teams-add-on-licensing/microsoft-teams-add-on-licensing.md)

> [!NOTE]
> If you have Enterprise E5 or Microsoft 365 Business Voice, you won't be able to use the free Audio Conferencing offer because these licenses already include Audio Conferencing.

In this article, we'll walk you through how to set up Audio Conferencing. You only need to set up Audio Conferencing for people who plan to schedule or lead meetings. Meeting attendees who call in to meetings don't need licenses or other setup. To learn more, see [Audio Conferencing](audio-conferencing-in-office-365.md).

## Step 1: Get Audio Conferencing licenses

Get one Audio Conferencing license for each person who will lead meetings. Use the Microsoft 365 admin center to do this.

1. In the Microsoft 365 admin center, go to **Billing** > **Purchase services**, and then at the bottom of the page, select **Add-ons**. 
2. Select **Microsoft 365 Audio Conferencing** > **Details**.
3. Enter the number of licenses you need for your meeting organizers, and then complete your order.

> [!NOTE]
> Clear or select the **Automatically assign to all of your users with no licenses**, depending on whether you want to automatically assign an Audio Conferencing license to all users who don't have this license.

## Step 2: Assign an Audio Conferencing license to users who lead meetings

Assign a license to each person who will lead meetings. Use the Microsoft 365 admin center to do this.

### Assign a license to one user

1. In the Microsoft 365 admin center, go to **Users** > **Active users**.  
2. Select the row of the user you want to assign the license to, and then in the pane, select **Licenses and Apps**.
3. Select the **Microsoft 365 Audio Conferencing** check box, and then select **Save changes**. 

### Assign a license to multiple users

1. In the Microsoft 365 admin center, go to **Users** > **Active users**.  
2. Select the circles next to the users you want to assign the license to, and then select **Manage product licenses**.
3. In the **Manage product licenses** pane, select **Assign more**.
4. Select the **Microsoft 365 Audio Conferencing** check box, and then select **Save changes**.  

## Step 3: Find or get a phone number for your conferencing bridge

You'll need a phone number (also called a service number) for your conferencing bridge so that it can be used in meeting invitations. You can use a **shared number** or a **dedicated number**. Both types of numbers can be used by any caller to join a meeting.

### Shared numbers

A shared number is a number that's shared across all organizations. Toll numbers (where long-distance charges are applied) are automatically assigned as shared numbers when you set up Audio Conferencing. The number that's assigned as the default phone number of your conferencing bridge is a number from your country or region.

To find the default number that's assigned to your conferencing bridge, in the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Conference bridges**, and then find the number for the location that's nearest to you.

### Dedicated numbers

A dedicated number is a number that's available only to your users. You can get a dedicated toll number or toll-free number, and then assign it to your conferencing bridge.

There are a couple ways to get a dedicated number. You can get a number from Microsoft or transfer (port) an existing number from your current service provider to Microsoft. To learn more about how to do this, see [Getting service numbers](getting-service-phone-numbers.md).

> [!NOTE]
> If you use a toll-free number, you have to first assign a Communications Credits license to each person who will lead meetings. To learn more, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).

After you have your number, assign it to your conference bridge. Use the Microsoft Teams admin center to do this.

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Conference bridges**.
2. Select **Add**, and then select **Toll number** or **Toll-free number**.
3. In the **Add phone number** pane, select the number, and then select **Apply**.

## Step 4: Assign a dial-in number to users who lead meetings

Assign a dial-in number for each person who will lead meetings. Use the Microsoft Teams admin center to do this.

1. In the left navigation of the Microsoft Teams admin center, select **Users**, click the display name of the user, and select **Edit**.
2. Select **Edit** next to **Audio Conferencing**, and then in the **Audio Conferencing** pane, select a number in the **Toll number** or **Toll-free** number lists, and then select **Apply**.

## Step 5: Schedule a Teams meeting in Outlook

To schedule a meeting, in Outlook, go to **Calendar**, and then select the **New Teams meeting** button. The dial-in numbers that you set for the user and the conference ID are automatically added to the meeting invitation that's sent to meeting attendees.

To learn more, see [Schedule a Teams meeting in Outlook](https://support.microsoft.com/office/schedule-a-teams-meeting-from-outlook-883cc15c-580f-441a-92ea-0992c00a9b0f).

> [!NOTE]
> If you want, you can customize meeting invitations to add your company logo, links to your support website and legal disclaimer, and a text-only footer. See [Customize meeting invitations](meeting-settings-in-teams.md#customize-meeting-invitations).

## Related topics

- [Audio Conferencing](audio-conferencing-in-office-365.md)
- [Set up Audio Conferencing for Teams](set-up-audio-conferencing-in-teams.md)
- [Audio Conferencing common questions](audio-conferencing-common-questions.md)
- [Getting service numbers](getting-service-phone-numbers.md)
- [Teams add-on licenses](teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Assign licenses to users](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)
