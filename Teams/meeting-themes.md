---
title: Create and manage meeting themes for Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.date: 2/29/2024
ms.reviewer: nraghavan
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
appliesto: 
  - Microsoft Teams
f1.keywords:
  - CSH
ms.localizationpriority: medium
search.appverid: MET150
description: Using approved corporate branding assets like images and logos to create custom meeting themes for Teams meetings within your organization.
---

# Create and manage meeting themes for Teams meetings

**APPLIES TO:** ✔️Meetings ✖️Webinars ✖️Town halls

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

## Overview

Meeting themes consist of your organization’s brand colors, a custom image to represent your org, and your org’s logo. Applying a custom theme allows you, as an admin, to customize the visual appearance of the meeting invite, prejoin, and lobby screens for your users' meetings. Meeting themes don't apply to webinars; instead, the webinar registration page is used for configuring the webinar's branding for registration and emails.

Customization in Teams meetings allows organizations to extend their visual identities across the meeting experience. An organization’s images and colors help foster internal corporate culture building and increase overall brand awareness with guests. With the help of an organization's brand management and corporate communications teams, you can easily set up and create meeting themes for various business units and departments within a single tenant.

Teams premium licensed users with an assigned meeting customization policy can create meetings with meeting themes. Anyone who joins these meetings can see the themes (including unlicensed internal users, guests, and anonymous users). 

:::image type="content" source="media/meeting-themes-edu-small.png" alt-text="Screenshot of Contoso Education's meeting theme featuring their brand logo, image, and colors." lightbox="media/meeting-themes-edu.png":::

> [!IMPORTANT]
> Microsoft doesn't validate the ownership of brand logos or images associated with meeting themes. When your users join meetings with other organizations, they should always verify the authenticity of the organization they're meeting with.

> [!NOTE]
> Uploaded images and their associated image URL are visible to all meeting participants; including external users, guests, unauthenticated users, and anyone with a link to join the meeting. To stop displaying your images, you must delete the images from your meeting theme. To remove images from a meeting theme, navigate to the **Meeting customization policy** in the Teams admin center, select the chosen meeting theme, and select **Edit meeting theme**.

## Prerequisites

Before setting up meeting themes in Teams meetings, check to make sure you have the following items:

