---
title: Set up and manage Teams Rooms on Windows custom backgrounds
ms.author: tonysmit
author: tonysmit
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.date: 05/30/2023
ms.topic: quickstart
ms.service: msteams
ms.subservice: itpro-rooms
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
ms.custom: seo-marvel-apr2020
ms.assetid: f09f4c2a-2608-473a-9a27-f94017d6e9dd
description: Learn how to set up custom backgrounds on Teams Rooms front-of-room and touch console displays.
---

# Set up and manage Teams Rooms on Windows custom backgrounds

You can create custom background images for your Microsoft Teams Rooms on Windows devices to represent your brand or to provide instructions to Teams Rooms users. For example, you can add a copy logo to your background images and include contact information for your organization's help desk if meeting attendees need help.

The custom background options available to you, and how you set them up, depend on the version of Teams Rooms installed on your device and whether the device has a Microsoft Teams Rooms Pro or Microsoft Teams Rooms Basic license. 

To check which version of Teams is installed and which Teams Rooms license is applied to your device:

- On your Teams Rooms device:
  1. Select **More** and then **Settings**
  1. Enter your admin password and select **Yes**
  1. On the **Settings** screen
      - Find the version under **App version**
      - Find the Teams Rooms license under **Room License**
- In Teams admin center:
  1. Go to <https://admin.teams.microsoft.com> and sign in with your admin account
  1. Select **Teams Rooms on Windows** and then find the device you want to see the app version and Teams Rooms license for
  1. On the details page, look next to the device name to find the license type
      - **Pro** - Teams Rooms Pro license
      - **Basic** - Teams Rooms Basic license
      - Any other license type - equivalent to Teams Rooms Basic license
  1. Select the **Health** tab
  1. On the **Health** tab, go to the **Software health** section and find the version under **Teams App**

Select the tab that corresponds to the version of Teams Rooms and the Teams Rooms license that applies to your device.

| Teams Rooms version                                  | Teams Rooms Pro       | Teams Rooms Basic |
|------------------------------------------------------|-----------------------|-------------------|
| Teams Rooms 4.17 and later                           | Enhanced and Standard | N/A          |
| Teams Rooms 4.16 and earlier                         | Standard              | N/A          |

## [Enhanced backgrounds](#tab/Enhanced)

### Teams Rooms 4.17 and later with Teams Rooms Pro license

Enhanced backgrounds give you more options for how to set up custom backgrounds on your front-of-room displays. If you have dual front-of-room displays, you can configure different images for each display. They also let you set up a custom background for your system's touch console.

When you enable custom backgrounds, you need to provide custom backgrounds for your front-of-room displays. If you have two front-of-room displays, you need to provide a custom background for each display. Providing a custom background for your touch console is optional.

If you enable custom backgrounds and don't provide custom backgrounds for all of your front-of-room displays, all displays, including the touch console, default to `No Theme`.

> [!NOTE]
> If you've been using the `<CustomThemeImageUrl>` element to provide a single custom background image for your front-of-room displays, you can continue using it if it suits your needs. However, if you want to provide separate custom backgrounds for each front-of-room display, or if you want to configure a custom background on your touch console, you need to use the elements provided in this section.
>
> For more information about using `<CustomThemeImageUrl>`, see [Standard backgrounds](/microsoftteams/rooms/custom-backgrounds?tabs=Standard).

### Minimum resolutions

Front-of-room displays and touch consoles have minimum supported custom background resolutions. For front-of-room displays, the minimum supported resolution is 1920 x 1080. For touch consoles, the minimum supported resolution is 1280 x 800. If the resolution of any custom background is below the minimum supported resolution for the display or console it's added to, all displays default to `No Theme`.

### Recommended resolutions

The recommended custom background resolution for front-of-room displays and touch consoles depends on their aspect ratios. The following lists the aspect ratios supported by each display and the recommended resolution for each.

