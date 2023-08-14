---
title: Virtual appointment meeting template in Microsoft Teams
author: lana-chin
ms.author: v-chinlana
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: 
ms.date: 04/11/2023
search.appverid: MET150
searchScope:
  - Microsoft Teams
audience: admin
description: Learn how to manage the Virtual appointment meeting template for Teams users in your organization.
ms.localizationpriority: medium
MS.collection: 
  - Teams_ITAdmin_Help
  - M365-collaboration
  - m365-frontline
appliesto: 
  - Microsoft Teams
---

# Virtual appointment meeting template in Microsoft Teams

![Information icon](media/info.png) **Some features described in this article require [Teams Premium](teams-add-on-licensing/licensing-enhance-teams.md)**.

## Overview

The Virtual appointment template is a default meeting template in Microsoft Teams that your users can use to schedule virtual appointments with customers, clients, and other people outside your organization. For example, use it to schedule and conduct interviews, mentorship sessions, financial consultations, virtual shopping experiences, and more.

This article gives you an overview of how to manage the Virtual appointment meeting template<!--in the Teams admin center-->.

## Use meeting template policies to specify which users can use the template

You use meeting template policies in the Teams admin center to control which meeting templates are available to users in your organization. By default, the Global policy allows users to see and use all meeting templates, including the Virtual appointment template and any custom templates that you created.

If you want to make the Virtual appointment template available to specific users or groups of users in your organization, you can create a custom meeting template policy, and then assign it to those users or groups.

To learn more, see [Manage meeting templates in Teams](manage-meeting-templates.md).

## Control access to SMS notifications in the template

![Information icon](media/info.png) **This is a [Teams Premium](teams-add-on-licensing/licensing-enhance-teams.md) feature. Meeting organizers must have a Teams Premium license to use this feature.**.

> [!NOTE]
> This feature is currently only available in the United States. Your users can only send SMS text notifcations to people who have a valid United States phone number (+1 country code). SMS text notifications are sent in English.

You can control whether your users can choose to send SMS text notifications to external guests in meetings that they schedule using the template. When this feature is enabled for a user, they'll see  the SMS notifications setting in the template.

- If the user chooses **Send text notifications** (the default setting), external guests will receive appointment confirmation, update, and reminder text messages that include the Teams meeting join link and appointment details.
- If the user chooses **Don't send text notifications**, external guests won't receive text messages about their appointment.

You use PowerShell to control access to this feature in your organization by setting the following policy:

### Things to consider

If a user doesn't have access to this feature, either through policy restrictions or if they don't have a Teams Premium license:

- The SMS notifications setting isn't visible in the template when they schedule a new meeting or when they edit an existing meeting in which the SMS notifications feature was previously enabled.
- If the user chose **Send text notifications** when they scheduled a meeting, and then their access to the feature is disabled, no additional text messages are sent to the external guest.

View the [SMS notifications usage report](/microsoft-365/frontline/sms-notifications-usage-report) in the Teams admin center get an overview of SMS notifications usage in your organization.

## Meeting options available to external guests

When users in your organization use the template to schedule a virtual appointment, external guests get a tailored meeting invitation that includes a **Join appointment as a guest** button and other appointment details. They can use this button to easily join from any device without having to download and install Teams.

Keep in mind that some Teams meeting options may not apply to external guests or to any person who joins using the **Join appointment as a guest** button. The following meeting options are supported for guests to join:

- **Who can bypass the lobby**: The **Everyone** setting allows external guests to bypass the lobby.
- **Choose co-organizers**
- **Record automatically**
- **Allow meeting chat**: Set to **Disabled** if you want to prevent a meeting chat before, during, and after the meeting.

People within your organization receive a meeting invitation, and the appointment appears in their Teams and Outlook calendar, from where they can easily join as in any other Teams meeting. All Teams meeting options apply to attendees who join using the Teams meeting link in the meeting invitation or from the Teams or Outlook calendar.

> [!NOTE]
>External guests need pop-up notifications allowed on their mobile and web browser for the browser-based Teams experience to function properly. This setting will show a pop-up asking for permission to access the microphone and camera for the meeting, which is required for the meeting to begin.

To learn more about how to use the Virtual appointment meeting template and about the user experience, see [Use a Teams meeting template to create a Virtual Appointment](https://support.microsoft.com/office/6a9e8cbb-c0ed-4598-851e-3b1750a4a747).

## Related articles

- [Overview of custom meeting templates in Teams](custom-meeting-templates-overview.md)
