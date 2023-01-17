---
title: "Manage the Bookings app in Microsoft Teams"
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: how-to 
ms.service: msteams 
search.appverid: 
searchScope:
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
  - Microsoft Cloud for Retail
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - microsoftcloud-healthcare
  - microsoftcloud-retail
  - m365solution-healthcare
  - m365solution-scenario
  - m365-frontline
  - tier2
  - highpri
  - m365initiative-meetings
ms.reviewer: 
description: Learn how to manage the Bookings app in Teams for users in your organization.
---

# Manage the Bookings app in Microsoft Teams

The Bookings app in Microsoft Teams offers a simple way to schedule in-person and virtual appointments. For example, healthcare visits, financial consultations, interviews, customer support, and education office hours. To learn more, see [Virtual Appointments with Teams and the Bookings app](/microsoft-365/frontline/bookings-virtual-appointments).

Schedulers can manage multiple department and staff calendars and communications with internal and external attendees, from a single experience. Virtual appointments are held via Teams meetings that offer robust videoconferencing capabilities.

## Prerequisites to use the Bookings app in Teams

* The Exchange mailbox is in Exchange Online. On-premises Exchange Server mailboxes aren't supported.
* Microsoft Bookings is available for the organization.
* Users have an appropriate license. Office 365 A3, A5, E1, E3, E5, F1, F3, Microsoft 365 A3, A5, E3, E5, F1, F3, and Business Standard are supported.
* All users of the Bookings app and all staff participating in meetings have a license that supports Teams meeting scheduling.
* [Software and browser prerequisites](hardware-requirements-for-the-teams-app.md).

## Availability of Bookings in Teams

The Bookings app for Teams is available on the desktop and web. It can be found under [Apps in Teams](https://teams.microsoft.com/l/app/4c4ec2e8-4a2c-4bce-8d8f-00fc664a4e5b?source=store-copy-link) and under **Manage Apps** in the Teams admin center.

## Control access to Bookings within your organization

There are several ways to control who has access to the Bookings app and to specific features of the app. You can make Microsoft Bookings app available or disable it from Microsoft 365 admin center. Alternately, you can create a Bookings app policy to allow select users to create Bookings calendars. See [Get access to Microsoft Bookings](/microsoft-365/bookings/get-access).

You can also [create a Teams app setup policy to pin the Bookings app for select users](teams-app-setup-policies.md).

## Recommended meeting policy settings

To enable the best experience for Bookings, create a Teams meeting policy to automatically admit **Everyone in your organization** and assign the policy to your staff. The policy allows staff to join the appointment automatically and enable the lobby experience for external attendees. See [how to automatically admit people to meetings](meeting-policies-participants-and-guests.md#automatically-admit-people).

For more information about meeting policies, see [Manage meeting policies in Teams](meeting-policies-in-teams.md) and [Meeting policies and meeting expiration in Teams](meeting-expiration.md).

## SMS text notifications

![Information icon](media/info.png) **This feature is moving to [Teams Premium](teams-add-on-licensing/licensing-enhance-teams.md) (Preview). Users can continue using this feature during the preview period. After the preview, users need a Teams Premium license.**

> [!NOTE]
> We'll be providing unlimited SMS notifications through March 1, 2023 (previously January 31, 2023) for customers with Bookings licenses. As we get closer to the end of the promotion period, we'll provide additional details on licensing requirements. Contact your account team or support to receive pricing details after the promotion period.

You can control whether SMS text notifications can be sent to external attendees for virtual appointments scheduled by your staff in your organization.

By default, this setting is on, and SMS text notifications are enabled for all Bookings calendars in your organization. Keep in mind that Bookings admins and schedulers can later choose to turn off or turn on SMS notifications on an as-needed basis in [scheduled appointment types](/microsoft-365/frontline/bookings-virtual-appointments#scheduled-appointment-type) and scheduled individual appointments.

To configure this setting, go to the Microsoft 365 admin center \> **Settings** \> **Org settings**, and then choose **Bookings**. Select or clear the **Allow Microsoft to send SMS text message notifications** check box.

Learn more about how to [configure SMS text notifications for your organization](/microsoft-365/bookings/turn-bookings-on-or-off).

## Optional staff approvals setting

You can require staff to opt in before Bookings shares their schedule availability information and before others can schedule an appointment with them.

To enable this setting, go to the Microsoft 365 admin center \> **Settings** \> **Org settings**, and then choose **Bookings**. Select the **Require staff approvals** check box.

With this setting turned on, staff receive an email in which they're requested to approve membership to a booking calendar.  

Learn more about [how to configure the staff approvals setting](/microsoft-365/bookings/turn-bookings-on-or-off).

## Changing your default domain when setting up a Bookings mailbox

When setting up a Bookings mailbox, the default email domain of your Microsoft 365 or Office 365 organization is used. However, the default domain may cause problems when sending meeting invites to external recipients. For example, your invite may get flagged as spam and moved to the recipient’s junk folder, so the recipient might never see your invite.

We recommend that you change the default domain before you create your Bookings mailbox. See [Domains FAQ](/microsoft-365/admin/setup/domains-faq#how-do-i-set-or-change-the-default-domain-in-microsoft-365).

If you need to change the default domain after creating your Bookings mailbox, use PowerShell.

```powerShell
Set-Mailbox -identity business@domain.onmicrosoft.com -WindowsEmailAddress business@domain.com -EmailAddresses business@domain.com
```

To learn more, see [Set Mailbox](/powershell/module/exchange/mailboxes/set-mailbox).

> [!NOTE]
> If you're using an Exchange hybrid configuration, we recommend that you thoroughly test mail flow between on-premises Exchange and Exchange Online when changing the default domain.

## Send feedback

We welcome your feedback on:

* User experience or ease of use
* Feature gaps or missing functionality
* Bugs or issues
  
To send feedback, select the **Help** option at bottom of the Teams left navigation bar, and then select **Report a Problem** for **ALL** issues. Indicate at the beginning of your feedback report that you're sending feedback about "Bookings" so we can easily identify Bookings issues.

## Related articles

[Manage the join experience for Teams Virtual Appointments on browsers](/microsoft-365/frontline/browser-join)

[Bookings documentation for end users](https://support.office.com/article/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-US&rs=en-US&ad=US#PickTab=Bookings)