- Single and dual front-of-room displays (per display)
  - 16:9 displays - 1920 x 1080 (up to two 16:9 displays are supported)
  - 21:9 displays - 2560 x 1080 (only one 21:9 display is supported)
- Touch consoles
  - 16:9 display - 1920 x 1080
  - 16:10 display - 1280 x 800
  - 3:2 display - 1920 x 800

If you're not sure what the aspect ratio of your display is, check your display's specifications.

> [!IMPORTANT]
> Custom backgrounds with resolutions higher than the recommended resolution for a display may be center-cropped.
>
> :::image type="content" source="../media/front-of-room-16-9-center-crop.png" alt-text="A custom background showing a center crop in a larger image." lightbox="../media/front-of-room-16-9-center-crop-large.png":::
>
> Custom backgrounds with resolutions lower than the recommended resolution but higher than the minimum supported resolution are scaled to fill the frame of the display and are then center-cropped. The original aspect ratio of the custom background is maintained.

### Custom background content guidelines

The graphics and text you place on your custom backgrounds needs to follow content guidelines to ensure the following:

- Content doesn't collide with on-screen elements
- Content is visible to meeting attendees further away from the displays
- Content remains legible when placed in front of visual elements in the custom background
- Content remains visible if a custom background is cropped

The following guidelines apply for both front-of-room and touch console displays:

- Use a darker background in the top and bottom left corners to ensure users can read the white of the clock, room information, and help text in those locations.
- For the best experience, use a contrast ratio of 4.5:1 for small text and 3:1 for large text. Use an accessibility contrast checker on the Internet to input color values to see if their contrast ratio is acceptable.

If you want to set up two front-of-room displays, both displays need to have an aspect ratio of 16:9. When you have two front-of-room displays, the right one is the "main" display while the left one is the "extended" display.

Save the custom background image file in one of the following formats: `jpg`, `jpeg`, `png`, `bmp`. After you've created the image file, [deploy it to your Teams Rooms devices](#deploy-an-updated-custom-background).

