---
title: Virtual appointment meeting template in Microsoft Teams
author: LanaChin
ms.author: v-lanachin
manager: samanro
ms.topic: conceptual
ms.service: msteams
ms.reviewer: 
search.appverid: MET150
searchScope:
  - Microsoft Teams
audience: admin
description: Learn how to manage the Virtual appointment meeting template for Teams users in your organization.
ms.localizationpriority: medium
MS.collection: 
  - Teams_ITAdmin_Help
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Virtual appointment meeting template in Microsoft Teams

## Overview

The Virtual appointment template is a default meeting template in Microsoft Teams that your users can use to schedule virtual appointments with customers, clients and other people outside your organization. For example, use it to schedule and conduct interviews, mentorship sessions, financial consultations, virtual shopping experiences, and more.

The template allows you to specify values for meeting settings that meeting organizers typically control. It gives you the flexibility to apply default settings and enforce settings. You can choose to lock settings so meeting organizers can't change them when they use the template.

With this template, you can enable a consistent experience across your organization for virtual appointments scheduled within Teams and help enforce compliance requirements.

This article gives you an overview of how to view and manage the Virtual appointment meeting template in the Teams admin center.

## View or change Virtual appointment meeting template settings

1. In the left navigation of the Teams admin center, go to **Meetings** > **Meeting templates**.
1. Choose **Virtual appointment**, and then select **Edit**.
1. To make changes, select an option, and then configure the settings that you want. For each option, you can define the following settings:
    - **Default value**: The value that's applied to the virtual appointment when the template is used.
    - **Visibility**: Choose **Hide** or **Show** to specify whether the option is visible to meeting organizers in Teams meeting options.
    - **Lock status**: To prevent meeting organizers from changing the value that you set, choose **Lock**. To allow meeting organizers to change the value that you set, choose **Unlock**.
1. Review your changes, and then choose **Save**.

## Manage the Virtual appointment meeting template

You use meeting template policies in the Teams admin center to control which meeting templates are available to users in your organization. By default, the Global policy allows users to see and use all meeting templates, including the Virtual appointment template, and any custom templates that you created.

If you want to make the Virtual appointment template available to specific users or groups of users in your organization, you can create a custom meeting template policy, and then assign it to those users or groups.

To learn more, see [Manage meeting templates in Teams](manage-meeting-templates.md).

## User experience

When users in your organization use the meeting template to schedule a virtual appointment, people outside your organization (external guests) get a tailored meeting invitation that includes a **Join appointment as a guest** button and other appointment details. They can use this button to easily join from any device without having to download and install Teams.

Keep in mind that some Teams meeting options may not apply to external guests or to any person who joins using the **Join appointment as a guest** button. The following meeting options are supported for guest join:

- **Who can bypass the lobby**: The **Everyone** setting allows external guests to bypass the lobby.
- **Choose co-organizers**
- **Record automatically**
- **Allow meeting chat**: Set to **Disabled** to prevent meeting chat before, during, and after the meeting.

People within your organization receive a meeting invitation and the appointment appears in their Teams and Outlook calendar, where they can easily join as in any other Teams meeting. All Teams meeting options apply to attendees who join using the Teams meeting link in the meeting invitation or from the Teams or Outlook calendar.

To learn more about how to use the Virtual appointment template and the user experience, see [Use a Teams meeting template to create a virtual appointment]().

## Related articles

- [Overview of custom meeting templates in Teams](custom-meeting-templates-overview.md)
- [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)
