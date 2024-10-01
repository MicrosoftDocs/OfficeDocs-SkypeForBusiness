---
title: Microsoft Teams apps permissions and consent
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
search.appverid: MET150
ms.date: 07/08/2024
ms.reviewer: Orion.OMalley
description: Understand permissions that Teams apps request to access your organization and user information.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Understand the permissions of and the information accessed by Teams apps

Depending on their functionality, Teams apps may or may not access your user's or your organization's information to work as intended.

* Some apps don't seek access to organization's information and hence don't require any approval. Users can use such apps without admin approval or consent as organization's information is secured from such apps.
* Some apps require your organization's or user's information to work or to process the information. Such apps can't work unless you allow such an app to access your org's information.

You must evaluate the compliance, security, and data handling information of an app and also understand the permissions requested by the app before you allow an app to be used by your users. To do so, you need to understand about permissions, consent, and the controls available to you.

Permissions enable apps to access privileged resources and act on behalf of the user. This allows developers to create rich features in apps that boost user productivity. You must understand about permissions, their scope, and implications clearly. We provide all permissions of an app and its detailed info in the app details page in Teams admin center.

## How apps access organization's information using permissions

Teams provides safeguards so that your organization's or user's information can't be accessed without your consent. For an app to access any information, the following actions must happen:

