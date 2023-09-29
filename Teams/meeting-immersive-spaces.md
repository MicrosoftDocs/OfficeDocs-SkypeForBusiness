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
description: Learn ho to set up immersive spaces for teams.
---


# Set up immersive spaces in Teams

The Mesh immersive spaces app is allowed in the Teams Admin Center. Though, unlike other apps, to join an immersive space users will use the View switcher menu. There is no standalone app for immersive spaces.

To set up immersive spaces in Teams, you should:

- [Verify URLs, endpoints, and ports](#verify-endpoints-and-ports) are properly set up.
- [Allow the Mesh immersive spaces app](#verify-endpoints-and-ports) in the [Teams admin center](https://admin.teams.microsoft.com/dashboard).
- [Create or edit app permission policy](#create-or-edit-app-permission-policy) to block specific people from accessing the app.

## What is an immersive space

Connect in a 3D Immersive space to transform the feel of online and hybrid meetings into face-to-face connections. With just one click, you can easily connect with your team in a pre-built immersive space right from a Teams meetings.

:::image type="content" source="media/meeting-immersive-spaces-view-selector.png" alt-text="Immersive spaces view selector in Teams View menu":::

Use your avatar and join with a Meta Quest VR device to bring even more richness to the experience.  To learn more, [set up avatars for Microsoft Teams](meeting-avatars.md).

Immersive spaces work well for these types of meetings:

- *Weekly scrums* or standups with your team

- *Brainstorming sessions* with multiple break-out groups

- *Casual get-togethers* or celebrations for morale

- *Virtual networking events* across multiple groups

- *Onboarding meet-and-greets* for new team members

## Verify endpoints and ports

> [!IMPORTANT]
> If you disallow the Mesh immersive spaces app after allowing it, the UI entry point for Immersive space will **still be visible for up-to 24 hours** after its disallowed.


> [!IMPORTANT]
> Starting in Public Preview, IT Admins will need to take action in the Teams admin center. Specifically, review the app description and allow the Mesh Immersive Spaces app in the Teams Admin Center for it to continue functioning as expected. This applies even if you have previously allowed the app for your organization or a select group of users or if the app was automatically allowed because of a general policy on your tenant.
>
> If the app appears to be in the **Allowed** state, we highly recommend you toggle the status to **Blocked** then back to **Allowed** to ensure the app continues to work as expected.

To ensure immersive spaces for Teams works properly, access to the following endpoints must be allowed by your firewall or proxy server.

### Allow endpoints

All endpoints need to allow traffic on TCP ports 80 and 443:

- *.microsoft.com
- *.meshxp.net
- *.office.com
- *.office.net
- js.monitor.azure.com

### Firewall ports

In addition to the endpoints above, Mesh also requires the following outgoing ports to be opened in your firewall:

- TCP ports 80, 443
- TCP & UDP ports 30,000-31,000
- UDP ports 3478-3481

Mesh traffic will use IP addresses in the AzureCloud service tag.

For more information about service tags, see the [Azure service tags overview | Microsoft Learn](/azure/virtual-network/service-tags-overview).

## Allow the Mesh immersive spaces app

1. In the [Teams admin center](https://admin.teams.microsoft.com/dashboard), in the left-nav, go to **Teams apps** then select **Manage apps**.

1. In the **Search by name** text box, search for and select **Mesh immersive spaces**, then toggle it to **Allowed**.
:::image type="content" source="media/meetings-immersive-spaces-allow-app.png" alt-text="Allow immersive spaces app in the Teams admin center":::

## Create or edit app permission policy

If you want to allow or block the app for specific user groups, such as TAP opt-in users, create/edit an app permission policy so that selected groups are allowed or blocked from the Mesh immersive spaces app.

> [!NOTE]
> It may be more complicated if the tenant already has different app permission policies for users/groups.

1. In the left panel, go to **Teams apps** > **Permission policies**.
1. In **App permission policies**, select **Add**.
1. Provide a name and description for the policy.
1. Under **Microsoft apps**, select **Block specific apps and allow all others**.
1. Search for and select the **Mesh immersive spaces** app, then select **Block**.
:::image type="content" source="media/meetings-immersive-spaces-block-app.png" alt-text="Block the immersive spaces app in permissions policies window in teams admin center":::

> [!NOTE]
> Users may need to restart Teams for the App setup policy to take effect.

**Now users in Teams should be able to join an immersive space in Microsoft Teams!**

## Next steps for immersive spaces

It may not be immediately clear how we should use immersive spaces for work. To give you some inspiration, see how we use immersive spaces below.

### Try out some activities

- Schedule a meeting where one of the goals is to socialize and invite multiple people.
- Join the meeting and select the 'View' -> 'Immersive spaces' menu option to enter into the immersive space.
- Verify the right audio devices are configured.
- Experience how sound works within an audio zone.
- Teleport or walk out of the audio zone and have a side conversation with someone.
- Experiment by speaking to people at varying distances and locations.

## See the immersive spaces user documentation

To see all the features and learn more about immersive spaces, go to INSERT LINK TO SUPPORT.MSFT USER DOCS.
