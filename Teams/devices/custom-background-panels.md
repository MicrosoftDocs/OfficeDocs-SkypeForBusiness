---
title: Set custom backgrounds on Teams Panels
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: eviegrimshaw
ms.date: 8/21/2024
ms.topic: article
audience: Admin
appliesto: 
  - Microsoft Teams
ms.service: msteams
ms.subservice: itpro-devices
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
search.appverid: MET150
ms.localizationpriority: medium
description: <Insert description>
---
# Set up and manage custom backgrounds on Teams panels

You can create custom background images for your Teams panel devices to showcase your brand or to provide instructions and support information to Teams panels users. For example, you can add your company logo, custom QR codes, a help URL link, or other organization information.

To use custom backgrounds, it depends on the version of Teams panels app installed and the license of the account that is signed in to that device:

- Verify the Teams panel is running on version 1449/1.0.96.2024081207 or later.

- Verify the account signed in on your Teams panel device is assigned a Teams Rooms Pro or Teams Shared Devices license.

To set up and manage custom backgrounds for your Teams panels:

1. Sign in to the **Teams admin center**.
2. Go to **Teams devices** > **Panels** > **Configuration profiles** and select **Add** or **Edit**.
3. Go to **Device settings** > **Background** > select **Use a custom background**. You can upload one image, which will be displayed on the panel home screen.
4. Select **Save**.

## Custom background requirements

There are a few requirements on the custom background you'll upload to the Teams panel. The minimum resolution supported is 1280 x 720. The custom background image file must be between 100 KB and 2 MB and a JPG, JPEG, and PNG file format.  

> [!NOTE]
> Custom backgrounds with resolutions or aspect ratios higher than the recommended resolution for a display may be center-cropped.

### Custom background content guidelines

Follow the best practices listed here to ensure that:

- Content doesn't collide with on-screen elements.
- Content remains legible when placed in front of visual elements in the custom background.
- Content remains visible if a custom background is cropped.

For Teams panels display, follow the following guidelines:

- Use a darker background in the top corner to ensure users can read the clock and room information that is in white text.

- For the best experience, use a contrast ratio of 4.5:1 for small text and 3:1 for large text. Use an accessibility contrast checker on the Internet to input color values to see if their contrast ratio is acceptable.

> [!TIP]
> Use the custom background template in designing your custom background image.

:::image type="content" source="./media/custom-background-panels/image.png" alt-text="Teams panel background screen layout." lightbox="./media/custom-background-panels/image.png":::

### Custom background template

To create custom backgrounds that meet the guidelines in the previous section, you can download the [Microsoft Teams panels Custom Background template](https://www.microsoft.com/en-us/download/details.aspx?id=106223). The template is a .PSD file. You can use apps such as Adobe Photoshop or Paint.NET (a plug-in may be required) to customize the PSD file. The template provides the guidelines to help you place text and graphics in your custom backgrounds so that on-screen elements won't be blocked or obscured.

## Deploy custom backgrounds

After you've created a background image, make sure you save it, and then you can deploy the background image.

1. Upload it to a Teams panel configuration profile in the Teams admin center.

2. Assign the Teams panel configuration profile to any Teams panel device with a Teams Rooms Pro or Teams Shared Devices license.

Once your custom image is saved and assigned to the configuration profile for your Teams panels, the custom image is applied as the screen background.

If you want to revert back to one of the Teams built-in images you can go to **Teams Admin Settings** > **Backgrounds** and then select another background. To change the custom image saved on the device, you need to make the update from the Teams admin center.