1. App developers declare permissions and [app capabilities](apps-in-teams.md#understand-app-capabilities) when they create apps.
1. Admins understand and analyze the permissions required by the app in admin portals.
1. Data access is granted in two ways. When the app is added to Teams, it's granted access to some basic capabilities that may include access to basic information. Upon granting consent, an app receives access to some data of user and organization or both, based on app permissions that it requested consent for.

## Understand data access by apps and the required permissions

An application can access an organization's information in the following two ways:

* **Delegated access**: An application accesses the resource on behalf of the user. This access requires delegated permissions. The application can access only the information that the user can access themselves.
* **Application access**: An application acts on its own with no user signed in, when it's undesirable to have a specific user signed in or when the data required can't be scoped to a single user. This access required applications permissions. An application if granted consent is able to access data that the permission is associated with.

| Admin consideration                 | Delegated permissions                                                                                                                 | Application permissions                                 |
|---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| How can apps access information | On behalf of a signed-in user.                                                                                                        | On their own, using their own identity.                 |
| What information is accessed    | Permissions that app is granted consent to and the information associated with that permission that the signed-in user has access to. | Any info that a consented permission is associated with |
| What roles can consent          | Admins or users or group owners depending on Microsoft Entra ID configuration                                                         | Only admins                                             |
| Can users consent               | Users can consent depending on Microsoft Entra ID configuration                                                                       | Only admins can consent                                 |

For each app, its permissions are listed in the app details page in the admin center.

| App permission type | Access context | Declaration source | When is consent required? | Who all can consent? |
|---------------------|----------------|--------------------|---------------------------|------------------|
| [Microsoft Entra ID for Graph and legacy endpoint access](#microsoft-entra-id-permissions) | Delegated | Microsoft Entra ID  | App sign-in  | Global Admin, Cloud Admin, and Application Admin |
| [Microsoft Entra ID for Graph and legacy endpoint access](#microsoft-entra-id-permissions) | Application | Microsoft Entra ID  |  App sign-in  |  Global Admin, Cloud Admin, and Application Admin |
| [RSC for information of teams, chats, and users](#resource-specific-consent-permissions) | Delegated | App manifest file | Adding app to a team, chat, meetings | Resource owner |
| [RSC for information of teams, chats, and users](#resource-specific-consent-permissions) | Application | App manifest file |  Adding app to a team, chat, meetings  | Resource owner |
| [Other permissions and data access](#what-can-apps-do-in-teams) | Delegated via SDKs | Manifest properties define it | Add app in a client | Consent is implied at install |

We recommend using a lower privilege role to accomplish tasks where possible. Use Global Administrator role only when necessary.

## Where can admins see all permissions of an app

You can find the details of all types of permissions requested by an app in the Permissions tab of the app details page. Optionally, you can also download all the permissions in a .csv file for further analysis.

:::image type="content" source="media/app-permissions.png" alt-text="Screenshot showing the page in admin center that list and requests permissions for an app and also allows admins to grant consent for such permissions for all org-users."  lightbox="media/app-permissions-details.png":::

   * **A**: All the Application permissions of the app.
   * **B**: All the Delegated permissions of the app.
   * **C**: [Basic capabilities and interactions with user and data accessed by apps](#what-can-apps-do-in-teams)

To know how you can permit use of an app, see [grant and manage consent to Teams app permissions](manage-consent-app-permissions.md).

## Microsoft Entra ID permissions

Microsoft Graph lets developers access your organization's Microsoft 365 information and data but only with the appropriate Microsoft Entra ID permissions. An app declares these permissions upfront and admins must consent to these permissions before the app can access the info. If you grant admin consent to such a permission in a Teams app, then all allowed users of your org can use the app and let the app access org's information. These permissions are defined in Microsoft Entra ID portal.

App developers choose appropriate permissions from a wide variety of Graph APIs so that the apps get the necessary information to work. Before you grant consent to these permissions, you can view the specific permissions requested by an app. It helps you evaluate the impact of granting consent to an app's permissions. To view the Microsoft Entra ID permissions, follow these steps:

1. Access Teams admin center and open the **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page.

1. Search for the required app and select its name to open the app details page.

1. Select **Permissions** tab and select **Review permissions and consent**.

1. In the dialog, view the permissions required by the app. For more information about the information available in the dialog, see [information available in the consent prompt](/entra/identity-platform/application-consent-experience).

    :::image type="content" source="media/app-consent-entra-dialog.png" alt-text="Screenshot of permissions requested by an app.":::

A complete list of all the possible permissions is documented in the [Microsoft Graph permissions reference](/graph/permissions-reference).

## Resource-specific consent permissions

Resources in Teams can be a team, a chat, or a user. Use of these permissions let apps access the information of only a specific resource. Using RSC permissions, an app doesn't have to request access to org-wide information and can limit the scope of its access. These RSC permissions are defined in the app's manifest file. Only those users who have access to the resources, can consent for these permissions. Developers define these permissions in the app itself, in the app manifest file.

RSC permissions let users give consent to apps for scope-specific information. Such consent lets apps access and modify only a team's or a chat's information. Such an app can't access the information of a chat or a team in which it isn't added. Examples of RSC permissions include the ability to create and delete channels, get the settings for a team, and create and remove channel tabs.

RSC permissions limit the scope of the app permissions to a specific resource as opposed to org-wide Graph permissions that can let apps access org-wide information. The resources on which RSC permissions can apply are chats and meetings, teams and channels, and users.

RSC permissions are defined in the app manifest and not in Microsoft Entra ID. You grant consent to RSC permissions when you add the app to a team. To learn more, see [Resource-specific consent (RSC)](/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

To view RSC permissions for an app, follow these steps:

1. Access Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.
1. Search for the app you want, select the app name to go to the app details page, and then select the **Permissions** tab.
1. Under **Resource-specific consent (RSC) permissions**, review the RSC permissions requested by the app.

## What can apps do in Teams

When developers create Teams apps, they use some capabilities defined in the development framework. These capabilities are high-level functionalities that apps can have. For example, an app can contain a bot that converses with the user. When an app uses a capability, it is automatically granted some basic privileges. For example, if the app containing a bot is allowed for a user, then the bot can send and receive messages. These privileges exist in apps based on what functionality the app developer added to an app and aren't permissions that require consent to be effective. Developers don't explicitly define these permissions but these permissions are implicitly added when developers build any app functionality.

As an admin, you manage Teams apps and not their capabilities. [Teams apps have capabilities](apps-in-teams.md#understand-app-capabilities) that allow apps to accomplish their core use case and accomplish some tasks. The [capabilities are provided by SDKs](/microsoftteams/platform/concepts/build-and-test/tool-sdk-overview) and the consent is implied when the app is installed. The tasks that apps can accomplish that are associated with capabilities are different from the permissions that require consent by an admin. You as an admin must consider what an app can do and how it interacts with users based on the following capabilities.

* [Bots and Messaging extensions](#bots-and-messaging-extensions)
* [Tabs](#tabs)
* [Connectors](#connectors)
* [Outgoing webhooks](#outgoing-webhooks)

> [!NOTE]
> Apps may not use all the below capabilities, unless the app is a complex app catering to multiple use cases. The tasks that app can do depend on the capabilities used in it by the app developer.

### Bots and messaging extensions

Consider the following types of user interaction, required permissions, and data access by bots and messaging extensions:

* A bot can receive messages from users and reply to them. Bots only receive messages in chats where users explicitly mention a bot by its name. This data leaves the corporate network.

* After a user sends a message to a bot, the bot can send the user direct or proactive messages at any time.

* Some bots only send messages. They're called notification-only bots and the bot doesn't offer a conversational experience.

* A bot added to teams can get a list of names and IDs of the channels in a team.

* When using it in a channel, in a personal chat, or a group chat, the app's bot can access basic identity information of team members. The information includes first name, last name, user principal name (UPN), and email address.

* It's possible for an app's bot to send direct or proactive messages to team members even if they haven't interacted with the bot.

* Depending on settings and functioning of an app that is a bot, it can send and receive files in personal chat only. It isn't supported for group chats or channels.

* Bots only have access to teams to which the bots are added or to users who add the bots app.

* When a user converses with a bot, if the bot stores the user's ID, it can send the user direct messages at any time.

* If necessary, a user or an admin can block a bot. Microsoft can also remove a bot from the store. [App verification and validation checks](overview-of-app-validation.md) ensures high quality apps are available in Teams store and that bots don't spam their users.

* A bot can retrieve and can store basic identity information for the team members the app is added to, or for individual users in personal or group chats. To get further information about these users, the bot must require them to sign in to Microsoft Entra ID.

* Bots can retrieve and can store the list of channels in a team. This data leaves the corporate network.

* By default, bots don't have the ability to act on behalf of the user, but bots can ask users to sign in; as soon as the user signs in, the bot has an access token with which it can do other tasks. The tasks depend on the bot and where the user signs in: a bot is a Microsoft Entra app registered at `https://apps.dev.microsoft.com/` and can have its own set of permissions.

* When a file is sent to a bot, the file leaves the corporate network. Sending and receiving files requires user approval for each file.

* Bots are informed whenever users are added to or deleted from a team.

* Bots don't see users' IP addresses or other referrer information. All information comes from Microsoft. (There's one exception: if a bot implements its own sign-in experience, the sign-in UI sees users' IP addresses and referrer information.)

* Messaging extensions, on the other hand, can see users' IP addresses and referrer information.

> [!NOTE]
>
> * If a bot has its own sign-in, there's a different consent experience the first time the user signs in.
> * Users can search apps with the `botId` that was available in the app. While users can view the app name but they can't interact with such bots.

### Tabs

A tab is a website running inside Teams. It can be as a tab in a meeting, a chat, or a channel.

Consider the following types of user interaction or data access for Tabs:

* Users opening a tab in a browser or in Teams is exactly the same. The website itself can't have access to any organization's information on its own.

* A tab also gets the context in which it's running, including the sign-in name and UPN of the current user, the Microsoft Entra Object ID for the current user, the ID of the Microsoft 365 group in which it resides (if it's a team), the tenant ID, and the current locale of the user. However, to map these IDs to a user's information, the tab would have to make the user sign in to Microsoft Entra ID.

### Connectors

A connector posts messages to a channel when events in an external system occur. The required permission for Connectors is to be able to post messages in channel. An optional permission for Connectors is the permission to reply to a message. Some connectors support actionable messages, which allow users to post targeted replies to the connector message. For example, by adding a response to a GitHub issue or adding a date to a Trello card. Consider the following types of user interaction, required permissions, and data access by Connectors:

* The system that posts connector messages doesn't know who it's posting to or who receives the messages. No information about the recipient is disclosed. Microsoft is the actual recipient and not the organization. Microsoft does the actual posting to the channel.

* No data leaves the corporate network when Connectors post messages in a channel.

* Connectors that support actionable messages also don't see IP address and referrer information; this information is sent to Microsoft and then routed to HTTP endpoints that were previously registered with Microsoft in the Connectors portal.

* Each time a Connector is configured for a channel, a unique URL for that connector instance is created. If that connector instance is deleted, the URL can no longer be used.

* Connector messages can't contain file attachments.

* The Connector instance URL should be treated as secret or confidential. Anyone who has the URL can post to it. If necessary, team owners can delete the connector instance.

* If necessary, an administrator can prevent new Connector instances from being created and Microsoft can block all usage of a Connector app.

### Outgoing webhooks

Team owners or team members create Outgoing webhooks. Outgoing webhooks can receive messages from users and reply to them. Consider the following types of user interaction, required permissions, and data access by Outgoing webhooks:

* Outgoing webhooks are similar to bots but have fewer privileges. They must be explicitly mentioned, just like bots.

* When an outgoing webhook is registered, a secret is generated, which allows the outgoing webhook to verify that the sender is Microsoft Teams as opposed to a malicious attacker. This secret should remain a secret; anyone who has access to it can impersonate Microsoft Teams. If the secret is compromised, delete and re-create the outgoing webhook to generate a new secret.

* Although it's possible to create an outgoing webhook that doesn't validate the secret, we recommend against it.

* Other than receiving and replying to messages, outgoing webhooks can't do much: they can't proactively send messages, they can't send or receive files, they can't do anything else that bots can do except receive and reply to messages.

## Related articles

* [Grant and manage consent to Teams app permissions](manage-consent-app-permissions.md).
* [Microsoft Graph permissions reference including RSC permissions](/graph/permissions-reference).