- The users who need to use meeting themes have a Teams Premium license.
- You’re an admin with access to the Teams admin center or you have an assigned customization policy.
- Your [custom logo](#2-add-a-custom-logo), [image](#3-add-a-custom-image), and [color](#4-add-a-custom-color) meet the required specifications.

## Set up and manage meeting themes in the Teams admin center

Meeting themes house the following assets for your theme:

- Logo - Your organization's logo.
- Custom image - A brand image from your organization (custom images aren't the same as [custom meeting backgrounds](custom-meeting-backgrounds.md)).
- Custom color - We recommend using either your brand's primary or secondary color - whichever one best complements your brand image and logo.

As an admin, you can set up and manage meeting themes for Teams meetings with the Teams admin center or PowerShell.

### 1. Create or edit a customization policy

To create or manage meeting themes, you need to create a new meeting customization policy or modify an existing policy.
To enable the custom background policy, perform the following steps:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Customization policies**
4. Either select an existing policy or create a new one.
5. Within your chosen policy, navigate to the **Customize meeting visuals** section.
6. If you're creating a new policy, select the **Add a theme** button to upload your assets. If you're managing an existing policy, select the **Edit meeting themes** button if you'd like to make changes to your theme.
7. Toggle the **Currently Active** setting to **Yes** to enable your theme.
8. Select **Save**

> [!NOTE]
> Although you can access custom meeting visuals from the meeting policies page, we recommend accessing it through customization policies to avoid navigating through global organizational default policies.

### 2. Add a custom logo

Teams meetings support square logos that appear on key surfaces during your meeting, including the lobby screen. Logo images must meet Microsoft accessibility contrast ratios (4:5:1). We recommend using a square icon style logo with minimal text and the dimensions of 800 x 800 pixels.

Uploads must adhere to the following parameters. An admin can only upload:

- PNG and JPEG image formats of your logo.
- Two variations of the logo images that appear on the Pre-Join and Lobby UI:
  - Dark theme brand logo
  - Light theme brand logo
- A logo image  with a maximum size of 5 MB.
- A logo image with a minimum dimension of 576 x 576 pixels.
- Upload one image per theme from your device.

### 3. Add a custom image

Teams meetings support an organization's images that display on the meetings screen and provide a colorful backdrop to your meetings. We recommend using an image with the dimensions of 1440 x 810 pixels.

> [!NOTE]
> These images aren't the same as [custom meeting backgrounds](custom-meeting-backgrounds.md).

Custom images must meet Microsoft accessibility contrast ratios (4:5:1), and uploads must follow these parameters:

- PNG and JPEG image formats of your brand image.
- Two variations of the brand images that appear on the Pre-Join and Lobby UI:
  - Dark theme brand image
  - Light theme brand image
- Brand images with max size of 5 MB.
- Brand images with following dimensions:
  - Minimum dimensions: 1024 x 574 pixels
  - Maximum dimensions: 3840 x 2160 pixels
- Upload a minimum of 0 and a maximum of one image per theme from your device.

### 4. Add a custom color

Teams meetings support an organization's primary or secondary color in the meeting experience. You can enter the hex code value of your organization's color, which displays on key surfaces of the meeting experience.

To support Microsoft accessibility standards, the final color generated might not match your brand color.

### 5. Preview your meeting theme

Once you add your meeting assets, you can preview how your theme looks before saving. Selecting **Preview** opens the preview dialog and shows the newly defined theme for desktop.

### 6. Save your meeting theme

By selecting **Save**, the meeting theme is automatically saved and applied to your meetings. Selecting **Save and apply for later** saves the meeting theme, but doesn't apply it to any of your meetings. To apply this theme, select **Save** on the meeting theme creator, or use the **Currently active** toggle on the meeting theme table on the customization policy page.

### Manage meeting themes in PowerShell

 To upload images, you must use the Teams admin center. You can manage meeting themes by using the following PowerShell cmdlets in Teams PowerShell:

- [Set-CsTeamsMeetingBrandingPolicy](/powershell/module/teams/set-csteamsmeetingbrandingpolicy)
- [Grant-CsTeamsMeetingBrandingPolicy](/powershell/module/teams/grant-csteamsmeetingbrandingpolicy)
- [New-CsTeamsMeetingBrandingPolicy](/powershell/module/teams/new-csteamsmeetingbrandingpolicy)

This example assigns a meeting theme policy called 'Policy Test' to a group named group@contoso.com.

```PowerShell
Grant-CsTeamsMeetingBrandingPolicy -Group group@contoso.com -PolicyName "Policy Test" -Rank 1
```

This example assigns a meeting theme policy called 'Policy Test' to a user named alice@contoso.com.

```PowerShell
Grant-CsTeamsMeetingBrandingPolicy -identity " alice@contoso.com" -PolicyName "Policy Test"
```

### Assigning a meeting customization policy to users

Meeting customization policies can be assigned to one, many, or a predefined user group in your Tenant. Make sure that these users have a Teams premium license to use these features.

- All licensed users automatically get the global default policy assigned to them.
- Custom customization policies override the global default.
- A licensed user can only be assigned one customization policy.

## Where are meeting themes visible

Supported clients:

- Desktop client
- Web client (Meeting themes aren't currently supported on Safari or Firefox)
- Android (Versions 11+ only)
- iOS

> [!NOTE]
> Images aren't visible on mobile clients.

|  Asset type       | Join Launcher | Meeting Pre-Join | Meeting Lobby | Meeting Stage | Meeting invite |
| :---:          |     :---:      |         :---:  |         :---:  |         :---:  |       :---:  |
| **Logo**   | Yes | Yes| Yes| No| Yes |
| **Image**     | Yes | Yes| Yes| No| No |
| **Color**     | Yes | Yes| Yes| Yes| No |

> [!NOTE]
> Logos added to the meeting theme override any logos you upload to meeting invitations. To learn more about meeting invitations, see [Customize meeting invitations](customize-meeting-invitations.md).
> [!NOTE]
> If  your users edit a meeting invite with Teams calendar after sending it, the logo might not appear when they resend the invite.

## Who can view a meeting theme

While only licensed users who are assigned a meeting customization policy can create meeting themes-enabled meetings, anyone can view the themes that are applied to a meeting. These users include:

- In-tenant, Teams Premium licensed users
- In-tenant, nonlicensed users
- Guest of Tenant users
- External Users
- Anonymous users

## Allow organizers to turn off meeting themes for a meeting

Admins can allow meeting organizers to disable meeting themes for a specific meeting. Disabling meeting themes returns the meeting to the default Teams theme.

To give your meeting organizers the ability to disable meeting themes:

1. Navigate to the **Meeting customization policy**.
1. Toggle the **Allow organizer to control meeting theme** setting to **On**.

Meeting organizers can turn off meeting themes by:

1. Navigating to the **Meeting options** menu for a meeting.
1. Toggling the **Meeting theme** meeting option to **Off**.

> [!NOTE]
>
> - For recurring meetings or series, the meeting option applies for every instance of the meeting.
> - Meeting themes aren't disabled for meetings that are in-progress. To apply changes, your users must end the call and restart the meeting.

## Best practices for meeting themes

- Only use your organization's official image assets. Don't use image content that you don't own.
- Work with your brand and marketing team to ensure that your image assets and colors together follow your organization's brand guidelines.
- Ensure you're using high-quality logo images, which are visible on small and large screen devices.
- Colors generated in the Teams App might differ from your brand colors. This process was created to ensure Microsoft Accessibility Standards are met.
- Users with high-contrast device settings can't see meeting themes.

### Accessibility

Here are a few points to ensure accessibility requirements are met:

- Follow existing UI patterns and structure – The current structure and text on the screen aren’t being modified with this feature.
- Image Contrast Ratio – Image assets are required to meet the 4:5:1 color contrast ratio.  
- Accessible Color Generation Support – We calculate the accessible color output that is the closest match to the brand color input while maintain Microsoft Accessibility standards.  
- High Contrast support – For users with high contrast settings enabled, branding doesn't apply. They continue to see the default Teams meeting experience.
- Admin Controls – Admins can prevent users with accessibility concerns from seeing the branding through:
  - Policy control – ensuring they're not added to a customization policy. This control prevents them from creating branding-enabled meetings.
  - Meeting Options – meeting organizers can turn off branding for a meeting if a user with accessibility concerns joins their meeting.

## Use cases for multiple departments or business units in one tenant

Some organizations have multiple business units under different brand identities within the same tenant. In these cases, you can create meeting customization policies that are dedicated to each brand. They can also assign a department or business unit user group to a specific policy.

Contoso Ltd. has a single Tenant in Microsoft Teams, containing the user profiles of all their employees across different business organizations. The company is looking to adopt custom branded meetings in Teams to increase their brand presence with their clients and encourage an internal corporate culture.

Contoso has two business units (BUs) under their organization: Contoso Technical Services and Contoso Education. Both BUs have their own distinct brand imagery, and want to display their branding during their internal and external meetings.

To support this use case, Tenant Admins can create two distinct customization policies:

- Policy A - Contoso Technical Services – houses Contoso Technical Service’s brand logo, image, and color.
- Policy B - Contoso Education – houses Contoso Education’s brand logo, image, and color.

They can proceed to assign the licensed employees in Contoso Technical Services to Policy A, and licensed employees of Contoso Education to Policy B.

:::image type="content" source="media/meeting-themes-tech-services-small.png" alt-text="Screenshot of policy A, Contoso Technical Services' meeting theme featuring their brand logo, image, and colors." lightbox="media/meeting-themes-tech-services.png":::
