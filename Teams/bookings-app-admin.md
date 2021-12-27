---
title: "Manage the Bookings app in Microsoft Teams"
author: dmaguire
ms.author: serdars
manager: serdars
audience: ITPro
ms.topic: article 
ms.service: msteams 
search.appverid: 
searchScope:
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - microsoftcloud-healthcare
  - m365solution-healthcare
  - m365solution-scenario
ms.reviewer: 
description: Learn how to manage the Bookings app in Teams for users in your organization.
---

# Manage the Bookings app in Microsoft Teams

The Bookings app in Microsoft Teams offers a simple way to schedule in-person and virtual appointments, such as healthcare visits, financial consultations, interviews, customer support, education office hours, and much more. To learn more, see [Virtual visits with  Teams and the Bookings app](expand-teams-across-your-org/bookings-virtual-visits.md).

Schedulers can manage multiple department and staff calendars, as well as communications with internal and external attendees, from a single experience. The virtual appointments themselves are held via Microsoft Teams meetings, which offers robust videoconferencing capabilities.

> [!NOTE]
> Only schedulers need to have the Bookings app installed in Teams. Staff who conduct or participate in virtual appointments don't need the app. They can simply join appointments from their Outlook or Teams calendar or from the Teams meeting link in their booking confirmation email.

## Prerequisites for using the Bookings app in Teams

- The Exchange mailbox must be in Exchange Online. On-premises Exchange Server mailboxes aren't supported.

- Microsoft Bookings must be turned on for the organization.

- Users must have an appropriate license. Office 365 A3, A5, E3, E5, F1, F3, Microsoft 365 A3, A5, E3, E5, F1, F3, and Business Standard are supported.

- All users of the Bookings app and all staff participating in meetings must have a license that supports Teams meeting scheduling.

- Your systems must meet all [software and browser prerequisites](hardware-requirements-for-the-teams-app.md).

## Availability of Bookings in Teams

Microsoft Bookings app for Teams is available on the desktop and web. It can be found under [Apps in Teams](https://teams.microsoft.com/l/app/4c4ec2e8-4a2c-4bce-8d8f-00fc664a4e5b?source=store-copy-link) and under **Manage Apps** in the Teams admin center.

### Control access to Bookings within your organization

There are several ways to control who has access to the Bookings app and to specific features of the app.

To learn how to turn Microsoft Bookings on or off in the Microsoft 365 admin center and how to create a Bookings app policy to allow selected users to create Bookings calendars, see [Get access to Microsoft Bookings](https://support.microsoft.com/en-us/office/get-access-to-microsoft-bookings-5382dc07-aaa5-45c9-8767-502333b214ce).

You can also [create a Teams app setup policy to pin the Bookings app for select users](teams-app-setup-policies.md).

## Recommended meeting policy settings

To enable the best experience for Bookings, create a Teams meeting policy to automatically admit **Everyone in your organization** and assign the policy to your staff. Doing this allows staff to join the appointment automatically and enable the lobby experience for external attendees. Learn more about how to [automatically admitting people to meetings](meeting-policies-participants-and-guests.md#automatically-admit-people).

## Optional staff approvals setting

As an extra privacy setting, you can choose to require staff to opt in before their schedule availability information is shared through Bookings and before they can be booked for an appointment.  

To enable this setting, go to **Microsoft 365 admin center** \> **Settings** \> **Settings**, and then select **Bookings**.

With this setting turned on, staff will receive an email in which they're' asked to approve membership to a booking calendar.  

This feature is gradually being rolled out worldwide to Microsoft 365 and Office 365 customers. If all options aren't yet available in your environment, check back soon.

## Changing your default domain when setting up Bookings mailboxes

When setting up a Bookings mailbox, the default email domain of your Microsoft 365 or Office 365 organization is used. However, this can cause problems when sending meeting invites to external recipients; your invite might be flagged as spam and moved to the recipient’s junk folder, so the recipient might never see your invite.

We recommend that you change the default domain before you create your Bookings mailbox. For information on how to do this, see the [Domains FAQ](/microsoft-365/admin/setup/domains-faq#how-do-i-set-or-change-the-default-domain-in-office-365).

If you need to change the default domain after your Bookings mailbox has already been created, you can do so with PowerShell:

```PowerShell
Set-Mailbox -identity business@domain.onmicrosoft.com -WindowsEmailAddress business@domain.com -EmailAddresses business@domain.com
```

For more information, see the PowerShell documentation for the [Set-Mailbox](/powershell/module/exchange/mailboxes/set-mailbox) cmdlet.

> [!NOTE]
> If you're using an Exchange hybrid configuration, we recommend that you thoroughly test mail flow between on-premises Exchange and Exchange Online when changing the default domain.

## Sending feedback

We welcome your feedback on:

  - User experience or ease of use
  - Feature gaps or missing functionality
  - Bugs or issues
  
To send feedback, select the **Help** button near the bottom of the Teams left navigation bar, and then select **Report a Problem** for **ALL** issues. Indicate at the beginning of your feedback report that you're sending feedback about "Bookings" so we can easily identify Bookings issues.

## Related articles

[Manage the join experience for Teams virtual visits on mobile browsers](expand-teams-across-your-org/mobile-browser-join.md)

[Bookings documentation for end users](https://support.office.com/en-us/article/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-US&rs=en-US&ad=US#PickTab=Bookings)
