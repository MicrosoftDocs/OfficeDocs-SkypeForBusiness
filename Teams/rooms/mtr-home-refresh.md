---
title: Microsoft Teams Rooms home screen design refresh
ms.author: tonysmit
author: tonysmit
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.date: 10/04/2023
ms.topic: quickstart
ms.service: msteams
ms.subservice: itpro-rooms
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - Tier1
  - M365-collaboration
  - Teams_ITAdmin_Rooms
description: Learn about the improvements to the Microsoft Teams Rooms on Windows home screen design.
---

# Microsoft Teams Rooms home screen design refresh

Microsoft Teams Rooms on Windows version 4.16 and later includes a refreshed home screen design that adds a calendar to front-of-room displays, quick access to more commonly used actions on consoles, additional built-in themes, and better consistency with other Teams devices.

The refreshed home screen design is available to anyone who has Teams Rooms on Windows version 4.16 or later. The refreshed home screen is opt-in on Teams Rooms version 4.16.  To see the refreshed home screen in Teams Rooms version 4.16, you need to [manually enable it](#enable-refreshed-home-screen-design).

> [!IMPORTANT]
> On Teams Rooms versions 4.17 and later, the refreshed home screen is **enabled** by default.

Before you enable the refreshed home screen design in Teams Rooms version 4.16, check the following:

- **Integrated Exchange calendar** - The refreshed home screen changes how the calendar on Teams Rooms devices communicates with Exchange. The new method aligns with Teams desktop, web, and mobile clients. Make sure meetings that appear in Outlook or Outlook on the web are correctly reflected in your Teams clients. For information about Exchange and Teams, see [How Exchange and Microsoft Teams interact](../Exchange-Teams-interact.md)
  > [!WARNING]
  > If you're using Teams Rooms with an on-premises Exchange server, we recommend that you don't enable the refreshed home screen design on Teams Rooms version 4.16. The new calendar included with the refreshed home screen design isn't supported with on-premises Exchange servers in Teams Rooms version 4.16. On-premises Exchange servers with Hybrid Configuration and AutoDiscover v2 published externally is supported in Teams Rooms version 4.17 and later. For information on how on-premises mailboxes work with Teams, see [Microsoft Teams and on-premises mailboxes](https://techcommunity.microsoft.com/t5/microsoft-teams-community-blog/microsoft-teams-and-on-premises-mailboxes-part-1-how-do-teams/ba-p/2229851)
- **Custom themes** - A calendar has been added to front-of-room display with the refreshed home screen. If you have a custom theme that has logos or information that users need to see, we recommend that you don't enable the refreshed home screen design until you've [updated your theme](#custom-background-guidelines) or that you [remove the calendar from the front-of-room display](#hide-front-of-room-calendar-display).

You can temporarily roll back to the previous Teams Rooms home screen design if you need to do so by following the information in [Roll back to legacy home screen design](#roll-back-to-legacy-home-screen-design). Keep in mind, however, that new features are being added only to the refreshed home screen going forward. We recommend that you move to the refreshed home screen as soon as possible to take advantage of these new investments.

## Custom background guidelines

For custom background guidelines, see [Set up and manage Teams Rooms on Windows custom backgrounds](custom-backgrounds.md).

## Updating Teams Rooms device configuration

To apply the configuration changes included in this article to your Teams Rooms for Windows devices, you need to use the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

### Enable refreshed home screen design

To enable the refreshed home screen design, add the following to your XML configuration file:

> [!NOTE]
> The `</TeamsRoomsNewExperience>` setting will be removed in a future release.

```xml
<TeamsRoomsNewExperience>true</TeamsRoomsNewExperience> 
```

### Hide front-of-room calendar display

To hide the calendar on your front-of-room display, add the following to your XML configuration file:

```xml
<RemoveFoRCalendar>true</RemoveFoRCalendar> 
```

### Roll back to legacy home screen design

To roll back to the legacy home screen design, add the following to your XML configuration file:

> [!NOTE]
> The `</TeamsRoomsNewExperience>` setting will be removed in a future release.

```xml
<TeamsRoomsNewExperience>false</TeamsRoomsNewExperience> 
```
