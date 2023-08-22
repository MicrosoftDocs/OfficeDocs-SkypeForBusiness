---
title: Microsoft Teams apps permissions and considerations
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.collection: 
  - M365-voice
  - M365-collaboration
  - Tier1
search.appverid: MET150
ms.reviewer: tolgaki
ms.date: 08/22/2023
description: Learn what permissions Teams apps request to access data in your organization.
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

Based on its permissions, an app can access some information, perform some tasks, and engage with users. To help you understand what apps can do, a compilation of this information is available in [what can apps do in Teams](#what-can-apps-do-in-teams).

:::image type="content" source="media/app-permissions.png" alt-text="Screenshot that shows the permissions tab of an app and the Microsoft Graph and RSC permissions that may be required by an app.":::

| Type of permission for an app | Why is it required | Where to find details | Remarks |
|-------------------------------|----------------------------------|----------------------------|---------|
| **1** Not permissions but capabilities of an app. Actions that an app can perform and basic information that it can access. | For an app to work, it interacts with users, messages users, or it read basic user profile by virtue of being added to Teams client. | Available in the `Permissions` tab in app details page of each app. This information is also listed in the Teams store when a user installs an app. More details are [here](#what-can-apps-do-in-teams). | Required for app to work. Exists by virtue of app being installed. Only basic and not sensitive information is ever accessed by app via this method. |
| **2** Non-RSC Graph permissions | For some features to work, an app needs to access the organization's information in the tenant. | The information that is accessed is displayed in the `Permissions` tab in the app details page of each app. See [Microsoft Graph permissions required by Teams apps](#graph-permissions-required-by-teams-apps-to-access-your-organizations-information) | Controlled via API permissions and consent using [Azure Active Directory consent framework](/azure/active-directory/develop/consent-framework) |
| **3** Resource specific permissions | For some features to work, an app can need access to and information contained within a Teams resources such as meetings, chat, or teams and channels in which the app is added. | Information is displayed in Permissions tab in app details page of each app. See [RSC permissions reference](/graph/permissions-reference#teams-resource-specific-consent-permissions) for a list of all possible RSC permissions. | NA |

## Privacy and data access considerations

In the terms of use and privacy policy of any app, the app developer discloses what data their app uses and how it is handled. This information is available on app developer's website and you can access the URLs in the app details page in Teams admin center.

:::image type="content" source="/media/app-details-urls.png" alt-text="Screenshot that shows privacy and terms of use URLs in the app details page.":::

Many app developers choose to undergo the Microsoft 365 app compliance program. The program checks and audits an app against controls that are derived from leading industry-standard frameworks. The detailed information about each such app is available on Microsoft website at [Teams Apps Security and Compliance](/microsoft-365-app-certification/teams/teams-apps).

The program demonstrates that strong security and compliance practices are in place to protect customer data. See the details in [app compliance program for security, data handling, and privacy](overview-of-app-certification.md).

## Graph permissions required by Teams apps to access your organization's information

Microsoft Graph is used to allow app developers access to the requisite Microsoft 365 information but always with the appropriate permissions. App developers choose from a wide variety of Graph APIs to create their apps and fetch the relevant org-wide information to make the app functionality work. However, the permissions for an app to fetch such information isn't available by default. IT admins validate the apps, their use cases, and the permissions that apps seek in their organizations. IT admins create a balance between their user's need for productivity and their organizations needs for safety and security. To do so, admins must understand the potential of Graph permissions, how Teams apps use these, and how they can approve or reject the apps that seek a set of such permissions.

In Teams admin center, you can view Graph permission that an app will request if deployed and you can know what organization's information can an app access, if you grant consent to it.

1. Access Teams admin center and open the **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page.

1. Search for the required app and select its name to open the app details page.

1. In the app details page, in the **Permissions** tab, notice the permissions required by the app.

:::image type="content" source="media/app-permissions.png" alt-text="Screenshot showing the page in admin center that list and requests permissions for an app and also allows admins to grant consent for such permissions for all org-users.":::

A complete list of all the possible permissions is available at [Microsoft Graph permissions reference](/graph/permissions-reference).

## What can apps do in Teams

As an admin, you only manage Teams apps. The apps themselves can use one or more capabilities. These capabilities have differences when it comes to app functionality, user engagement, required permissions and risk profiles. Depending on these, you as an admin must consider the access to the following Teams information by the apps.

The Azure AD permissions associated with any of the capabilities inside a Teams app (bot, tab, connector, or messaging extension) are completely separate from the Teams permissions listed here.

* Bots
* Messaging extensions
* Tabs
* Connectors
* Outgoing webhooks

### Bots and messaging extensions

Consider the following types of user interaction, required permissions, and data access by bots and messaging extensions:

* A bot can receive messages from users and reply to them. Bots only receive messages in chats where users explicitly mention a bot by its name. This data leaves the corporate network.

* After a user has sent a message to a bot, the bot can send the user direct or proactive messages at any time.

* Some bots only send messages. They're called notification-only bots and the bot doesn't offer a conversational experience.

* A bot added to teams can get a list of names and IDs of the channels in a team.

* When it's used in a channel, in a personal chat, or a group chat, the app's bot can access basic identity information of team members (first name, last name, user principal name [UPN], and email address).

* It is possible for an app's bot to send direct or proactive messages to team members even if they haven't interacted with the bot.

* Depending on settings and functioning of an app that is a bot, it can send and receive files in personal chat only. It isn't supported for group chats or channels.

* Bots only have access to teams to which they've been added or to users who have installed them.

* When a user converses with a bot, if the bot stores the user's ID, it can send the user direct messages at any time.

* If required, a user or an admin can block a bot. Microsoft can also remove a bot from the store. [App verification and validation checks](overview-of-app-validation.md) ensures high quality apps are available in Teams store.

* A bot can retrieve and may store basic identity information for the team members the app has been added to, or for individual users in personal or group chats. To get further information about these users, the bot must require them to sign in to Azure Active Directory.

* Bots can retrieve and may store the list of channels in a team. This data leaves the corporate network.

* By default, bots don't have the ability to act on behalf of the user, but bots can ask users to sign in; as soon as the user signs in, the bot has an access token with which it can do other tasks. The tasks depend on the bot and where the user signs in: a bot is an Azure AD app registered at `https://apps.dev.microsoft.com/` and can have its own set of permissions.

* When a file is sent to a bot, the file leaves the corporate network. Sending and receiving files requires user approval for each file.

* Bots are informed whenever users are added to or deleted from a team.

* Bots don't see users' IP addresses or other referrer information. All information comes from Microsoft. (There's one exception: if a bot implements its own sign-in experience, the sign-in UI will see users' IP addresses and referrer information.)

* Messaging extensions, on the other hand, do see users' IP addresses and referrer information.

* App guidelines (and our AppSource review process) require discretion in posting personal chat messages to users (via the POST_MESSAGE_TEAM permission) for valid purposes. If necessary, users can block the bot, tenant admins can block the app, and Microsoft can remove the app that works as a bot.

> [!NOTE]
> If a bot has its own sign-in, there's a different consent experience the first time the user signs in.

### Tabs

A tab is a website running inside Teams. It can be as a tab in a meeting, a chat, or a channel.

Consider the following types of user interaction or data access for Tabs:

* Users opening a tab in a browser or in Teams is exactly the same. The website itself can't have access to any organization's information on its own.

* A tab also gets the context in which it's running, including the sign-in name and UPN of the current user, the Azure AD Object ID for the current user, the ID of the Microsoft 365 group in which it resides (if it's a team), the tenant ID, and the current locale of the user. However, to map these IDs to a user's information, the tab would have to make the user sign in to Azure AD.

### Connectors

A connector posts messages to a channel when events in an external system occur. The required permission for Connectors is to be able to post messages in channel. An optional permission for Connectors is the permission to reply to a message. Some connectors support actionable messages, which allow users to post targeted replies to the connector message. For example, by adding a response to a GitHub issue or adding a date to a Trello card. Consider the following types of user interaction, required permissions, and data access by Connectors:

* The system that posts connector messages doesn't know who it's posting to or who receives the messages. No information about the recipient is disclosed. (Microsoft is the actual recipient, not the tenant; Microsoft does the actual post to the channel.)

* No data leaves the corporate network when connector messages are posted to a channel.

* Connectors that support actionable messages also don't see IP address and referrer information; this information is sent to Microsoft and then routed to HTTP endpoints that were previously registered with Microsoft in the Connectors portal.

* Each time a connector is configured for a channel, a unique URL for that connector instance is created. If that connector instance is deleted, the URL can no longer be used.

* Connector messages can't contain file attachments.

* The connector instance URL should be treated as secret or confidential. Anyone who has the URL can post to it. If required, team owners can delete the connector instance.

* If required, a tenant administrator can prevent new connector instances from being created and Microsoft can block all usage of a connector app.

### Outgoing webhooks

Team owners or team members create Outgoing webhooks. Outgoing webhooks can receive messages from users and reply to them. Consider the following types of user interaction, required permissions, and data access by Outgoing webhooks:

* Outgoing webhooks are similar to bots but have fewer privileges. They must be explicitly mentioned, just like bots.

* When an outgoing webhook is registered, a secret is generated, which allows the outgoing webhook to verify that the sender is Microsoft Teams as opposed to a malicious attacker. This secret should remain a secret; anyone who has access to it can impersonate Microsoft Teams. If the secret is compromised, delete and re-create the outgoing webhook to generate a new secret.

* Although it's possible to create an outgoing webhook that doesn't validate the secret, we recommend against it.

* Other than receiving and replying to messages, outgoing webhooks can't do much: they can't proactively send messages, they can't send or receive files, they can't do anything else that bots can do except receive and reply to messages.
