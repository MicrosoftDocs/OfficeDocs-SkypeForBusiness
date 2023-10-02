---
title: Custom meeting backgrounds for Teams meetings
author: wlibebe
ms.author: wlibebe
manager: serdars
ms.date: 09/15/2022
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

Custom meeting backgrounds are images that you, as an admin can upload for your users to display in the background of their video feed during meetings.

Customization in Teams meetings allows organizations to extend their visual identities across the meeting experience. Using custom meeting backgrounds helps foster internal corporate culture building and increase overall brand awareness with both internal and external meeting participants. With the help of an organization's brand management and corporate communications teams, admins can easily set up and create custom meeting backgrounds for various business units and departments within a single tenant.

By default, Teams premium licensed users who are either admins or have been assigned a meeting customization policy can create meetings that feature custom meeting  backgrounds. These custom backgrounds are only available for end users within your organization who have a Teams Premium license to use. These users can still upload their own custom backgrounds.

## Prerequisites

Before setting up custom meeting backgrounds for your Teams Meetings, check to make sure you have the following items:

- Access to the Teams Premium SKU
- You’re an admin with access to the Teams admin center or you’ve been assigned a customization policy
- You’ve enabled the [custom background policy](#enabling-the-custom-background-policy)
- Your background images meet the [required specifications](#adding-custom-background-images)

## Setting up custom meeting backgrounds

Admins can upload and manage custom meeting backgrounds for Teams meetings in the Teams admin center.

### Enabling the custom background policy

As an admin, to create custom backgrounds, you need to create a new meeting customization policy or modify the organizational global default policy.
To enable the custom background policy, follow these steps:

1. Open the Teams admin center
2. Select **Meetings** from the navigation pane
3. Under Meetings, there are two ways to access the custom background policy. You could select **Customization Policies** to select an existing policy or create a new one. Alternatively, you could select **Meeting Policies** and then select the **Custom meeting images** button in the upper right hand corner.
4. Within your chosen policy, navigate to the **Custom Meeting Backgrounds** section
5. Toggle the **Custom backgrounds** setting from off to on to enable the setting
6. Select **Save**

### Adding custom background images

Now that you’ve enabled the custom background policy, you can upload your custom background images. These images are displayed on the end users’ interfaces, ordered by the time of upload.

Uploads must adhere to the following parameters. Admins can upload:

- PNG and JPEG image formats for their images
- Images with minimum dimensions of 360 px X 360 px
- Images with maximum dimensions of 3840 px X 2160 px
- A maximum of 50 custom background images

To upload your images, navigate to **Meetings** > **Customization Policies** and select your policy from the previous step. Scroll down to the **Custom meeting backgrounds** section, and under the table with the custom background’s toggle, select **+Add**. Once you select +Add, a pane called **Managing Backgrounds** opens, allowing you to add your images.

> [!NOTE]
> Only end users with a Teams Premium license will see these images in their Background Settings panel.

### Saving custom background images

You'll find previews of your uploaded images in a new table under the **Custom meeting backgrounds** section. This table also displays the name and resolution of your images. Once you confirm your choice of uploaded images, select the **Save** button below the preview table. Now that you’ve selected save, your uploaded backgrounds are visible to your end users with a Teams Premium license.

## Show only custom backgrounds in your users' gallery

You can decide to only show custom backgrounds you've uploaded in your users' gallery.

To only show custom backgrounds you've uploaded, follow these steps:

1. Select **Meetings** from the navigation pane in the Teams Admin Center
2. Under Meetings, select **Meeting Policies** and select an existing policy, or create a new one.
3. Within your chosen policy, navigate to the **Audio and Video** section and set  **Participants can use video effects** to **Off** or **Only background blur**.
4. Select **Save**
5. Navigate to **Meetings** >  **Customization Policies** to select an existing policy or create a new one.
6. Within your chosen policy, scroll down to the **Custom Meeting backgrounds** section and set **Custom backgrounds** to **On**. If you haven't already, you can upload your custom backgrounds.
7. Select **Save**

> [!NOTE]
> You must set **Participants can use video effects** to **Off** or **Only background blur** to only show custom backgrounds in your users' gallery.

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
- In-tenant, nonlicensed users
- External Users
- Anonymous users
