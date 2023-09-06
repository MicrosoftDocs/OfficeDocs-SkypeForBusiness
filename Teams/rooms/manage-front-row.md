---
title: Remotely configure front row layout on Teams Rooms
ms.author: tonysmit
author: tonysmit
ms.reviewer: sohailta
ms.date: 01/24/2023
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.subservice: itpro-rooms
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
description: Remotely configure the front row layout on Microsoft Teams Rooms systems.
---

# Remotely configure front row on Teams Rooms

Front row is an inclusive meeting layout available on Microsoft Teams Rooms systems that fosters a deeper connection between in-person and virtual meeting participants. Front row allows you to maximize screen real estate so you can see both people, content, and chat simultaneously.

If you have multiple Teams Rooms systems deployed in your organizations, you can configure front row on those systems remotely using an XML configuration file. This XML configuration file can be deployed from a central location to your Teams Rooms systems. When the XML file is deployed to a Teams Rooms system, the configuration settings defined within it will be applied the next time the system is restarted.

For more information about the Teams Rooms XML configuration file, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

## Turn off front row

Front row is enabled by default. Turn off Front row if you don't want to allow end-users to use Front row in a certain room. To do disable front row, add `<FrontRowEnabled>false</FrontRowEnabled>` to your XML configuration file.

## Set front row as the default layout

If you don't set a default display layout for a room in your XML configuration, the default layout will be set to Gallery. To see Front row as the default layout, add `<DefaultFoRExperience>1</DefaultFoRExperience>` to your XML configuration file.

End-users can switch from the default display layout using the view switcher during meetings.

## Set front row size

You can control the size of front row to give more or less space to meeting participant video or to meeting content. To set the front row size, add `<FrontRowVideoSize>` to your XML configuration file. You can set `<FrontRowVideoSize>` to `small`, `medium`, or `large`. The default is `medium`. For example, to set the front row size to large, use `<FrontRowVideoSize>large</FrontRowVideoSize>`.
