---
title: Set up immersive spaces for Teams
ms.author: tmilligan
author: typride
manager: tyadams
audience: ITPro
ms.reviewer: sekerawa
ms.date: 09/28/2023
ms.topic: quickstart
ms.service: msteams
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - teams-1p-app-admin
description: Learn how to set up immersive spaces for teams.
---


# Set up immersive spaces in Teams

The Mesh immersive spaces app is by default allowed in the Teams admin center. However, unlike other apps, users don't need to search for or pin it in Teams. Instead, they can access an immersive space in the View menu in any Microsoft Teams meeting.

To set up immersive spaces in Teams, you should:

- [Verify URLs, endpoints, and ports](#verify-endpoints-and-ports) are properly set up.
- [Create or edit app permission policy](#create-or-edit-app-permission-policy) to block specific people from accessing the app.

## What is an immersive space?

Connect in a 3D immersive space, helping hybrid meetings feel more like face-to-face connections. With just one click, you can easily connect with your team in a pre-built immersive space right from a Teams meeting.

:::image type="content" source="media/meeting-immersive-spaces-view-selector.png" alt-text="Immersive spaces view selector in Teams View menu":::

Use your avatar and join with a Meta Quest VR device to bring even more richness to the experience.  To learn more, [set up avatars for Microsoft Teams](meeting-avatars.md).

Immersive spaces work well for these types of meetings:

- *Weekly scrums* or standups with your team

- *Brainstorming sessions* with multiple break-out groups

- *Casual get-togethers* or celebrations for morale

- *Virtual networking events* across multiple groups

- *Onboarding meet-and-greets* for new team members

## License requirements

Mesh immersive spaces is available with the following licenses:

Teams Essentials, Microsoft 365 Business Basic, Microsoft 365 Business Standard, Microsoft 365 Business Premium, Microsoft 365 E3/E5, and Office 365 E1/E3/E5.

## Verify endpoints and ports

To ensure immersive spaces for Teams works properly, access to the following endpoints must be allowed by your firewall or proxy server.

### Ensure endpoints can be allowed for Mesh immersive spaces

To ensure the Mesh features work properly, the following endpoints must be allowed through your firewall or proxy server. All endpoints need to allow traffic on TCP ports 80 and 443:

- *.microsoft.com
- *.office.com
- *.office.net

### Firewall Ports for Mesh immersive spaces

In addition to the endpoints above, Mesh also requires the following outgoing ports to be opened in your firewall:

- TCP ports 80, 443

- TCP & UDP ports 30,000-30,499

- UDP ports 3478-3481

Mesh traffic usees IP addresses in the AzureCloud service tag.

For more information about service tags, see the [Virtual network service tags](/azure/virtual-network/service-tags-overview).

## Disallow or allow the app

> [!IMPORTANT]
> If you disallow or allow the Mesh immersive spaces app, the UI entry point for Immersive space will still be visible for up-to 24 hours.

## Create or edit app permission policy

If you want to allow or block the app for specific user groups, create or edit an app permission policy so that selected groups are allowed or blocked from the Mesh immersive spaces app.

> [!NOTE]
> It may be more complicated if the tenant already has different app permission policies for users or groups.

1. In the left panel, go to **Teams apps** > **Permission policies**.
1. In **App permission policies**, select **Add**.
1. Provide a name and description for the policy.
1. Under **Microsoft apps**, select **Block specific apps and allow all others**.
1. Search for and select the **Mesh immersive spaces** app, then select **Block**.

    :::image type="content" source="media/meetings-immersive-spaces-block-app.png" alt-text="Block the immersive spaces app in permissions policies window in teams admin center":::

> [!NOTE]
> Users may need to restart Teams for the App setup policy to take effect.

Now users in Teams should be able to join an immersive space in Microsoft Teams.

## Next steps for immersive spaces

To see all the features and learn more about immersive spaces, see [Immersive spaces in Teams](https://aka.ms/immersivespacesdocs).
