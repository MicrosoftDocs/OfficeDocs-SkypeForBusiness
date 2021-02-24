---
title: Set up Microsoft Teams in your enterprise
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
description: Set up Teams in your enterprise to enable your users to collaborate using chat and file sharing, set up and attend small and large meetings, and talk via video and voice.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
appliesto: 
  - Microsoft Teams
---

# Set up Microsoft Teams in your enterprise

## Plan your deployment

[Teams enterprise deployment overview](deploy-enterprise-overview.md)

## Administration and team ownership

| Decision | Description |
|--|--|
| [Who should be Teams administrators?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#teams-administrators) | Admin roles can be used to grant specific permissions to people who you want to administer Teams. Small businesses may not need these extra roles because the same person may be responsible for all aspects of Teams. You can always add or remove administrators later on.<br><br>[Use Microsoft Teams administrator roles to manage Teams](using-admin-roles.md) |
| [Who should be Team owners and members?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#teams-owners-and-members) | Team owners control who can access a team and its channels. They can decide whether a team or channel is public (to the organization) or private and can set up policies like whether a channel should be moderated. Members can access the team and its channels (unless a channel is set to private and they're not a member of that channel) and can be designated as moderators.<br><br>[Assign team owners and members in Microsoft Teams](assign-roles-permissions.md) |

## Default settings and lifecycle policies

| Decision | Description |
|--|--|
| [What messaging policies should be applied?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#messaging-policies)  | Messaging policies control which chat and channel messaging features (such as who can use chat, who can edit and delete sent messages, and so on) are available to users in Teams. Teams has a global policy that applies to everyone. All of the features in the global policy are **On** by default.<br>If you want the same policy to apply to everyone, all you need to do is make changes to this global policy (for example, turn off meme support in conversations).<br>If you want different policies for different groups of people (for example, one policy for office workers and another for factory workers), you can create and assign policies. When you assign a policy to a user, the global policy no longer applies to them.<br><br>[Manage messaging policies in Teams](messaging-policies-in-teams.md) |
| [What Team settings should be applied?](enable-features-office-365#teams-settings) | Teams settings let you set up your teams for features such as email integration, cloud storage options, organization tab, meeting room device setup, and search scope. When you make changes to these settings, they apply to all the teams in your organization. <br><br>[Teams settings](enable-features-office-365#teams-settings)  |

## External and guest access

| Decision | Description |
|--|--|
| [Should external access be enabled?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#external-access) | External access lets anyone in another organization talk to people in your organization. This is useful when you have a close relationship with another organization, such as a supplier, and want to make it easy for people in either organization to chat with each other, hold meetings, and so on. <br>External access is different than guest access. External access gives everyone in an another organization access to interact with people in your organization. Guest access invites specific individuals access to interact with people in your organization.<br>External access is turned **Off** by default.<br><br>[Manage external access in Microsoft Teams](manage-external-access.md)  |
| [Should guest access be enabled?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#guest-access) |Guest access lets people in your organization invite people outside your organization access your teams and channels. Guest access is often used to collaborate with people outside your organization who don't have a formal relationship with yours. For example, you might invite a project planner to work on a project temporarily.<br>Guest access is different than external access. Guest access invites specific individuals access to interact with people in your organization. External access gives everyone in an another organization access to interact with people in your organization. <br>Guest access is turned **Off** by default. <br><br>[Turn on or turn off guest access to Microsoft Teams](set-up-guests.md)  |

## Compliance

## Security

## Deploy clients

When you're ready for your users to start using Teams, they can install the Teams client on their Windows, Mac, or Linux PC, or on their Android or iOS device. Users can download the Teams client directly from <https://teams.microsoft.com/downloads>.

Make sure everyone who will be using Teams has a Teams license. For more information about assigning a Teams license, see [Manage user access to Teams](user-access.md#using-the-microsoft-365-admin-center).

> [!TIP]
> Get recommendations on how to plan your Teams client deployment by completing the [Deploy Microsoft Teams clients](https://docs.microsoft.com/learn/modules/m365-teams-collab-deploy-clients/) module on Microsoft Learn.

If your organization uses Microsoft Endpoint Configuration Manager, Group Policy, or a third-party distribution mechanism, to deploy software to your user's computers, see [Install Microsoft Teams using Microsoft Endpoint Configuration Manager](msi-deployment.md).

If you want detailed information about deploying Teams clients, see [Get clients for Microsoft Teams](get-clients.md).

## Training

For information on how to train your users to use Teams, see [Microsoft Teams training](training-microsoft-teams-landing-page.md).