These guidelines are also available in a [custom theme template](#custom-background-template) that you can download.

#### Front-of-room displays

When you create a custom background:

- Place text, logos, or icons, in the middle of the screen so it isn't obscured by home screen elements.
- Avoid placing text, logos, or icons, near these locations:
  - **Upper left corner** - Time and room information.
    - **Size**: 280 x 130
    - **Upper-left corner coordinates**: 96, 96
  - **Bottom left corner** - Help information.
    - **Size**: 500 x 40
    - **Upper-left corner coordinates**: 96, 946
  - **Right side** - Room calendar.
    - **Size**: 512 x 585
    - 16:9 displays
      - **Upper-left corner (single display) coordinates**: 1312, 248
      - **Upper-left corner (dual display) coordinates**: 3232, 248
    - 21:9 displays
      - **Upper-left corner coordinates**: 1912, 248
  
**16:9 - Single front-of-room display dimensions**

:::image type="content" source="../media/front-of-room-16-9-single-dimensions.png" alt-text="A custom background showing a 16:9 front of room display with element dimensions." lightbox="../media/front-of-room-16-9-single-dimensions-large.png":::

**16:9 - Dual front-of-room display dimensions**

:::image type="content" source="../media/front-of-room-16-9-dual-display-dimensions.png" alt-text="A custom background showing dual 16:9 front of room displays with element dimensions." lightbox="../media/front-of-room-16-9-dual-display-dimensions-large.png":::

**21:9 - Single front-of-room display dimensions**

:::image type="content" source="../media/front-of-room-21-9-dimensions.png" alt-text="Custom background showing a 21:9 front of room display with element dimensions." lightbox="../media/front-of-room-21-9-dimensions-large.png":::

These guidelines are also available in a [custom theme template](#custom-background-template) that you can download.

#### Touch console display

When you create a custom background, avoid placing text, logos, or icons, near these locations:

- **Upper left corner** - Time and room information.
  - **Size**: 260 x 104
  - **Upper-left corner coordinates**: 48, 48
- **Middle** - Action buttons.
  - **Size**: 408 x 336
  - **Upper-left corner coordinates**: 156, 221
- **Right side** - Room calendar.
  - **Size**: 512 x 631
  - **Upper-left corner coordinates**: 720, 48

**16:9 - Touch console dimensions**

:::image type="content" source="../media/console-16-9-dimensions.png" alt-text="A custom background showing a 16:9 touch console display with element dimensions." lightbox="../media/console-16-9-dimensions-large.png":::

### Custom background template

To create custom backgrounds that meet the guidelines in the previous sections, you can download the [Microsoft Teams Rooms Theme Template](https://www.microsoft.com/download/details.aspx?id=105251). 

The template is a .PSD file that can be opened by apps such as Adobe Photoshop or Paint.NET (a plug-in may be required). The template provides assets and guidelines to help you place text and graphics in your custom backgrounds that won't be obscured by on-screen elements.

### Deploy updated custom backgrounds

After you've created backgrounds for each of your displays, save them with unique and descriptive filenames. For example, `ContosoBackground-Right-FoR.jpg` (main/right display), `ContosoBackground-Left-FoR.jpg` (extended/left display), and `ContosoBackground-Console.jpg` (touch console display).

When your custom background image files are ready, copy them to the `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState` folder on your Teams Rooms device. You can use a USB drive or remotely connect to the network share of your device to copy the file.

To tell Teams to use custom backgrounds and which files to use, you need to add the `<Theming>` element to your XML configuration file. Within the `<Theming>` element, you need to provide the elements in the following table.

> [!NOTE]
> If the `<CustomThemeImageUrl>` element is also included in the XML configuration file, the following elements override the value provided in that element.

| Element | Description | Required? |
|---------|-------------|-----------|
| `<ThemeName>`                          | Set to `Custom` to use custom backgrounds.                                            | **Yes**, if `<Theming>` element is provided.                                                                                                                    |
| `<CustomBackgroundMainFoRDisplay>`     | Filename of main/right custom background. <br>e.g., `ContosoBackground-Right-FoR.jpg`   | If `<ThemeName>` is set to:<br><ul><li> `Custom` - **Yes**</li><li>Other value - **No**</li></ul>                                                                 |
| `<CustomBackgroundExtendedFoRDisplay>` | Filename of extended/left custom background. <br>e.g., `ContosoBackground-Left-FoR.jpg` | **Yes**, if both of the following are true:<br><ul><li>`<ThemeName>` is set to `Custom`.</li><li>`<DualScreenMode>` is set to `true`.</li></ul> |
| `<CustomBackgroundConsole>`            | Filename of touch console background. <br>e.g., `ContosoBackground-Console.jpg`         | **No**                                                                                                                                                          |

Here's an example XML snippet showing background images being provided for both right and left front-of-room displays and the touch console display:

```xml
<Theming> 
    <ThemeName>Custom</ThemeName> 
    <CustomBackgroundMainFoRDisplay>ContosoBackground-Right-FoR.jpg</CustomBackgroundMainFoRDisplay> 
    <CustomBackgroundExtendedFoRDisplay>ContosoBackground-Left-FoR.jpg</CustomBackgroundExtendedFoRDisplay> 
    <CustomBackgroundConsole>ContosoBackground-Console.jpg</CustomBackgroundConsole> 
</Theming> 
```

To apply the configuration changes included in this article to your Teams Rooms for Windows devices, you need to use the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

## [Standard backgrounds](#tab/Standard)

### Teams Rooms 4.16 with refreshed home screen enabled

The guidelines in this section apply to Teams Rooms on Windows version 4.16 devices that have the refreshed home screen enabled.

Custom backgrounds are supported on 16:9 and 21:9 displays. The guidelines differ slightly depending on the size of your display:

- **16:9 displays** Custom backgrounds need to be exactly 3840 x 1080 pixels in size, regardless of whether the background is used with a single front-of-room display or dual front-of-room displays. If used with a single front-of-room display, the right half of the image is used and the left half is cropped out. If used with a dual front-of-room display, the image is divided between the left and right front-of-room displays.
- **21:9 displays** Custom backgrounds need to be exactly 2560 x 1080 pixels in size. Only one 21:9 front-of-room display is supported.

If you want to have dual front-of-room displays, they both need to be 16:9 displays. Two 21:9 displays or mixing 16:9 and 21:9 displays isn't supported. If you're not sure if your display is 16:9 or 21:9, check your display's specifications.

**16:9 - Single front-of-room display dimensions**

:::image type="content" source="../media/front-of-room-16-9-single-dimensions.png" alt-text="Custom background showing a single 16:9 front of room display with element dimensions." lightbox="../media/front-of-room-16-9-single-dimensions-large.png":::

**16:9 - Dual front-of-room display dimensions**

:::image type="content" source="../media/front-of-room-16-9-spanned-dimensions.png" alt-text="Custom background showing dual 16:9 front of room displays with element dimensions." lightbox="../media/front-of-room-16-9-spanned-dimensions-large.png":::

**21:9 - Single front-of-room display dimensions**

:::image type="content" source="../media/front-of-room-21-9-dimensions.png" alt-text="Custom background showing a single 21:9 front of room display with element dimensions." lightbox="../media/front-of-room-21-9-dimensions-large.png":::

When you create a custom background, use the following guidelines:

- Place text, logos, or icons, in the middle of the screen so it isn't obscured by home screen elements.
- Avoid placing text, logos, or icons, near these locations:
  - **Upper left corner** - Time and room information.
    - **Size**: 280 x 130
    - **Upper-left corner coordinates**: 96, 96
  - **Bottom left corner** - Help information.
    - **Size**: 500 x 40
    - **Upper-left corner coordinates**: 96, 946
  - **Right side** - Room calendar.
    - **Size**: 512 x 585
    - 16:9 displays
      - **Upper-left corner (single display) coordinates**: 1312, 248
      - **Upper-left corner (dual display) coordinates**: 3232, 248
    - 21:9 displays
      - **Upper-left corner coordinates**: 1912, 248
  
- Use a darker background in the top and bottom left corners to ensure users can read the white of the clock, room information, and help text in those locations.
- For the best experience, use a contrast ratio of 4.5:1 for small text and 3:1 for large text. Use an accessibility contrast checker on the Internet to input color values to see if their contrast ratio is acceptable.

Save the custom background image file in one of the following formats: `jpg`, `jpeg`, `png`, `bmp`.

### Teams Rooms 4.16 without refreshed home screen and earlier versions of Teams Rooms

The custom theme image file must be placed in the `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState` folder. Enter the file name and extension in the `<CustomThemeImageUrl>` variable.

The image file should be exactly 3840 x 1080 pixels and must be one of the following file formats: `jpg`, `jpeg`, `png`, and `bmp`. If your organization wants a custom image, a graphic designer can use the Custom Theme Photoshop Template. It contains further detail on where various user interface elements are relative to the rest of a theme image and what areas appear on consoles and displays.

The XML configuration file must be updated at device startup to recognize the theme image. Once the new XML file is processed and deleted, the theme graphic file is deleted from the directory.

### Updating Teams Rooms device configuration

To apply the configuration changes included in this article to your Teams Rooms for Windows devices, you need to use the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

### Deploy an updated custom background

First, copy your custom background to the `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState` folder on your Teams Rooms device. You can use a USB drive or remotely connect to the network share of your device to copy the file.

After you've copied your custom background to the device, you need to tell Teams to use it. To use the custom background, add the following to your XML configuration file:

```xml
<CustomThemeImageUrl>ContosoBackground.png</CustomThemeImageUrl>
```

Change `ContosoBackground.png` to the file name of your custom background.
