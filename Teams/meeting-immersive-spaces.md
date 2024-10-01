---
title: Manage the Mesh app in Microsoft Teams
ms.author: tmilligan
author: typride
manager: tyadams
audience: ITPro
ms.reviewer: sekerawa
ms.date: 10/01/2024
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - teams-1p-app-admin
description: Learn how to set up immersive spaces for teams.
---


# Manage the Mesh app in Microsoft Teams

The Mesh app, which enables immersive spaces in Teams, is enabled by default in the Teams Admin Center. This app allows users to change the [View in a Teams meeting to an immersive space](https://support.microsoft.com/en-us/office/get-started-with-immersive-spaces-in-microsoft-teams-4a6182f8-0f43-4c24-bb66-ef229fa221d8). However, unlike other apps in Teams, users don't need to search for or pin it in. Instead, they only access an immersive space in the View menu in any Microsoft Teams meeting.

To set up immersive spaces in Teams, you should:

1. [Verify endpoints and ports](#verify-endpoints-and-ports) are properly set up.

1. Manage user access to the Mesh app using one of the following options:
    1. [Manage access to immersive spaces in Teams using app centric management](#use-app-centric-management-for-immersive-spaces-in-teams)
    1. [Block immersive spaces in Teams for specific users or groups](#block-immersive-spaces-in-teams-for-specific-users-or-groups)
    1. [Allow immersive spaces in Teams using service plans in the Microsoft 365 Admin Center](#allow-immersive-spaces-for-teams-using-service-plans-in-the-microsoft-365-admin-center)

## What is an immersive space?

Connect in a 3D immersive space, helping hybrid meetings feel more like face-to-face connections. With a few clicks, you can easily connect with your team in a prebuilt immersive space right from a Teams meeting.

In a Microsoft Teams meeting, select **View** > **Immersive space (3D)**.

:::image type="content" source="media/meeting-immersive-spaces-view-selector-v2.png" alt-text="Screenshot of immersive spaces view selector in Teams View menu.":::

Use your avatar and join with a Meta Quest VR device to bring even more richness to the experience.  To learn more, [set up avatars for Microsoft Teams](meeting-avatars.md).

Immersive spaces work well for these types of meetings:

- *Weekly scrums* or standups with your team

- *Brainstorming sessions* with multiple break-out groups

- *Casual get-togethers* or celebrations for morale

- *Virtual networking events* across multiple groups

- *Onboarding meet-and-greets* for new team members

## License requirements

Immersive spaces in Teams is available with the following licenses:

Teams Essentials, Microsoft 365 Business Basic, Microsoft 365 Business Standard, Microsoft 365 Business Premium, Microsoft 365 E3/E5, and Office 365 E1/E3/E5.

## Verify endpoints and ports

This section outlines the specific endpoints and firewall requirements for the Mesh app in Teams, which allows users to join an immersive space (3D) while in a Teams meeting.

Configure your enterprise firewall settings to align with the standard set of Microsoft 365 requirements for **Microsoft Teams**, and **Microsoft 365 Common** outlined in [Microsoft M365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide&preserve-view=true).

As part of this, ensure that you have configured your firewall to enable traffic to `*.cloud.microsoft.com`, `*.office.com`, and `*.microsoft.com` over `TCP 443`, `80`.

Mesh also requires the IP addresses and port ranges detailed in [Firewall configuration for Azure Communication Services](https://learn.microsoft.com/azure/communication-services/concepts/voice-video-calling/network-requirements#firewall-configuration) for media capabilities such as audio, video, and screenshare.

Without access to these, Mesh won't work properly for users in your organization.

## Use app centric management for immersive spaces in Teams

> [!IMPORTANT]
> App centric management of Teams apps is a new feature. For more info on this rollout see [Use app centric management to manage apps | Microsoft Learn](app-centric-management.md).

## Block immersive spaces in Teams for specific users or groups

> [!IMPORTANT]
> If you disallow or allow the Mesh app, the UI entry point for Immersive space will still be visible for up-to 24 hours.

The **Mesh app is by default allowed in the Teams admin center**. If you want to allow or block the app for specific user groups, configure availability via **Manage apps**.

> [!NOTE]
> It may be more complicated if the tenant already has different app permission policies for users or groups.

1. Sign in to the [Microsoft Teams Admin Center](https://admin.teams.microsoft.com/).
1. In the left panel, go to **Teams apps** > **Manage apps**.
1. Search for the app named "Mesh" and open the app settings.
1. To block the app, select **Actions** at the top right and select **Block app**.
1. To block the app for specific users or groups:
    1. Under the **Users and groups** tab, choose edit availability.
    2. Under the **Users and groups** tab, select edit availability and configure as needed.

:::image type="content" source="media/meetings-immersive-spaces-availability.png" alt-text="Screenshot of the Teams Admin Center showing how to manage the availability of the Mesh application." lightbox="media/meetings-immersive-spaces-availability.png":::

> [!NOTE]
> Users may need to restart Teams for the App setup policy to take effect.

Now users in Teams should be able to join an immersive space in Microsoft Teams.

## Allow immersive spaces for Teams using service plans in the Microsoft 365 Admin Center

1. Sign into [Microsoft 365 Admin Center](https://admin.microsoft.com/) with an admin account with at least Global, License, or User level permissions and open the left navigation panel to the Users section.

1. Select the user or user group and go to **Licenses and apps** to manage the active licenses and service plans.

1. Ensure that you enabled the appropriate licenses for Immersive spaces for Teams.

For more information about assigning licenses in Microsoft 365, see:

[Assign or unassign licenses for users in the Microsoft 365 admin center - Microsoft 365 admin | Microsoft Learn](/microsoft-365/admin/manage/assign-licenses-to-users).

For more complex and larger group license management, you can do [Assign licenses to a group - Microsoft Entra ID | Microsoft Learn](/entra/identity/users/licensing-groups-assign).

## Next steps for immersive spaces

To see all the features and learn more about immersive spaces, see [Immersive spaces in Teams](https://aka.ms/immersivespacesdocs).
