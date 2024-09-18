---
title: Set up and manage Teams Rooms on Android custom backgrounds
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: henrikalim
ms.date: 07/10/2024
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
ms.assetid: f09f4c2a-2608-473a-9a27-f94017d6e9dd
description: Learn how to set up custom backgrounds on Teams Rooms on Android front-of-room and touch console displays.
---

# Set up and manage Teams Rooms on Android custom backgrounds

You can create custom background images for your Teams Rooms on Android devices to showcase your brand or to provide instructions and support information to Teams Rooms users. For example, you can add your company logo and include contact information for your organization's help desk to your custom background.

Your ability to deploy custom backgrounds depends on the version of Teams Rooms on Android app installed on your device and the license of the account logged in on the device:
- Your Teams Rooms on Android device must be running on version 1449/1.0.96.2024070201 or later.
- The account signed in on your Teams Rooms on Android device must be assigned with a Teams Rooms Pro license.

To set up and manage custom backgrounds for your Teams Rooms on Android devices, log into **Teams admin center** > go to **Teams devices** > **Teams Rooms on Android** > select **Configuration profiles** > **Add** or **Edit** > **Device settings** > **Background** > select the dropdown and choose **Use a custom background**. You can upload up to three images and specify which one goes to the main display, extended display, or touch console. You also have the option to reuse the main display image for the extended display.  

No matter how many screens your devices may have, the main display and extended display inputs are required, while the touch console input is optional:
- When you push the configuration profile to a single screen device, only the main display image will show up. 
- When you have two front-of-room displays or when you connect a second display later, the extended display image will be shown. 
- If no image is uploaded for the touch console, a purple gradient default image will be displayed. 

> [!NOTE]
> In a dual screen set up, the main display is where the room calendar is shown and is meant to be installed on the right side; the extended display is where the date/time and room information is shown and is meant to be placed on the left side.

### Supported resolutions

#### Minimum resolutions

Front-of-room displays and touch consoles have **minimum** supported custom background **resolutions**:
- For front-of-room displays, the minimum supported resolution is 1920 x 1080. 
- For touch consoles, the minimum supported resolution is 1280 x 720.

#### Recommended resolutions

The **recommended** custom background **resolution** for front-of-room displays and touch consoles depends on the aspect ratio and resolution of the display used. The following lists the recommended custom background resolution for each supported display aspect ratio:
- Single and dual front-of-room displays (per display)
  - 16:9 displays – 1920 x 1080 for 1080p displays, 3840 x 2160 for 4K displays. Up to two 16:9 displays are supported.
- Touch console displays
  - 16:9 displays – 1920 x 1080 
  - 16:10 displays – 1280 x 800
- Touch board displays (4K displays)
  - 16:9 – 3840 x 2160

If you're not sure what the aspect ratio of your display is, check your display's specifications.

> [!IMPORTANT]
> Custom backgrounds with resolutions or aspect ratios higher than the recommended resolution for a display may be center-cropped.
> 
> :::image type="content" source="../media/front-of-room-16-9-center-crop.png" alt-text="Screenshot that shows a custom background showing a center crop in a larger image." lightbox="../media/front-of-room-16-9-center-crop-large.png":::
>
> Custom backgrounds with resolutions or aspect ratios lower than the recommended resolution but higher than the minimum supported resolution are scaled to fill the frame of the display and are then center-cropped. The original aspect ratio of the custom background is maintained.

### Supported file size and formats 

The custom background image file must be under 20MB and saved in one of the following formats: `JPG`, `JPEG`, and `PNG`. 

### Custom background content guidelines

Follow the best practices listed in this section to ensure the following:
- Content doesn't collide with on-screen elements
- Content remains legible when placed in front of visual elements in the custom background
- Content remains visible if a custom background is cropped

The following guidelines apply for front-of-room, touch console, and touch board displays:
- Use a darker background on the top and bottom left corners to ensure users can read the clock, room information, and tips in those locations in white.
- For the best experience, use a contrast ratio of 4.5:1 for small text and 3:1 for large text. Use an accessibility contrast checker on the Internet to input color values to see if their contrast ratio is acceptable.
- Place text, logos, or icons, in the middle of the screen so it isn't blocked by home screen elements. 

