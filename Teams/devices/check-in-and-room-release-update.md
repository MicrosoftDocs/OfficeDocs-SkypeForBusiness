---
title: Check in and room release update
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: eveigrimshaw
ms.date: 05/02/2024
ms.topic: article
audience: Admin
appliesto: 
  - Microsoft Teams
ms.service: msteams
ms.subservice: itpro-devices
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
search.appverid: MET150
ms.localizationpriority: medium
description: This article provides guidance on how to enable check-in and room release Teams panels devices.
---
# Check-in and room release on Microsoft Teams panels

When check-in and room release are enabled, users must check in at the room they reserved at the start of the meeting. They can do so on Teams panels using the 'Check in' button or, when Teams panels share a resource account with Teams Rooms, they can do so by joining a meeting on Teams Room. If a user doesn't check in within a set amount of time after the meeting start time, the meeting room declines the meeting invite, sends a cancellation message to the meeting organizer, and the room becomes available for others to reserve.

This feature can be used in a standalone Teams panel deployment or on a Teams panel that is sharing an account with Teams rooms. For rooms with multiple panels, check-in and room release will only work if the panel devices are all on app version 1449/1.0.97.2024050205 or later. For additional functionalities like check-in notifications, you can also pair Teams panels with Teams Rooms on Android with app version 1449/1.0.96.2022011305 or later.

The shared mailbox associated with the Teams panel needs to have the correct time zone set for this feature to work correctly. For information about how to set the time zone for shared mailboxes, see [Time zone settings for shared mailboxes in Outlook on the web](/exchange/troubleshoot/outlook-on-the-web-issues/shared-mailboxes-time-zone-setting).

## Enable check-in and room release

Check-in and room release is off by default. To turn it on,  

1. On the Teams panel, sign in using your admin credentials.  

1. Go to **Settings > Device settings > Admin settings > Teams admin settings > Meetings**.

1. Turn on **Release room if no one checks in**.

1. To adjust the amount of time users have to check in before the room is released, go to **Release after:** and select an option from the dropdown.  

In addition, you can use configuration profiles to apply this feature to a set of devices. For more information, see [Use configuration profiles in Teams](device-management.md#use-configuration-profiles-in-teams).

Finally, for devices on app version 1449/1.0.97.2024050205 or later, you can also edit this setting through Powershell using the [Set-CalendarProcessing cmdlet](/powershell/module/exchange/set-calendarprocessing?branch=main&branchFallbackFrom=pr-en-us-14644&view=exchange-ps). 

__Note:__ For devices on app version 1449/1.0.97.2024050205 or later, it is strongly recommended to change this setting through any of the methods listed only during a 48-hour period where there are no meetings so that the change can sync to the backend.

## Turn on check-in notifications

**Note:** This feature is currently only available on Teams panels that are paired with a Teams Room on Android. The Teams panel and Teams room must be signed into the same resource account. See **[Pair a Teams panel with a Microsoft Teams Room on Android](/editor/MicrosoftDocs/OfficeDocs-SkypeForBusiness-pr/Teams%2Fdevices%2Fcheck-in-and-room-release.md/main/08c71f9d-8c3a-87ca-c670-832cbb3cc9f3/use-teams-panels.md)** to learn more.

Check-in notifications are sent when a meeting is continuing past its reserved time slot. Once a user from the next meeting checks in, the notification will appear on the front of room display at their scheduled meeting start time to let the previous meeting participants know their reservation is over and people are waiting for the space.

To turn on check-in notifications,

1. On the Teams panel, sign in using your admin credentials.

1. Go to **Settings > Device settings > Admin settings > Teams admin settings > Meetings**.

1. Go to **Check-in** and turn on **Send check-in notification**

## Related topics

- [How to use Microsoft Teams panels](use-teams-panels.md)

- [Microsoft Teams panels](teams-panels.md)

