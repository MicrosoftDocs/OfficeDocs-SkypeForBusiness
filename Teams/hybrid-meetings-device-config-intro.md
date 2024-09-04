---
title: "Step 5 - Overview"
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
ms.reviewer: sohailta
ms.date: 02/25/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection:
- m365solution-teamshybrid
- m365solution-scenario
- m365initiative-meetings
- teams-rooms-devices
f1.keywords:
- Teams hybrid
- remote work
- Teams meetings
ms.localizationpriority: high
description: Step through the complete process of setting up a new Teams Rooms device in your organization.
---

# Overview

:::image type="content" source="media/hybrid-audience-itpro-small.png" alt-text="IT Pro audience" border="false":::

After you've installed and connected all of your devices, it's time to configure the Teams Rooms console.

In order for Teams Rooms to work with your organization, you need to complete a few steps. These steps set up an account and license for your Teams Room, tell it how to handle meeting requests, and tell it when it and participants can and can't do in a meeting.

## Before you begin

- You need to be a Global admin and a Teams admin to complete the steps below. For more information, see [About Microsoft 365 admin roles](/microsoft-365/admin/add-users/about-admin-roles).

> [!IMPORTANT]
>Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

## Set up the Teams Rooms account

The following steps show you how to purchase a license for your Teams Rooms console, create an account for it, and then assign the license to it. Each Teams Rooms console needs its own account and license to work properly. The account you create will show up in the organization's address list as a room available for reservation in Outlook.

[Step 1 - Purchase a license for the Teams Rooms console](hybrid-meetings-device-config-license.md)

[Step 2 - Create a resource account](hybrid-meetings-device-config-account.md)

[Step 3 - Assign a meeting room license](hybrid-meetings-device-config-assign.md)

## Configure mailbox and account properties

To allow people in your organization to book the Teams Room, you need to configure a few properties on the account the console uses. Setting these properties allows Teams Rooms to process meeting requests automatically the way you want, remove or add information shown about the meeting on the console, and set what should be included in meeting request responses.

Password expiration needs to be turned off on the Teams Rooms resource account so that the console is able to log into the account.

[Step 4 - Configure mailbox properties](hybrid-meetings-device-config-mailbox.md)

[Step 5 - Turn off password expiration](hybrid-meetings-device-config-password.md)

## Configure meeting policies and options

Meeting policies are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization. For example, you can control whether participants can share video, allow or block anonymous participants, control whether meetings can be recorded and how those recordings are stored, and so on.

Calendar options let you organize Teams Rooms locations so you can, for example, show only meeting rooms for users in a specific geographical location. You can also set the room capacity and other information that can be shown in Outlook.

[Step 6 - Configure meeting policies](hybrid-meetings-device-config-policies.md)

[Step 7 - Configure calendar options](hybrid-meetings-device-config-calendar.md)

> [!div class="nextstepaction"]
> [Next step](hybrid-meetings-device-config-license.md)