> [!TIP]
> Use the [custom background template](#custom-background-template) in designing your custom background images. 

#### Front-of-room displays

When you create a custom background, avoid placing text, logos, or icons, near these locations:

- **Upper left corner** - Time and room information.
  - **Size**: up to 46% of the screen width, up to 42% of the screen height depending on the display settings
- **Bottom left corner** - Tips.
  - **Size**: up to 46% of the screen width, up to 16% of the screen height depending on the display settings
- **Right side** - Room calendar.
  - **Size**: up to 36% of the screen width, up to 72% of the screen height depending on the display settings
    
**16:9 - Single front-of-room display dimensions**

:::image type="content" source="../media/mtr-devices/mtra-for-qr-16x9.png" alt-text="Screenshot that shows a custom background showing a 16:9 front of room display with element dimensions and a QR code." lightbox="../media/mtr-devices/mtra-for-qr-16x9.png":::

**16:9 - Dual front-of-room display dimensions**

:::image type="content" source="../media/mtr-devices/mtra-dual-for-qr.png" alt-text="Screenshot that shows a custom background showing dual 16:9 front of room displays with element dimensions and a QR code." lightbox="../media/mtr-devices/mtra-dual-for-qr.png":::

#### Touch console displays

When you create a custom background, avoid placing text, logos, or icons, near these locations:

- **Upper left corner** - Time and room information.
  - **Size**: up to 42% of the screen width, up to 32% of the screen height depending on the display settings
- **Bottom left corner** - Tips.
  - **Size**: up to 42% of the screen width, up to 11% of the screen height depending on the display settings 
- **Middle** - User actions.
  - **Size**: vertically centered between the room information section and tips section, horizontally centered between the left edge and the room calendar 
- **Right side** - Room calendar.
  - **Size**: up to 44% of the screen width, up to 80% of the screen height depending on the display settings
- **Bottom right corner** - Help.
  - **Size**: up to 4% of the screen width, up to 7% of the screen height depending on the display settings 
    
**16:9 - Touch console dimensions**

:::image type="content" source="../media/mtr-devices/mtra-console-qr.png" alt-text="Screenshot that shows a custom background showing a 16:9 touch console display with element dimensions with QR code." lightbox="../media/mtr-devices/mtra-console-qr.png":::

#### Touch board displays

When you create a custom background, avoid placing text, logos, or icons, on these locations:

- **Upper left corner** - Time and room information.
  - **Size**: up to 46% of the screen width, up to 42% of the screen height depending on the display settings
- **Bottom left corner** - Tips.
  - **Size**: up to 46% of the screen width, up to 16% of the screen height depending on the display settings
- **Right side** - User actions and room calendar.
  - **Size**: up to 43% of the screen width, up to 72% of the screen height depending on display settings
- **Bottom right corner** - Help.
  - **Size**: up to 3% of the screen width, up to 5% of the screen height depending on display settings

**16:9 - Touch board display dimensions**

:::image type="content" source="../media/mtr-devices/mtra-touchboard-qr-16x9.png" alt-text="Screenshot that shows a custom background showing a 16:9 touch board display with element dimensions with QR code." lightbox="../media/mtr-devices/mtra-touchboard-qr-16x9.png":::

### Custom background template

To create custom backgrounds that meet the guidelines in the previous section, you can download the [Microsoft Teams Rooms on Android Custom Background Template](https://www.microsoft.com/download/details.aspx?id=106161).

The template is a .PSD file that can be opened by apps such as Adobe Photoshop or Paint.NET (a plug-in may be required). The template provides assets and guidelines to help you place text and graphics in your custom backgrounds that won't be obscured by on-screen elements.

### Deploy custom backgrounds

After you've created background images:
1. Save them with unique and descriptive filenames. For example, `ContosoBackground-Right-FoR.jpg` (main/right display), `ContosoBackground-Left-FoR.jpg` (extended/left display), and `ContosoBackground-Console.jpg` (touch console display). 
2. Upload them to a Teams Rooms on Android configuration profile in the Teams admin center. 
3. Assign the Teams Rooms on Android configuration profile to any Teams Rooms on Android device with a Teams Rooms Pro license.

Once the custom images are saved in the configuration profile, and the configuration profile has been assigned to Teams Rooms on Android devices with a Teams Rooms Pro license, the custom images will be applied as the background of the Teams Rooms on Android devices accordingly.

On your Teams Rooms on Android device settings, you can switch the background of your device from the custom image to one of the Teams built-in images, or vice versa: go to **Teams Admin Settings** > **General** > **Background** > select another background thumbnail as desired. To change the custom image saved on the device, you'll need to make the update from the Teams admin center.   
