---
title: Manage the Mesh app in Microsoft Teams
ms.author: tmilligan
author: typride
manager: tyadams
audience: ITPro
ms.reviewer: sekerawa
ms.date: 05/29/24
ms.topic: quickstart
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

1. [Verify URLs, endpoints, and ports](#verify-endpoints-and-ports) are properly set up.

1. Manage user access to the Mesh app using one of the following options:
    1. [Use app centric management for immersive spaces in Teams](#use-app-centric-management-for-immersive-spaces-in-teams)
    1. [Use app permission policies for immersive spaces in Teams](#use-app-permission-policies-for-immersive-spaces-in-teams)
    1. [Use service plans in the Microsoft 365 Admin Center to allow immersive spaces for Teams](#use-service-plans-in-the-microsoft-365-admin-center-to-allow-immersive-spaces-for-teams)

## What is an immersive space?

Connect in a 3D immersive space, helping hybrid meetings feel more like face-to-face connections. With just one click, you can easily connect with your team in a pre-built immersive space right from a Teams meeting.

In a Microsoft Teams meeting, select **View** > **Immersive space (3D)**.

:::image type="content" source="media/meeting-immersive-spaces-view-selector-v2.png" alt-text="Screenshot of mmersive spaces view selector in Teams View menu.":::

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

To ensure immersive spaces in Teams works properly, access to the following endpoints must be allowed through your firewall or proxy server.

### Ensure endpoints can be allowed for Mesh app

To ensure the Mesh features work properly, the following endpoints must be allowed through your firewall or proxy server. All endpoints need to allow traffic on TCP ports 80 and 443:

- *.microsoft.com
- *.office.com
- *.office.net

### Firewall Ports for Mesh

In addition to the endpoints, Mesh also requires the following outgoing ports to be opened in your firewall:

- TCP ports 80, 443

- TCP & UDP ports 30,000-30,499

- UDP ports 3478-3481

> [!IMPORTANT]
>Mesh traffic uses IP addresses in the AzureCloud service tag.
>For more information about service tags, see the [Virtual network service tags](/azure/virtual-network/service-tags-overview).

## Use app centric management for immersive spaces in Teams

> [!IMPORTANT]
> App centric management of Teams apps is a new feature. For more info on this rollout see [Use app centric management to manage apps | Microsoft Learn](app-centric-management.md).

App centric management functionality introduces a new way to control how you control access to Teams apps for users and groups. It replaces app permission policies. This functionality lets you specify which users and groups can use each app and you can control it on a per-app basis.

When you start using this functionality, we retain your existing app access that you defined using permission policies. Users continue to have access to only those apps that you allow for them.

## Use app permission policies for immersive spaces in Teams

> [!IMPORTANT]
> If you disallow or allow the Mesh app, the UI entry point for Immersive space will still be visible for up-to 24 hours.

The **Mesh app is by default allowed in the Teams admin center**. If you want to allow or block the app for specific user groups, create or edit an app permission policy.

> [!NOTE]
> It may be more complicated if the tenant already has different app permission policies for users or groups.

1. In the left panel, go to **Teams apps** > **Permission policies**.
1. In **App permission policies**, select **Add**.
1. Provide a name and description for the policy.
1. Under **Microsoft apps**, select **Block specific apps and allow all others**.
1. Search for and select the **Mesh** app, then select **Block**.

    :::image type="content" alt-text="Block the immersive spaces app in permissions policies window in teams admin center." source="media/meetings-immersive-spaces-block-app2.png" lightbox="media/meetings-immersive-spaces-block-app2.png":::

> [!NOTE]
> Users may need to restart Teams for the App setup policy to take effect.

Now users in Teams should be able to join an immersive space in Microsoft Teams.

## Use service plans in the Microsoft 365 Admin Center to allow immersive spaces for Teams

1. Sign into [Microsoft 365 Admin Center](https://admin.microsoft.com/) with an admin account with at least Global, License, or User level permissions and open the left navigation panel to the Users section.

1. Select the user or user group and go to **Licenses and apps** to manage the active licenses and service plans.

1. Ensure that you enabled the appropriate licenses for Immersive spaces for Teams.

For more guidance for assigning licenses in Microsoft 365, see:

[Assign or unassign licenses for users in the Microsoft 365 admin center - Microsoft 365 admin | Microsoft Learn](/microsoft-365/admin/manage/assign-licenses-to-users).

For more complex and larger group license management, you can do [Assign licenses to a group - Microsoft Entra ID | Microsoft Learn](/entra/identity/users/licensing-groups-assign).

## Next steps for immersive spaces

To see all the features and learn more about immersive spaces, see [Immersive spaces in Teams](https://aka.ms/immersivespacesdocs).
