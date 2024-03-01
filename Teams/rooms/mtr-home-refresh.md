---
title: Microsoft Teams Rooms home screen design refresh
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
ms.reviewer: henrikalim
ms.date: 10/04/2023
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: Learn about the improvements to the Microsoft Teams Rooms on Windows home screen design.
---

# Microsoft Teams Rooms on Windows home screen design refresh

Microsoft Teams Rooms on Windows version 4.17 and later includes a refreshed home screen design that adds a calendar to front-of-room displays, quick access to more commonly used actions on consoles, additional built-in background options, and better consistency with other Teams devices.

To ensure you get the best home screen experience, check the following:

- **Integrated Exchange calendar** - The refreshed home screen changes how the calendar on Teams Rooms devices communicates with Exchange. The new method aligns with Teams desktop, web, and mobile clients. Make sure meetings that appear in Outlook or Outlook on the web are correctly reflected in your Teams clients. For information about Exchange and Teams, see [How Exchange and Microsoft Teams interact](../Exchange-Teams-interact.md).

  > [!WARNING]
  > Only on-premises Exchange servers with Hybrid Configuration and AutoDiscover v2 published externally is supported on the new Teams Rooms on Windows home screen experience, which is consistent with how other Teams clients connect with Exchange. If you're using Teams Rooms with an on-premises Exchange server, we recommend that you review how on-premises mailboxes work with Teams to avoid any disruption on your calendar experience, [Microsoft Teams and on-premises mailboxes](https://techcommunity.microsoft.com/t5/microsoft-teams-community-blog/microsoft-teams-and-on-premises-mailboxes-part-1-how-do-teams/ba-p/2229851)

- **Custom backgrounds** - A calendar component has been added to the front-of-room display with the refreshed home screen to ensure that the room schedule is easily visible. If you have a custom background that has logos or information that users need to see, we recommend that you [update your background based on the latest guidelines ](#custom-background-guidelines)or that you [remove the calendar from the front-of-room display](#hide-front-of-room-calendar-display).

## Custom background guidelines

For custom background guidelines, see [Set up and manage Teams Rooms on Windows custom backgrounds](custom-backgrounds.md).

## Updating Teams Rooms device configuration

To apply the configuration changes included in this article to your Teams Rooms for Windows devices, you need to use the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

### Hide front-of-room calendar display

To hide the calendar on your front-of-room display, add the following to your XML configuration file:


```xml
<RemoveFoRCalendar>true</RemoveFoRCalendar> 
```


