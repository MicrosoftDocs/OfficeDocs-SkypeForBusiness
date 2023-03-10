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

The refreshed home screen design is available to anyone who has Teams Rooms on Windows version 4.16 or later. However, because the refreshed design makes changes to Exchange calendar integration and the layout of the Teams Rooms home screen, we haven't made it the default experience yet. To see the refreshed home screen in Teams Rooms version 4.16, you need to [manually enable it](#enable-refreshed-ui-design).

> [!IMPORTANT]
> The refreshed home screen is opt-in for Teams Rooms version 4.16. The refreshed home screen will become the default experience in a future release. Be sure to review the guidelines in this article, and update custom themes, before the refreshed home screen becomes the default experience.

Before you enable the refreshed home screen design in Teams Rooms version 4.16, and before it becomes the default experience in a future release, check the following:

- **Integrated Exchange calendar** - The refreshed home screen changes how the calendar on Teams Rooms devices communicates with Exchange. Make sure meetings that appear in Outlook or Outlook on the web are correctly reflected in your Teams clients. [How Exchange and Microsoft Teams interact](../Exchange-Teams-interact.md)
  > [!IMPORTANT]
  > If you're using Teams Rooms with an on-premises Exchange server, some calendar functionality is unavailable in Teams Rooms version 4.16. If you use your Teams Rooms devices to join forwarded meetings, third-party meetings, cross-tenant meetings, or Teams Live Events, we recommend that you don't enable the refreshed home screen design yet. These meetings scenarios will be supported when the refreshed home screen becomes the default experience in an upcoming release.
- **Custom themes** - A calendar has been added to front-of-room display with the refreshed home screen. If you have a custom theme that has logos or information that users need to see, we recommend that you don't enable the refreshed home screen design until you've [updated your theme](#custom-wallpaper-guidelines) or that you temporarily [remove the calendar from the front-of-room display](#hide-front-of-room-calendar-display).

If you want roll back to the previous Teams Rooms home screen design, see [Roll back to legacy home screen design](#roll-back-to-legacy-ui-design).

## Custom wallpaper guidelines

You can create a custom wallpaper for your Teams Rooms theme to represent your brand or to provide instructions to Teams Rooms users. The guidelines in this section apply to Teams Rooms on Windows version 4.16 and later devices that have the refreshed home screen enabled. If your device is running 4.15 and earlier, or if you haven't enabled the refreshed home screen, use the guidelines provided in [Custom theme images](xml-config-file.md#custom-theme-images).

The custom theme image file needs to be placed in the `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState` folder on the Teams Rooms device. After the image file is copied to the device, use the [Teams XML configuration file](xml-config-file.md) to add the `<CustomThemeImageUrl>` variable to it. The `<CustomThemeImageUrl>` variable contains the filename of the image you copied to the device, for example `ContosoWallpaper.png`.

Custom wallpapers need to be exactly 3840 x 1080 pixels in size, regardless of whether the wallpaper is used with a single front-of-room display or dual front-of-room displays. If used with a single front-of-room display, the left half of the image is used and the right half is cropped out. If used with a dual front-of-room display, the image is divided between the left and right front-of-room displays. Supported image file formats include `.jpg`, `jpeg`, `png`, and `bmp`.

**Single room front-of-room display dimensions**
:::image type="content" source="../media/front-of-room-single-dimensions.png" alt-text="Single front of room display with element dimensions" lightbox="../media/front-of-room-single-dimensions.png":::

**Dual room front-of-room display dimensions**
:::image type="content" source="../media/front-of-room-dual-dimensions.png" alt-text="Dual front of room display with element dimensions" lightbox="../media/front-of-room-dual-dimensions.png":::

When you create a custom wallpaper, keep the following guidelines in mind:

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

## Updating Teams Rooms device configuration

To apply the configuration changes included in this article to your Teams Rooms for Windows devices, you need to use the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md). 

### Enable refreshed home screen design

To enable the refreshed home screen design, add the following to your XML configuration file:

```xml
<TeamsRoomsNewExperience>true</TeamsRoomsNewExperience> 
```

### Hide front-of-room calendar display

temporary

To hide the calendar on your front-of-room display, add the following to your XML configuration file:

```xml
<RemoveFoRCalendar>true</RemoveFoRCalendar> 
```

### Roll back to legacy home screen design

To roll back to the legacy home screen design, add the following to your XML configuration file:

```xml
<TeamsRoomsNewExperience>false</TeamsRoomsNewExperience> 
```

