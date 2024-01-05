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
ms.date: 01/08/2024
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

Depending on their functionality, Teams apps may or may not access your user's or organization's information.

* Some apps that don't seek access to internal data, don't require admin approval. Users can use such apps without admin approval or consent as these apps can't get any internal data.
* Apps that require permissions on your organization's information can't be used unless an admin permits it. Admins can grant their consent to the permissions required by the app in Teams admin center. You must do your diligence to evaluate apps based on the access an app needs on your organization's information and the reason an app needs it.

To access the information, an app or its user needs the following:

* Access to the org information.
* App developer adding permissions in the app to fetch the org info.
* Consent from user or admin to the app permissions.

This article describes the types of permissions that can be added to an app and how admins can built a better understanding of these permissions.

Teams app permissions can be of the following 3 types:

* Microsoft Entra ID permissions
* Resource-specific permissions
* Basic capabilities

<!---
IT admins grant consent to apps after they validate the compliance, security, and data handling information of an app and also understand the permissions requested by the app and how are those permissions relevant to the app's use cases. IT admins create a balance between their user's need for productivity and their organizations needs for safety and security. To do so, admins must understand the potential of permissions, how Teams apps use these, and how they can approve or reject the apps that seek a set of such permissions.
--->

## How apps access organization's information

An application can access organization's information in the following two ways:

* **Delegated access**: An application accesses the resource on behalf of the user. This access requires delegated permissions. The application can access only the information that the user can access themselves.
* **App-only access**: An application acts on its own with no user signed in, when it's undesirable to have a specific user signed in or when the data required can't be scoped to a single user. This access required applications permissions. An application if granted consent is able to access data that the permission is associated with.

## Where are app permissions defined

In addition, the permissions are defined in the following two places:

* Graph permissions for org-wide resources are defined in Microsoft Entra ID. Permissions that are needed for an app to work are selected in Microsoft Entra ID by the app developers. As an admin you must consent to these permissions otherwise the app can't be used in your tenant.
* RSC permissions to access local resources within Teams such as information in a group or a team are defined in the app manifest file by the developers. Only those users who have access to the resources, can consent for these permissions.
* Basic capabilities are [asd](asd).

## Summary of types and sources of app permission and consent info

For each app, these permissions are listed in the app details page in the admin center.

