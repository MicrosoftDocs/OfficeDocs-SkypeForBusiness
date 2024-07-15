---
title: Remotely configure layout, scale, and resolution on Teams Rooms displays
ms.author: tonysmit
author: mstonysmith
ms.reviewer: yoojinjung
ms.date: 07/15/2024
manager: pamgreen
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
description: Remotely configure the scale, resolution, and default layout of displays on Microsoft Teams Rooms systems.
---

# Remotely configure layout, scale, and resolution on Teams Rooms displays

If you have multiple Teams Rooms systems deployed in your organizations, you can configure display settings such as scale, resolution, and default layout, remotely using an XML configuration file. This XML configuration file can be deployed from a central location to your Teams Rooms systems. When the XML file is deployed to a Teams Rooms system, the configuration settings defined within it will be applied the next time the system is restarted.

For more information about the Teams Rooms XML configuration file, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

## Set default meeting layout for single display mode

If you only have one front of room display and the Dual monitor mode is turned OFF on Teams admin center or XML, you can set the default meeting layout that's used when a meeting starts. If you don't set a default meeting layout for a room, the default layout will be set to Gallery. To change the default meeting layout, add one of the two following options to your XML configuration file:
- `<DefaultFoRExperience>1</DefaultFoRExperience>` Front row
- `<SingleFoRDefaultContentLayout>0</SingleFoRDefaultContentLayout>` Focus on content (you will see Gallery until someone shares content)

For example, to default to the Gallery (Content and people) layout, use the following:

```xml
<SingleFoRDefaultContentLayout>1</SingleFoRDefaultContentLayout>
<DefaultFoRExperience>0</DefaultFoRExperience>
```

End-users can switch from the default display layout using the view switcher during meetings.

## Set default meeting layout for dual display mode

If you have two front-of-room displays and the Dual monitor mode is turned ON on Teams admin center or XML, you can choose the default meeting layout between Gallery and Front row. Focus on content is not available on dual display mode. If you don't set a default meeting layout for a room, the default layout will be set to Gallery. To see Front row as the default layout, add `<DefaultFoRExperience>1</DefaultFoRExperience>` to your XML configuration file.

For example, to default to the Gallery layout, use the following:

```xml
<DefaultFoRExperience>0</DefaultFoRExperience>
```

End-users can switch from the default display layout using the view switcher during meetings.

## Set front-of-room scale and resolution

You can set the scale and resolution for your main front-of-room display. If you have dual displays, you can and set the scale and resolution for an extended display too.

You can manually set the display resolution on main and extended displays. Those options are `MainFoRDisplayResolution` and `ExtendedFoRDisplayResolution` respectively. Both options accept two numerical values that represent the width and height of a display, separated by a comma. For example, to specify a display resolution of width of 1920 and a height of 1080, the value to enter would be `1920,1080`. If you enter display resolution values that the display doesn't support, the values will be ignored.

You can manually set the display scaling on main and extended displays. Those options are `MainFoRDisplayScaling` and `ExtendedFoRDisplayScaling` respectively. Both options accept the values 100 (recommended), 125, 150, 175, 200, 225, 250, and 300. If you enter a value the display doesn't support, it'll default to the closest supported value.

### Enable customized scale and resolution for front-of-room displays

To set the scale and resolution for your displays, you first need to tell Teams that you want to do so by adding `<EnableResolutionAndScalingSetting>true</EnableResolutionAndScalingSetting>` to the XML file. After you've added this line to the XML file, you can set the scale and resolution for your main display, and your extended display if you have one.

> [!IMPORTANT]
> If you enable customized scale and resolution and you have dual front-of-room displays, you need to specify both `MainFoRDisplay` and `ExtendedFoRDisplay` and their respective options. If you don't specify both, the custom configuration will be ignored.

### Set scale and resolution for your main front-of-room display

To set the scale and resolution for your main front-of-room display, add the following to your XML configuration file

```xml
<MainFoRDisplay>
      <MainFoRDisplayResolution>1920,1080</MainFoRDisplayResolution> 
      <MainFoRDisplayScaling>100</MainFoRDisplayScaling> 
</MainFoRDisplay>
```

### Set scale and resolution for your extended front-of-room display

To set the scale and resolution for your extended front-of-room display, add the following to your XML configuration file:

```xml
<ExtendedFoRDisplay> 
    <ExtendedFoRDisplayResolution>1920,1080</ExtendedFoRDisplayResolution> 
    <ExtendedFoRDisplayScaling>100</ExtendedFoRDisplayScaling> 
</ExtendedFoRDisplay>  
```

