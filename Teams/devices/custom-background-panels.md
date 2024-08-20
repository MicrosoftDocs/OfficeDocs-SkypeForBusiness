---
title: Set custom backgrounds on Teams Panels
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: eviegrimshaw
ms.date: 8/20/2024
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
# Set up and manage Teams panels custom backgrounds

You can create custom background images for your Teams panel devices to showcase your brand or to provide instructions and support information to Teams panels users. For example, you can add your company logo.

Your ability to deploy custom backgrounds depends on the version of Teams panels app installed on your Teams panel and the license of the account that is signed in to the device:

- Verify the Teams panels is running on version 1449/1.0.96.2024XXXX or later.
- Verify the account signed in on your Teams panel device is assigned a Teams Rooms Pro or Teams Shared Devices license.

To set up and manage custom backgrounds for your Teams panels:
1. Sign in to the **Teams admin center**.
2. Go to **Teams devices** > **Panels** > **Configuration profiles** and click **Add** or **Edit**.
3. Go to **Device settings** > **Background** > select **Use a custom background**. You can upload up to one image, which will display on the panel home screen.
4. Click **Save**.

### Custom background requirements

There are a few requirements on the custom background you will upload to the Teams panel. The minimum resolution supported is 1280 x 720. The custom background image file must be between 100KB and 2MB and is a JPG, JPEG, and PNG file format.  

> [!NOTE]
> Custom backgrounds with resolutions or aspect ratios higher than the recommended resolution for a display may be center-cropped.

### Custom background content guidelines

Follow the best practices listed here to ensure that:
- Content doesn't collide with on-screen elements.
- Content remains legible when placed in front of visual elements in the custom background.
- Content remains visible if a custom background is cropped.

For Teams panels display, follow the following guidelines:

- Use a darker background on the top corner to ensure users can read the clock and room information in white.
- For the best experience, use a contrast ratio of (@Evie to provide here). Use an accessibility contrast checker on the Internet to input color values to see if their contrast ratio is acceptable.

> [!TIP]
> Use the custom background template in designing your custom background image.   

:::image type="content" source="../media/byod/inventory-rooms-tab.png" alt-text="Screenshot of Inventory rooms tab." lightbox="../media/byod/inventory-rooms-tab.png"::: ![image](https://github.com/user-attachments/assets/2f4c6b95-a72f-490b-82ad-359ed9956e7e)

![User's image](media/custom-background-panels/image.png)

![User's image](media/custom-background-panels/image1.png)

### Custom background template

To create custom backgrounds that meet the guidelines in the previous section, you can download the (@Evie to provide here). The template is a .PSD file that can be opened by apps such as Adobe Photoshop or Paint.NET (a plug-in may be required). The template provides assets and guidelines to help you place text and graphics in your custom backgrounds that won't be obscured by on-screen elements.

### Deploy custom backgrounds

After you've created a background image:1. Save it with unique and descriptive file. 

1. Upload them to a Teams panel configuration profile in the Teams admin center.

1. Assign the Teams panel configuration profile to any Teams panel device with a Teams Rooms Pro or Teams Shared Devices license.

Once the custom images are saved in the configuration profile, and the configuration profile has been subsequently assigned to Teams panel devices with a Teams Rooms Pro or Teams Shared Devices license, the custom images will be applied as the background of the Teams panels devices accordingly.

On your Teams panel device settings, you can switch the background of your device from the custom image to one of the Teams built-in images, or vice versa: go to **Teams Admin Settings** > **Backgrounds** > select another background thumbnail as desired. To change the custom image saved on the device, you'll need to make the update from the Teams admin center.   

