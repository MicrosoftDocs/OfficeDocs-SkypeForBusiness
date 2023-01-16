---
title: Custom meeting backgrounds for Teams meetings
author: wlibebe
ms.author: wlibebe
manager: serdars
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
appliesto: 
  - Microsoft Teams
f1.keywords:
  - CSH
ms.localizationpriority: medium
search.appverid: MET150
description: Using approved corporate assets like backgrounds to create custom backgrounds for Teams meetings within your organization.
---

# Custom meeting backgrounds for Teams Meetings

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

## Overview

Customization in Teams meetings allows organizations to extend their visual identities across the meeting experience. Using custom meeting backgrounds helps foster internal corporate culture building and increase overall brand awareness with both internal and external meeting participants. With the help of an organization's brand management and corporate communications teams, admins can easily set up and create custom meeting backgrounds for various business units and departments within a single tenant.

By default, Teams premium licensed users who are either admins or have been assigned a meeting customization policy can create meetings that feature custom meeting  backgrounds. These custom backgrounds will only be available for end users within your organization who have a Teams Premium license to use.

## Prerequisites

Before setting up custom meeting backgrounds for your Teams Meetings, check to make sure you have the following items:

- Access to the Teams Premium SKU
- You’re an admin with access to the Teams admin center or you’ve been assigned a customization policy
- You’ve enabled the [custom background policy](#enabling-the-custom-background-policy)
- Your background images meet the [required specifications](#adding-custom-background-images)

## Setting up custom meeting backgrounds

Admins can upload and manage custom meeting backgrounds for Teams meetings in the Teams admin center.

### Enabling the custom background policy

As an admin, to create custom backgrounds, you'll need to create a new meeting customization policy or modify the organizational global default policy.
To enable the custom background policy, admins will perform the following steps:

1. Open the Teams admin center
2. Select **Meetings** from the navigation pane
3. Under Meetings, there are two ways to access the custom background policy. You could select **Customization Policies** to select an existing policy or create a new one. Alternatively, you could select **Meeting Policies** and then select the **Custom meeting images** button in the upper right hand corner.
4. Within your chosen policy, navigate to the **Custom Meeting Backgrounds** section
5. Toggle the **Custom backgrounds** setting from off to on to enable the setting
6. Select **Save**

### Adding custom background images

Now that you’ve enabled the custom background policy, you can upload your custom background images. These images will appear on the end users’ interfaces, ordered by the time of upload.

Uploads must adhere to the following parameters. Admins can upload:

- PNG and JPEG image formats for their images
- Images with minimum dimensions of 360 px X 360 px
- Images with minimum dimensions of 3840 px X 2160 px
- A maximum of 50 custom background images

To upload your images, navigate to **Meetings** > **Customization Policies** and select your policy from the previous step. Scroll down to the **Custom meeting backgrounds** section, and under the table with the custom background’s toggle, select **+Add**. Once you select +Add, a pane called **Managing Backgrounds** will open, allowing you to add your images.

> [!NOTE]
> Only end users with a Teams Premium license will see these images in their Background Settings panel.

### Saving custom background images

You'll find previews of your uploaded images in a new table under the **Custom meeting backgrounds** section. This table also displays the name and resolution of your images. Once you confirm your choice of uploaded images, select the **Save** button below the preview table. Now that you’ve selected save, your uploaded backgrounds are visible to your end users with a Teams Premium license.

## Where are custom backgrounds visible

The following list displays supported clients where custom backgrounds are visible:

- Web client
- Desktop client
- Android
- iOS

### Who can select and apply custom meeting backgrounds

Only Teams Premium licensed users can use the meeting backgrounds in their Background Settings panel.

> [!NOTE]
> External or anonymous users can't use custom meeting backgrounds.

### Who can view custom meeting backgrounds

While only licensed end users can select their choice of uploaded backgrounds, anyone can view the background that's applied to a meeting. These users include:

- In-tenant, Teams Premium licensed users
- In-tenant, non-licensed users
- External Users
- Anonymous users
