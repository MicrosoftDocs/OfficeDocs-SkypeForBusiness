---
title: Check-in and room release on Microsoft Teams panels
ms.author: dstrome
author: dstrome
manager: serdars
ms.reviewer: gary.lai
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-voice
  - Teams_ITAdmin_Devices
ms.topic: reference
search.appverid: MET150
description: This article provides guidance on how to enable check-in and room release Teams panels devices.
---

# Check-in and room release on Microsoft Teams panels

When check-in and room release are enabled, users check in on Teams panels at the room they reserved at the start of the meeting. If a user doesn’t check in within a set amount of time after the meeting start time, the meeting room declines the meeting invite, sends a cancellation message to the meeting organizer, and the room becomes available for others to reserve.  

## Requirements 

This feature can be used in a standalone Teams panel deployment. You can also pair Teams panels with Teams Rooms on Android with app version 1449/1.0.96.2022011305 or later for additional functionalities like check-in notifications.

The shared mailbox associated with the Teams panel needs to have the correct time zone set for this feature to work correctly. For information about how to set the time zone for shared mailboxes, see [Time zone settings for shared mailboxes in Outlook on the web](/exchange/troubleshoot/outlook-on-the-web-issues/shared-mailboxes-time-zone-setting).

## Enable check-in and room release 

Check-in and room release is off by default. To turn it on,  

1. On the Teams panel, sign in using your admin credentials.  

2. Go to **Settings > Device settings > Admin settings > Teams admin settings > Meetings**.

3. Turn on Release room if no one checks in.

4. To adjust the amount of time users have to check in before the room is released, go to **Release after:** and select an option from the dropdown.  

When Teams panels are paired with a Teams Room on Android, a user can check in joining the meeting on the Teams Room.  

## Turn on check-in notifications

> [!NOTE]
> This feature is currently only available on Teams panels that are paired with a Teams Room on Android. The Teams panel and Teams room must be signed into the same resource account. See [Pair a Teams panel with a Microsoft Teams Room on Android](use-teams-panels.md#pair-a-teams-panel-with-a-microsoft-teams-room-on-android) to learn more.  

Check-in notifications are sent when a meeting is continuing past its reserved time slot. Once a user from the next meeting checks in, the notification will appear on the front of room display at their scheduled meeting start time to let the previous meeting participants know their reservation is over and people are waiting for the space.  

To turn on check-in notifications,  

1. On the Teams panel, sign in using your admin credentials. 

2. Go to **Settings > Device settings > Admin settings > Teams admin settings > Meetings**.

3. Go to **Check-in** and turn on **Send check-in notification**.

## Related topics

- [How to use Microsoft Teams panels](use-teams-panels.md)

- [Microsoft Teams panels](teams-panels.md)
