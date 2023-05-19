---
title: Manage Teams Rooms on Windows custom backgrounds
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.date: 02/23/2018
ms.topic: quickstart
ms.service: msteams
ms.subservice: itpro-rooms
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
  - Tier1
ms.custom: seo-marvel-apr2020
ms.assetid: f09f4c2a-2608-473a-9a27-f94017d6e9dd
description: Read this article for information on how to create resource accounts for rooms and shared devices, including Microsoft Teams Rooms, Teams Rooms on Surface Hub, and hot-desking on Teams displays.
---

## Set up and manage Teams Rooms on Windows custom backgrounds

You can create custom background images for your Microsoft Teams Rooms on Windows devices to represent your brand or to provide instructions to Teams Rooms users. For example, you can add a copy logo to your background images and include contact information for your organization's help desk if meeting attendees need help.

The custom background options you have available to you, and how you set them up, depend on the version of Teams Rooms installed on your devices. Select the tab below that corresponds to the version of Teams installed on your Teams Rooms device. To check which version of Teams is installed on your device, do the following:

- On your Teams Rooms device:
  1. Select **More** and then **Settings**
  1. Enter your admin password and select **Yes**
  1. On the **Settings** screen, find the version under **App version**
- In Teams admin center:
  1. Go to <https://admin.teams.microsoft.com> and sign in with your admin account
  1. Select **Teams Rooms on Windows** and then select the device you want to see the app version for
  1. Select the **Health** tab
  1. On the **Health** tab, go to the **Software health** section and find the version under **Teams App**

## [Teams Rooms 4.16 and earlier](#tab/Teams416)

The guidelines in this section apply to Teams Rooms on Windows version 4.16 devices that have the refreshed home screen enabled. If your device is running 4.15 and earlier, or if you haven't enabled the refreshed home screen, use the guidelines provided in [Custom theme images](xml-config-file.md#custom-theme-images).

Custom backgrounds are supported on 16:9 and 21:9 displays. The guidelines differ slightly depending on the size of your display:

- **16:9 displays** Custom backgrounds need to be exactly 3840 x 1080 pixels in size, regardless of whether the background is used with a single front-of-room display or dual front-of-room displays. If used with a single front-of-room display, the right half of the image is used and the left half is cropped out. If used with a dual front-of-room display, the image is divided between the left and right front-of-room displays.
- **21:9 displays** Custom backgrounds need to be exactly 2560 x 1080 pixels in size. Only one 21:9 front-of-room display is supported.

If you want to have dual front-of-room displays, they both need to be 16:9 displays. Two 21:9 displays or mixing 16:9 and 21:9 displays isn't supported. If you're not sure if your display is 16:9 or 21:9, check your display's specifications.

**16:9 - Single front-of-room display dimensions**
:::image type="content" source="../media/front-of-room-16-9-single-dimensions.png" alt-text="Single 16:9 front of room display with element dimensions." lightbox="../media/front-of-room-16-9-single-dimensions-large.png":::

**16:9 - Dual front-of-room display dimensions**
:::image type="content" source="../media/front-of-room-16-9-dual-dimensions.png" alt-text="Dual 16:9 front of room displays with element dimensions." lightbox="../media/front-of-room-16-9-dual-dimensions-large.png":::

**21:9 - Single front-of-room display dimensions**
:::image type="content" source="../media/front-of-room-21-9-dimensions.png" alt-text="Single 21:9 front of room display with element dimensions." lightbox="../media/front-of-room-21-9-dimensions-large.png":::

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

Save the custom background image file in one of the following formats: `.jpg`, `jpeg`, `png`, `bmp`. After you've created the image file, [deploy it to your Teams Rooms devices](#deploy-an-updated-custom-background).

## [Teams Rooms 4.17 and earlier](#tab/Teams417)

Teams Rooms version 4.17 and later gives you more options for how to set up custom backgrounds on your front-of-room displays. If you have dual front-of-room displays, you can configure different images for each display. It also lets you set up a custom background for your system's touch console.

### Minimum resolutions

Front-of-room displays and touch consoles have minimum supported custom background resolutions. For front-of-room displays, the minimum supported resolution is 1920 x 1080. For touch consoles, the minimum supported resolution is 1280 x 800. If the resolution of any custom background is below the minimum supported resolution for the display or console it's added to, no custom background is shown on any display or console.

### Recommended resolutions

The recommended custom background resolution for front-of-room displays and touch consoles depends on their aspect ratios. The following lists the aspect ratios supported by each display and the recommended resolution for each.

- Single and dual front-of-room displays
  - 16:9 displays - 1920 x 1080
  - 21:9 displays - 2560 x 1080
  - 3:2 displays - 1920 x 1280
- Touch consoles
  - 16:9 display - 1920 x 1080
  - 16:10 display - 1280 x 800
  - 3:2 display - 1920 x 800

If you're not sure what the aspect ratio of your display is, check your display's specifications.

> [!IMPORTANT]
> Custom backgrounds with resolutions higher than the recommended resolution for a display may be center-cropped.
>
> Custom backgrounds with resolutions lower than the recommended resolution but higher than the minimum supported resolution are scaled to fill the frame of the display and are then center-cropped. The original aspect ratio of the custom background is maintained.

### Custom wallpaper content guidelines

The graphics and text you place on your custom backgrounds needs to follow content guidelines to ensure the following:

- Content doesn't collide with on-screen elements
- Content is visible to meeting attendees further away from the displays
- Content remains legible when placed in front of visual elements in the custom background
- Content remains visible if a custom background is cropped

The following guidelines apply for both front-of-room and touch console displays:

- Use a darker background in the top and bottom left corners to ensure users can read the white of the clock, room information, and help text in those locations.
- For the best experience, use a contrast ratio of 4.5:1 for small text and 3:1 for large text. Use an accessibility contrast checker on the Internet to input color values to see if their contrast ratio is acceptable.

Save the custom background image file in one of the following formats: `.jpg`, `jpeg`, `png`, `bmp`. After you've created the image file, [deploy it to your Teams Rooms devices](#deploy-an-updated-custom-background).

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
  
#### Touch console display

When you create a custom background:

- Place text, logos, or icons, in the middle of the screen so it isn't obscured by home screen elements.
- Avoid placing text, logos, or icons, near these locations:
  - **Upper left corner** - Time and room information.
    - **Size**: 260 x 104
    - **Upper-left corner coordinates**: 48, 48
  - **Middle** - Action buttons.
    - **Size**: 408 x 336
    - **Upper-left corner coordinates**: 156, 221
  - **Bottom left corner** - Cortana.
    - **Size**: 400 x 48
    - **Upper-left corner coordinates**: 56, 616
  - **Right side** - Room calendar.
    - **Size**: 512 x 631
    - **Upper-left corner coordinates**: 720, 48