| App permission type | Access context | Declaration source | When is consent required? | Who can consent? | Remarks |
|---------------------|----------------|-------------|--------------------------|-----------------|-----|
| Microsoft Entra ID for Graph and legacy endpoint access | Delegated | Microsoft Entra ID  | App sign-in  | Global Admin, Cloud Admin, and Application Admin | See [Microsoft Graph permissions required by Teams apps](#graph-permissions-required-by-teams-apps-to-access-your-organizations-information). |
| Microsoft Entra ID for Graph and legacy endpoint access | Application | Microsoft Entra ID  |  App sign-in  |  Global Admin, Cloud Admin, and Application Admin | See [Microsoft Graph permissions required by Teams apps](#graph-permissions-required-by-teams-apps-to-access-your-organizations-information). |
| RSC for information of teams, chats, and users | Delegated | App manifest file | Adding app to a team, chat, meetings | Resource owner. | See [RSC permissions reference](/graph/permissions-reference#teams-resource-specific-consent-permissions). |
| RSC for information of teams, chats, and users | Application | App manifest file |  Adding app to a team, chat, meetings  | Resource owner | See [RSC permissions reference](/graph/permissions-reference#teams-resource-specific-consent-permissions). |
| Other permissions and data access | Delegated via SDKs | Manifest properties define it | Add app in a client | Consent is implied at install. | Available in the `Permissions` tab in app details page of each app. More details are [here](#what-can-apps-do-in-teams). |


## Teams apps and permissions



An application can access an organization's information in the following ways depending on the permissions used by the developer. Understand it to know the different ways in which you can provide consent or enable users to consent for Teams apps in your org.

|                                                   | Delegated permissions                                                                                      | Application permissions                                       |
|---------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| How can apps access information                       | On behalf of a signed-in user.                                                                             | On their own, using their own identity.                       |
| What information is accessed                      | Permissions that app is granted consent to and the information that signed-in user has access to.                     | Any info that a consented permission is associated with       |
| What roles can consent                            | Admins or users or group owners depending on Azure AD configuration                                        | Only admins                                                   |
| Can users consent                                 | Users can consent depending on Azure AD configuration                                                      | Only admins can consent                                       |
| Can admins let users consent for some permissions | Admins can classify some or all Delegated permissions as low-risk to let users consent to these in any app | Admins can't classify any Application permissions as low-risk |

Teams app permissions are defined in the following two places:

* **Azure Active Directory**: Graph permissions lets an app access org-wide resources. Permissions that are needed for an app to work are added in Azure AD by the app developers. As an admin, you must consent to these permissions otherwise the app can't be used in your tenant. Admins can define if users can consent to these permissions or not.
* **Teams app manifest**: RSC permissions are defined in the app manifest file by the app developers. RSC permissions let an app access local resources within Teams such as information in a group or a team. These allow only for Application access and not for Delegated access. Only those users who have access to the resources, can consent for these permissions. Admin consent at org-level is not required though admins control how users consent to these permissions or can block users from consenting.

For each app, these permissions are listed in the app details page in the admin center.

| Type of permissions                                                                                                                           | Access context                             | Source of declaration | When is consent required             | Who can consent                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------|-----------------------|--------------------------------------|-----------------------------------------------------------------------------------|
| [Microsoft Entra ID for Graph and legacy endpoint access](#graph-permissions-required-by-teams-apps-to-access-your-organizations-information) | Delegated                                  | Microsoft Entra ID    | App sign-in                          | Users can partly consent. High-level Delegated permissions require admin consent. |
| Microsoft Entra ID for Graph and legacy endpoint access                                                                                       | Application                                | Microsoft Entra ID    | App sign-in                          | No (Only Global Admin can consent)                                                |
| [RSC for information of teams, chats, and users](#asdf)                                                                                                | Delegated                                  | App manifest file     | Adding app to a team, chat, meetings | User                                                                              |
| RSC for information of teams, chats, and users                                                                                                | Application                                | App manifest file     | Adding app to a team, chat, meetings | Resource owner                                                                    |
| [Interactions with user and data access](#what-can-apps-do-in-teams)                                                                        | Inherent to Teams apps and provided by SDK | Manifest properties   | Add app in a client                  | User (consent is implied at install)                                              |

:::image type="content" source="media/app-permissions.png" alt-text="Screenshot showing the page in admin center that list and requests permissions for an app and also allows admins to grant consent for such permissions for all org-users.":::

   * **A**: [Interactions with user and data access](#what-can-apps-do-in-teams)
   * **B**: [Microsoft Entra ID for Graph and legacy endpoint access](#graph-permissions-required-by-teams-apps-to-access-your-organizations-information)
   * **C**: [RSC for information of teams, chats, and users](#asdf)

<!--- Repurpose some info and discard this table.

| Type of permission for an app | Why is it required | Where to find details | Remarks |
|-------------------------------|----------------------------------|----------------------------|---------|
| **1** Not permissions but capabilities of an app. Actions that an app can perform and basic information that it can access. | For an app to work, it interacts with users, messages users, or it read basic user profile by virtue of being added to Teams client. | Available in the `Permissions` tab in app details page of each app. This information is also listed in the Teams store when a user installs an app. More details are [here](#what-can-apps-do-in-teams). | Required for app to work. Exists by virtue of app being installed. Only basic and not sensitive information is ever accessed by app via this method. |
| **2** Non-RSC Graph permissions | For some features to work, an app needs to access the organization's information in the tenant. | The information that is accessed is displayed in the `Permissions` tab in the app details page of each app. See [Microsoft Graph permissions required by Teams apps](#graph-permissions-required-by-teams-apps-to-access-your-organizations-information) | Controlled via API permissions and consent using [Azure Active Directory consent framework](/azure/active-directory/develop/consent-framework) |
| **3** Resource specific permissions | For some features to work, an app can need access to and information contained within a Teams resources such as meetings, chat, or teams and channels in which the app is added. | Information is displayed in Permissions tab in app details page of each app. See [RSC permissions reference](/graph/permissions-reference#teams-resource-specific-consent-permissions) for a list of all possible RSC permissions. | NA |

--->

## Graph permissions required by Teams apps to access your organization's information

Microsoft Graph is used to allow app developers access to the requisite Microsoft cloud information but always with the appropriate consent. App developers choose from a wide variety of Graph APIs to create their apps and fetch the relevant org information to make the app functionality work. However, the permissions for an app to fetch such information must be consented to for the APIs to access an org's info.

In Teams admin center, you can view Graph permission that an app requests if deployed and you can know what organization's information can an app access, if you grant consent to it.

1. Access Teams admin center and open the **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page.

1. Search for the required app and select its name to open the app details page.

1. In the app details page, in the **Permissions** tab, notice the permissions required by the app.

A complete list of all the possible permissions is available at [Microsoft Graph permissions reference](/graph/permissions-reference).

## Resource-specific consent permissions of an app

RSC permissions help users to give consent to app for scope-specific information and avoid giving it to information of the entire organization. 
Such consent lets apps access and modify a team's or a chat's information only. Such an app can't access the information of a chat or a team in which it is not added. Examples of RSC permissions include the ability to create and delete channels, get the settings for a team, and create and remove channel tabs.

RSC permissions limit the scope of the app permissions to a specific resource as opposed to org-wide Graph permissions that can let apps access org-wide information. The resources on which RSC permissions can apply are chats and meetings, teams and channels, and users.

RSC permissions are defined in the app manifest and not in Azure AD. You grant consent to RSC permissions when you add the app to a team. To learn more, see [Resource-specific consent (RSC)](/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

To view RSC permissions for an app, follow these steps:

1. Access Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.
1. Search for the app you want, select the app name to go to the app details page, and then select the **Permissions** tab.
1. Under **Resource-specific consent (RSC) permissions**, review the RSC permissions requested by the app.

    :::image type="content" source="media/app-perm-admin-center-rsc.png" alt-text="Screenshot showing an example of how to view RSC permissions of an app.":::

<!--- 
See if there's a need to reuse the AAD screenshot from the manage consent article here.
--->

## Privacy and data access considerations

In the terms of use and privacy policy of any app, the app developer discloses what data their app uses and how it's handled. For more information, see [understand where to find support information for apps](manage-apps.md#support-information-for-apps).

## What can apps do in Teams

As an admin, you manage Teams apps and not their capabilities. [Teams apps have capabilities](apps-in-teams.md#understand-app-capabilities) that allow apps to accomplish their core use case and accomplish some tasks. The [capabilities are provided by SDKs](/microsoftteams/platform/concepts/build-and-test/tool-sdk-overview) and don't require any consent. The tasks that apps can accomplish that are associated with capabilities are different from the permissions that require consent by an admin. You as an admin must consider what an app can do and how it interacts with users based on the following capabilities.

* [Bots and Messaging extensions](#bots-and-messaging-extensions)
* [Tabs](#tabs)
* [Connectors](#connectors)
* [Outgoing webhooks](#outgoing-webhooks)

> [!NOTE]
> Apps may not use all the below capabilities, unless the app is a complex app catering to multiple use cases. The tasks that app can do depend on the capabilities used in it by the app developer.

### Bots and Messaging Extensions

Consider the following types of user interaction, required permissions, and data access by bots and messaging extensions:

* A bot can receive messages from users and reply to them. Bots only receive messages in chats where users explicitly mention a bot by its name. This data leaves the corporate network.

* After a user has sent a message to a bot, the bot can send the user direct or proactive messages at any time.

* Some bots only send messages. They're called notification-only bots and the bot doesn't offer a conversational experience.

* A bot added to teams can get a list of names and IDs of the channels in a team.

* When it's used in a channel, in a personal chat, or a group chat, the app's bot can access basic identity information of team members (first name, last name, user principal name [UPN], and email address).

* It's possible for an app's bot to send direct or proactive messages to team members even if they haven't interacted with the bot.

* Depending on settings and functioning of an app that is a bot, it can send and receive files in personal chat only. It isn't supported for group chats or channels.

* Bots only have access to teams to which they've been added or to users who have installed them.

* When a user converses with a bot, if the bot stores the user's ID, it can send the user direct messages at any time.

* If necessary, a user or an admin can block a bot. Microsoft can also remove a bot from the store. [App verification and validation checks](overview-of-app-validation.md) ensures high quality apps are available in Teams store and that bots don't spam their users.

* A bot can retrieve and may store basic identity information for the team members the app is added to, or for individual users in personal or group chats. To get further information about these users, the bot must require them to sign in to Microsoft Entra ID.

* Bots can retrieve and may store the list of channels in a team. This data leaves the corporate network.

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

* The system that posts connector messages doesn't know who it's posting to or who receives the messages. No information about the recipient is disclosed. (Microsoft is the actual recipient, not the tenant; Microsoft does the actual post to the channel.)

* No data leaves the corporate network when Connectors post messages in a channel.

* Connectors that support actionable messages also don't see IP address and referrer information; this information is sent to Microsoft and then routed to HTTP endpoints that were previously registered with Microsoft in the Connectors portal.

* Each time a Connector is configured for a channel, a unique URL for that connector instance is created. If that connector instance is deleted, the URL can no longer be used.

* Connector messages can't contain file attachments.

* The Connector instance URL should be treated as secret or confidential. Anyone who has the URL can post to it. If necessary, team owners can delete the connector instance.

* If necessary, a tenant administrator can prevent new Connector instances from being created and Microsoft can block all usage of a Connector app.

### Outgoing webhooks

Team owners or team members create Outgoing webhooks. Outgoing webhooks can receive messages from users and reply to them. Consider the following types of user interaction, required permissions, and data access by Outgoing webhooks:

* Outgoing webhooks are similar to bots but have fewer privileges. They must be explicitly mentioned, just like bots.

* When an outgoing webhook is registered, a secret is generated, which allows the outgoing webhook to verify that the sender is Microsoft Teams as opposed to a malicious attacker. This secret should remain a secret; anyone who has access to it can impersonate Microsoft Teams. If the secret is compromised, delete and re-create the outgoing webhook to generate a new secret.

* Although it's possible to create an outgoing webhook that doesn't validate the secret, we recommend against it.

* Other than receiving and replying to messages, outgoing webhooks can't do much: they can't proactively send messages, they can't send or receive files, they can't do anything else that bots can do except receive and reply to messages.

## Related articles

* [RSC permissions reference](/graph/permissions-reference#teams-resource-specific-consent-permissions).
