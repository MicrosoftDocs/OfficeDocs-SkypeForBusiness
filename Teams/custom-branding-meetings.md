---
title: Meeting themes for Teams meetings
author: MicrosoftHeidi
ms.author: heidip
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
description: Using approved corporate assets like images and logos to create a custom branded experience for Teams meetings within your organization.
---

# Meeting themes for Teams meetings

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

Customization in Teams meetings allows organizations to extend their visual identities across the meeting experience. An organization’s images and colors help foster internal corporate culture building and increase overall brand awareness with external meeting participants. With the help of an organization's brand management and corporate communications teams, tenant admins can easily set up and create meeting themes for various business units and departments within a single tenant.
By default, Teams premium licensed users who have been assigned a meeting customization policy can create meeting themes-enabled meetings. These meetings feature themes by default, and anyone who joins the meetings can see the themes (including unlicensed internal, external, and anonymous users).

> [!NOTE]
> Attendees joining Teams through the Web experience won't be able to see meeting themes.

## Pre-requisites

Before setting up meeting themes in Teams Meetings, check to make sure you have the following items:

- Access to Teams Premium SKU
- You’re an admin with access to the Teams admin center or you’ve been assigned a customization policy
- Your [custom logo](#adding-a-custom-logo-image), [image](#adding-a-custom-image), and [color](#adding-a-custom-color) meet the required specifications

## Setting up meeting branding

Tenant admins can set up and manage meeting themes for Teams meetings in the Teams admin center.

### Creating a customization policy

To create meeting themes, admins will first need to create a new meeting customization policy or modify their existing policy.
To enable the custom background policy, admins will perform the following:

1. Open the Teams admin center
2. Select **Meetings** from the navigation pane
3. Under **Meetings**, select **Customization Policies**
4. Either select an existing policy or create a new one
5. Within your chosen policy, navigate to the **Custom Meeting Visuals** section
6. Toggle the **Currently Active** setting from off to **on** to enable the setting
7. Select **Save** to enable meeting themes

> [!NOTE]
> Although you can access Custom Meeting Visuals from the Meeting Policies page, we recommend accessing it through  Customization Policies to avoid navigation through global organization default policies.

Within the meeting customization policy, admins can begin defining their branding by creating a meeting theme.

Meeting themes house the brand assets for your theme. These include the following assets:

- Logo - your organization's logo image.
- Custom image - a brand image from your organization (custom images aren't the same as [custom meeting backgrounds](custom-org-defined-backgrounds.md)).
- Custom color - it's recommended to use either your brand's primary or secondary color - whichever one best complements your brand image and logo.

To create a new theme, select **Add meeting theme**.

### Adding a custom logo image

Teams Meetings supports square logos that appear on key surfaces during your meeting, including the lobby screen. Logo images must meet Microsoft accessibility contrast ratios (4:5:1).

Uploads must adhere to the following parameters. An admin can only upload:

- PNG and JPEG image formats for their logo.
- a logo image with a maximum size of 5 MB.
- logo images with a minimum dimension of 576 px X 576 px.
- only one image per theme from their device.

Admins will upload 2 variations of the logo images that will appear on the Pre-Join and Lobby UI:
  
- Dark Theme Brand Logo
- Light Theme Brand Logo 

> [!NOTE]
> Light Theme Brand Logos will be available in future updates.

### Adding a custom image

Teams meetings support an organization's images that skin the meetings screen and provide a colorful backdrop to your meetings.

> [!NOTE]
> These images aren't the same as [custom meeting backgrounds](custom-org-defined-backgrounds.md)

Custom images must meet Microsoft accessibility contrast ratios (4:5:1), and uploads must follow these parameters:

- Admin can only upload PNG and JPEG image formats for brand image
- Admin can only upload brand image with max size of 5 MB
- Admin can upload brand image with following dimensions:
  - Minimum dimensions: 360 px X 360 px
  - Maximum dimensions: 2048 px X 2048 px
- Admin can upload a minimum of 0 and a maximum of one image per theme from their device

### Adding a custom color

Teams meetings support an organization's primary or secondary color in the meeting experience. You can enter the hex code value of your organization's color, which will appear on key surfaces of the meeting experience.

> [!NOTE]
> To support Microsoft accessibility standards, the final color generated may not match your brand color.

### Previewing a meeting theme

Once you've added your meeting assets, you can preview how your theme will look before saving.  Selecting **Preview** will open the preview dialog and show the newly defined theme for both desktop and mobile.

### Save meeting theme

By selecting **Save**, the meeting theme is automatically saved and applied to your meetings. Selecting **Save and apply for later** will save the meeting theme, but won't apply it to any of your meetings. To apply this theme, select **Save** on the meeting theme creator, or use the **Currently active** toggle on the meeting theme table on the customization policy page.



### Assigning a meeting customization policy to users

Meeting customization policies can be assigned to one, many, or a pre-defined user group your Tenant. Make sure that these users have a Teams premium license to use these features.

- By default, all licensed users will get the Global Default policy assigned to them.
- Custom Customization Policies will override the global default
- A licensed user can only be assigned one customization policy

### Use cases for multiple departments or business units in one tenant

Some organizations have more than one business unit or department under a different brand identity which live within the same tenant. In these cases, admins can create meeting customization policies that are dedicated to each brand, and assign a department or business unit user group to a specific policy.

#### A use case

Contoso Ltd. has a single Tenant in Microsoft Teams, containing the user profiles of all their employees across different business organizations. The company is looking to adopt custom branded meetings in Teams to increase their brand presence with their clients and encourage an internal corporate culture.

Contoso has two business units (BUs) under their organization: Contoso Technical Services and Contoso Education. Both BUs have their own distinct brand imagery, and want to display their branding during their internal and external meetings.

To support this use case, Tenant Admins can create two distinct customization policies:

- Policy A - Contoso Technical Services – houses Contoso Technical Service’s brand logo, image, and color
- Policy B - Contoso Education – houses Contoso Education’s brand logo, image, and color

They can proceed to assign the licensed employees in Contoso Technical Services to Policy A, and licensed employees of Contoso Education to Policy B.

## Where are meeting themes visible

Supported clients:

- Desktop client
- Android (Versions 11+ only)
- iOS

|         | Join Launcher | Meeting Pre-Join | Meeting Lobby | Meeting Stage |
| :---:          |     :---:      |         :---:  |         :---:  |         :---:  |
| **Logo**   | No | Yes| Yes| Yes|
| **Image**     | No | Yes| Yes| Yes|
| **Color**     | Yes | Yes| Yes| Yes|

Logos and images will be available for Join Launcher in future updates.
> [!NOTE]
> Webinars will use premium meeting branding for the in-meeting branding experience and continue to use webinar branding for the registration webpage and email. Meeting organizers will have the ability to turn off meeting branding for a webinar instance using the opt-out meeting option.

### Who can view a meeting theme

While only licensed users who are assigned a meeting customization policy can create meeting themes-enabled meetings, anyone can view the themes that are applied to a meeting. These users include:

- In-tenant, Teams Premium licensed users
- In-tenant, non-licensed users
- Guest of Tenant users
- External Users
- Anonymous users

### How to turn off meeting themes for a meeting

Tenant Admins can allow meeting organizers to disable meeting themes for a specific meeting instance. Disabling meeting themes will return the meeting to the default Teams theme.

To give meeting organizers the ability to disable Meeting Themes:

1. Navigate to the **Meeting customization policy**.
1. Toggle the setting **"Meeting Theme" that allows organizers to turn off the meeting theme for specific meetings**.

Meeting organizers can turn off meeting themes by:

1. Navigating to the **Meeting options** menu for a meeting instance.
1. Toggling off the meeting option **Allow organizers to turn off meeting theme**.

> [!NOTE]
>
> - For recurring meetings or series, the meeting option will apply for every instance of the meeting.
> - Meeting themes won't be disabled for meetings that are in-progress. To apply changes, you must end the call and restart the meeting.

## Best practices for meeting themes

- Only use your organization's official image assets. Don't use image content that you don't own.
- Work with your brand and marketing team to ensure that your image assets and colors together follow your organization's brand guidelines.
- Ensure you're using high-quality logo images, which are visible on small and large screen devices.
- Colors generated in the Teams App may differ from your brand colors. This is to ensure Microsoft Accessibility Standards are met.
- Users with high-contrast device settings won't see meeting themes.

### Accessibility

Here are a few points to ensure accessibility requirements are met:

- Follow existing UI patterns and structure – The current structure and text on the screen aren’t being modified with this feature.
- Image Contrast Ratio – Image assets are required to meet the 4:5:1 color contrast ratio.  
- Accessible Color Generation Support – We calculate the accessible color output that is the closest match to the brand color input while maintain Microsoft Accessibility standards  
- High Contrast support – For users with high contrast settings enabled, branding does not apply. They will continue to see the default Teams meeting experience.
- IT Admin Controls – IT Admins can prevent users with accessibility concerns from seeing the branding by: 
  - Policy control – ensuring they are not added to a customization policy. This will prevent them from creating branding-enabled meetings.
  - Meeting Options – meeting organizers can turn off branding for a meeting if a user with accessibility concerns will be joining the meeting.
