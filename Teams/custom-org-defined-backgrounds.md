---
title: Custom org defined backgrounds for Teams meetings
author: wlibebe
ms.author: wlibebe
manager: serdars
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
  - CSH
ms.localizationpriority: medium
search.appverid: MET150
description: Using approved corporate assets like backgrounds to create custom backgrounds for Teams meetings within your organization.
---

# Custom organization branding for Teams meetings

> [!NOTE]
> Custom Org Defined Backgrounds is part of the Teams Premium Offering. To allow users to apply org wide backgrounds during a meeting, users must be assigned a Teams Premium license.  

## Overview

Branding in Teams meetings allows organizations to extend their visual identities across the meeting experience. Brand images and colors help foster internal corporate culture building and increase overall brand awareness with external meeting participants. With the help of an organization's brand management and corporate communications teams, admins can easily set up and create branded meeting themes for various business units and departments within a single tenant.


By default, Teams premium licensed users who are either admins or have been assigned a meeting customization policy can create meetings that feature custom organizational defined backgrounds. These custom backgrounds can be selected by your end users with a premium license within your organization.

## Prerequisites

Before setting up Org Defined Backgrounds for your Teams Meetings, check to make sure you have the following items:

- Access to the Teams Premium SKU
- You’re an admin with access to the Teams admin center or you’ve been assigned a customization policy
- You’ve enabled the [custom background policy](#enabling-the-custom-background-policy)
- Your background images meet the [required specifications](#adding-org-wide-background-images)

## Setting up org defined backgrounds

Admins can upload and manage customized org defined backgrounds for Teams meetings in the Teams admin center.

### Enabling the custom background policy

Meeting Branding lives on the Customization Policies page in the Teams admin center. To create custom backgrounds, admins will first need to create a new meeting customization policy or modify the organizational global default policy.
To enable the custom background policy, admins will perform the following:

1. Open the Teams admin center
2. Select **Meetings** from the navigation pane
3. Under Meetings, select **Customization Policies**
4. Either select an existing policy or create a new one
5. Within your chosen policy, navigate to the **Custom Meeting Backgrounds** section
6. Toggle the setting **Custom backgrounds** from off to on to enable the setting
7. Select **Save**

### Adding org wide background images

Now that you’ve enabled the custom background policy, you can upload your custom background images. These images will appear on the end users’ interfaces, ordered by the time of upload.

Uploads must adhere to the following parameters. Admins can upload:

- PNG and JPEG image formats for their images
- Images with minimum dimensions of 360 px X 360 px
- Images with minimum dimensions of 3840 px X 2160 px
- A maximum of 50 custom background images

To upload your images, navigate to **Meetings** > **Customization Policies** and select your policy from the previous step. Scroll down to the **Custom meeting backgrounds** section, and under the table with the custom background’s toggle, select +Add. Once you select +Add, a pane called **Managing Backgrounds** will open, allowing you to add your images.

The previews of your uploaded images can be found in a new table under the **Custom meeting backgrounds** section.

> [!NOTE]
> Only users with a Teams Premium license will see these images in their Background Settings panel.

### Saving org wide background images

The previews of your uploaded images are in a new table under the **Custom meeting backgrounds** section that displays the name and resolution of your images. Once you confirm your choice of uploaded images, select the **Save** button, below the preview table. Now that you’ve selected save, your uploaded backgrounds are visible to your end users with a Teams Premium license.

## Where are Meeting Themes visible

The following list displays supported clients where meeting themes are visible:

- Web client
- Desktop client
- Android
- iOS

### Who can select and apply org wide backgrounds

Org wide backgrounds will only be visible to Teams Premium licensed users in their Background Settings panel.  

> [!NOTE]
> Org wide backgrounds will not be available for external or anonymous users.

### Who can view org wide backgrounds

While only licensed end users can select their choice of uploaded backgrounds, anyone can view the background that's applied to a meeting. These users include:

- In-tenant, Teams Premium licensed users
- In-tenant, non-licensed users
- External Users
- Anonymous users
