---
title: Microsoft Teams Rooms home screen design refresh
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.date: 03/09/2023
ms.topic: quickstart
ms.service: msteams
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

The refreshed home screen design is available to anyone who has Teams Rooms on Windows version 4.16 or later. However, because the refreshed design makes changes to Exchange calendar integration and the layout of the Teams Rooms home screen, we haven't made it the default experience yet. To see the refreshed home screen in Teams Rooms version 4.16, you need to [manually enable it](#enable-refreshed-home-screen-design).

> [!IMPORTANT]
> The refreshed home screen is opt-in for Teams Rooms version 4.16. The refreshed home screen will become the default experience in a future release. Be sure to review the guidelines in this article, and update your custom themes if you have any, before the refreshed home screen becomes the default experience.

Before you enable the refreshed home screen design in Teams Rooms version 4.16, and before it becomes the default experience in a future release, check the following:

- **Integrated Exchange calendar** - The refreshed home screen changes how the calendar on Teams Rooms devices communicates with Exchange. Make sure meetings that appear in Outlook or Outlook on the web are correctly reflected in your Teams clients. For information about Exchange and Teams, see [How Exchange and Microsoft Teams interact](../Exchange-Teams-interact.md).
  > [!IMPORTANT]
  > If you're using Teams Rooms with an on-premises Exchange server, some calendar functionality is unavailable in Teams Rooms version 4.16. If you use your Teams Rooms devices to join forwarded meetings, third-party meetings, cross-tenant meetings, or Teams Live Events, we recommend that you don't enable the refreshed home screen design yet. These meetings scenarios will be supported when the refreshed home screen becomes the default experience in an upcoming release.
- **Custom themes** - A calendar has been added to front-of-room display with the refreshed home screen. If you have a custom theme that has logos or information that users need to see, we recommend that you don't enable the refreshed home screen design until you've [updated your theme](#custom-wallpaper-guidelines) or that you temporarily [remove the calendar from the front-of-room display](#hide-front-of-room-calendar-display).

If you want roll back to the previous Teams Rooms home screen design, see [Roll back to legacy home screen design](#roll-back-to-legacy-home-screen-design).

## Custom wallpaper guidelines

You can create a custom wallpaper for your Teams Rooms theme to represent your brand or to provide instructions to Teams Rooms users. The guidelines in this section apply to Teams Rooms on Windows version 4.16 and later devices that have the refreshed home screen enabled. If your device is running 4.15 and earlier, or if you haven't enabled the refreshed home screen, use the guidelines provided in [Custom theme images](xml-config-file.md#custom-theme-images).

Custom wallpapers need to be exactly 3840 x 1080 pixels in size, regardless of whether the wallpaper is used with a single front-of-room display or dual front-of-room displays. If used with a single front-of-room display, the left half of the image is used and the right half is cropped out. If used with a dual front-of-room display, the image is divided between the left and right front-of-room displays. 

**Single room front-of-room display dimensions**
:::image type="content" source="../media/front-of-room-single-dimensions.png" alt-text="Single front of room display with element dimensions" lightbox="../media/front-of-room-single-dimensions.png":::

**Dual room front-of-room display dimensions**
:::image type="content" source="../media/front-of-room-dual-dimensions.png" alt-text="Dual front of room display with element dimensions" lightbox="../media/front-of-room-dual-dimensions.png":::

When you create a custom wallpaper, use the following guidelines:

- Place text, logos, or icons, in the middle of the screen so it isn't obscured by home screen elements
- Avoid placing text, logos, or icons, near these locations:
  - **Upper left corner** - Time and room information.
    - **Size**: 280 x 130
    - **Upper-left corner coordinates**: 96, 96
  - **Bottom left corner** - Help information.
    - **Size**: 500 x 40
    - **Upper-left corner coordinates**: 96, 946
  - **Right side** - Room calendar.
    - **Size**: 512 x 585
    - **Upper-left corner (single display) coordinates**: 1312, 248
    - **Upper-left corner (dual display) coordinates**: 3232, 248

- Use a darker background in the top and bottom left corners to ensure users can read the white of the clock, room information, and help text in those locations
- For the best experience, use a contrast ratio of 4.5:1 for small text and 3:1 for large text. Use an accessibility contrast checker on the Internet to input color values to see if their contrast ratio is acceptable.

Save the custom wallpaper image file in one of the following format: `.jpg`, `jpeg`, `png`, `bmp`. After you've created the image file, [deploy it to your Teams Rooms devices](#deploy-an-updated-custom-wallpaper).

## Updating Teams Rooms device configuration

To apply the configuration changes included in this article to your Teams Rooms for Windows devices, you need to use the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

### Deploy an updated custom wallpaper

First, copy your custom wallpaper to the `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState` folder on your Teams Rooms device. You can use a USB drive or remotely connect to the network share of your device to copy the file.

After you've copied your custom wallpaper to the device, you need to tell Teams to use it. To use the custom wallpaper, add the following to your XML configuration file:

```xml
<CustomThemeImageUrl>ContosoWallpaper.png</CustomThemeImageUrl>
```

Change `ContosoWallpaper.png` to the file name of your custom wallpaper. 


### Enable refreshed home screen design

To enable the refreshed home screen design, add the following to your XML configuration file:

```xml
<TeamsRoomsNewExperience>true</TeamsRoomsNewExperience> 
```

### Hide front-of-room calendar display

To hide the calendar on your front-of-room display, add the following to your XML configuration file:

> [!IMPORTANT]
> The `<RemoveFoRCalendar>` setting is available only during the opt-in period for the refreshed home screen. When the refreshed home screen becomes the default experience, the `<RemoveFoRCalendar>` will be removed.

```xml
<RemoveFoRCalendar>true</RemoveFoRCalendar> 
```

### Roll back to legacy home screen design

To roll back to the legacy home screen design, add the following to your XML configuration file:

```xml
<TeamsRoomsNewExperience>false</TeamsRoomsNewExperience> 
```

