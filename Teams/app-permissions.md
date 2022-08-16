---
title: Microsoft Teams apps permissions and considerations
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection: 
  - M365-voice
  - M365-collaboration
search.appverid: MET150
ms.reviewer: rowille
description: Admin can learn what data and permissions Microsoft Teams apps are requesting from their organization.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---


# Microsoft Teams apps permissions and considerations

Microsoft Teams apps are a way to aggregate one or more capabilities into apps that can be installed, upgraded, and uninstalled. Capabilities of apps include:

* Bots
* Messaging extensions
* Tabs
* Connectors

As an admin, you only manage apps. However, the article focuses on permissions and considerations at the capability level as capabilities in an app affect the required permissions and risk profiles of the app. For usage, apps are consented to by users and managed by IT professionals from a policy perspective.

The permissions listed below in capital letters, for example `RECEIVE_MESSAGE` and `REPLYTO_MESSAGE` are only for illustration and explanation purpose. These strings or permissions don't appear anywhere in the [Microsoft Teams developer documentation](/microsoftteams/platform/overview) or the [permissions for Microsoft Graph](/graph/permissions-reference).

## Global app permissions and considerations

### Required permissions

None

### Optional permissions

None

### Considerations

* An app must disclose what data it uses and what the data is used for in its terms of use and privacy policy links.

* [Resource-specific consent](resource-specific-consent.md) provides a set of permissions that apps can request, which appears on the installation screen of the app. To learn more about resource-specific consent permissions, see [Graph permissions reference](/graph/permissions-reference#teams-resource-specific-consent-permissions).

* Apps may also need permissions other than resource-specific consent permissions. After an app is installed, the app may request Graph permissions through a consent prompt. To learn more, see [Understanding Azure AD application consent experiences](/azure/active-directory/develop/application-consent-experience). You can configure API permissions and consent in the Azure portal. To learn more, see [Azure Active Directory consent framework](/azure/active-directory/develop/consent-framework).

## Bots and messaging extensions

### Required permissions

* RECEIVE_MESSAGE, REPLYTO_MESSAGE: The bot can receive messages from users and reply to them.<sup>1</sup>

* POST_MESSAGE_USER: After a user has sent a message to a bot, the bot can send the user direct messages (also called *proactive messages* at any time.

* GET_CHANNEL_LIST: Bots added to teams can get a list of names and IDs of the channels in a team.

### Optional permissions

* IDENTITY: When it's used in a channel, the app's bots can access basic identity information of team members (first name, last name, user principal name [UPN], email address). When it's used in a personal or group chat, the bot can access the same information for those users.

* POST_MESSAGE_TEAM: Allows an app's bots to send direct (proactive) messages to the team member at any time, even if the user has never interacted with the bot.

* The following aren't explicit permissions, but are implied by RECEIVE_MESSAGE and REPLYTO_MESSAGE and the scopes into which the bots can be used, declared in the manifest:

  * RECEIVE_MESSAGE_PERSONAL, REPLYTO_MESSAGE_PERSONAL
  * RECEIVE_MESSAGE_GROUPCHAT, REPLYTO_MESSAGE_GROUPCHAT
  * RECEIVE_MESSAGE_TEAM, REPLYTO_MESSAGE_TEAM

* The following aren't explicit permissions, but are implied by RECEIVE_MESSAGE and REPLYTO_MESSAGE and the scopes into which the bots can be used, declared in the manifest:

  * RECEIVE_MESSAGE_PERSONAL, REPLYTO_MESSAGE_PERSONAL
  * RECEIVE_MESSAGE_GROUPCHAT, REPLYTO_MESSAGE_GROUPCHAT
  * RECEIVE_MESSAGE_TEAM, REPLYTO_MESSAGE_TEAM

* SEND_FILES, RECEIVE_FILES:<sup>2</sup> Controls whether a bot can send and receive files in personal chat (not yet supported for group chat or channels).

### Considerations

* Bots only have access to teams to which they've been added or to users who have installed them.

* Bots only receive messages in which they're explicitly mentioned by users. This data leaves the corporate network.

* Bots can only reply to conversations in which they're mentioned.

* When a user converses with a bot, if the bot stores the user's ID, it can send the user direct messages at any time.

* Theoretically it's possible for bot messages to contain links to phishing or malware sites. However, bots can be blocked by the user, the tenant admin, or globally by Microsoft. [App verification and validation checks](overview-of-app-validation.md) ensures that any spurious apps are not available in Teams store.

* A bot can retrieve (and might store) basic identity information for the team members the app has been added to, or for individual users in personal or group chats. To get further information about these users, the bot must require them to sign in to Azure Active Directory (Azure AD).

* Bots can retrieve (and might store) the list of channels in a team; this data leaves the corporate network.

* By default, bots don't have the ability to act on behalf of the user, but bots can ask users to sign in; as soon as the user signs in, the bot will have an access token with which it can do additional things. Exactly what those other things are depends on the bot and where the user signs in: a bot is an Azure AD app registered at https://apps.dev.microsoft.com/ and can have its own set of permissions.

* When a file is sent to a bot, the file leaves the corporate network. Sending and receiving files requires user approval for each file.

* Bots are informed whenever users are added to or deleted from a team.

* Bots don't see users' IP addresses or other referrer information. All information comes from Microsoft. (There's one exception: if a bot implements its own sign-in experience, the sign-in UI will see users' IP addresses and referrer information.)

* Messaging extensions, on the other hand, do see users' IP addresses and referrer information.

* App guidelines (and our AppSource review process) require discretion in posting personal chat messages to users (via the POST_MESSAGE_TEAM permission) for valid purposes. In the event of abuse, users can block the bot, tenant admins can block the app, and Microsoft can block bots centrally if necessary.

<sup>1</sup> Some bots only send messages (POST_MESSAGE_USER). They're called "notification-only" bots, but the term doesn't refer to what a bot is allowed or not allowed to do, it means that the bot doesn't want to expose a conversational experience. Teams uses this field to disable functionality in the UI that would ordinarily be enabled; the bot isn't restricted in what it's allowed to do compared to bots that expose a conversational experience.

<sup>2</sup> Governed by the supportsFiles Boolean property on the bot object in the `manifest.json` file for the app.

> [!NOTE]
> If a bot has its own sign-in, there's a second—different—consent experience the first time the user signs in.
>
>Currently, the Azure AD permissions associated with any of the capabilities inside a Teams app (bot, tab, connector, or messaging extension) are completely separate from the Teams permissions listed here.

## Tabs

A tab is a website running inside Teams.

### Required permissions

SEND_AND_RECEIVE_WEB_DATA

### Optional permissions

None (currently)

### Considerations

* The risk profile for a tab is almost identical to that same website running in a browser tab.

* A tab also gets the context in which it's running, including the sign-in name and UPN of the current user, the Azure AD Object ID for the current user, the ID of the Microsoft 365 Group in which it resides (if it's a team), the tenant ID, and the current locale of the user. However, to map these IDs to a user's information, the tab would have to make the user sign in to Azure AD.

## Connectors

A connector posts messages to a channel when events in an external system occur.

### Required permissions

POST_MESSAGE_CHANNEL

### Optional permissions

REPLYTO_CONNECTOR_MESSAGE. Certain connectors support actionable messages, which allow users to post targeted replies to the connector message, for example by adding a response to a GitHub issue or adding a date to a Trello card.

### Considerations

* The system that posts connector messages doesn't know who it's posting to or who receives the messages: no information about the recipient is disclosed. (Microsoft is the actual recipient, not the tenant; Microsoft does the actual post to the channel.)

* No data leaves the corporate network when connector messages are posted to a channel.

* Connectors that support actionable messages (REPLYTO_CONNECTOR_MESSAGE permission) also don't see IP address and referrer information; this information is sent to Microsoft and then routed to HTTP endpoints that were previously registered with Microsoft in the Connectors portal.

* Each time a connector is configured for a channel, a unique URL for that connector instance is created. If that connector instance is deleted, the URL can no longer be used.

* Connector messages can't contain file attachments.

* The connector instance URL should be treated as secret/confidential: anyone who has that URL can post to it, like an email address. Therefore, there's some risk of spam or links to phishing or malware sites. If that happens, then team owners can delete the connector instance.

* If the service that sends connector messages were to become compromised and start sending spam/phishing/malware links, a tenant administrator can prevent new connector instances from being created and Microsoft can block them centrally.

> [!NOTE]
> It's not currently possible to know which Connectors support actionable messages (REPLYTO_CONNECTOR_MESSAGE permission).

## Outgoing webhooks

_Outgoing webhooks_ are created by team owners or team members. They aren't capabilities of Teams apps; this information is included for completeness.

### Required permissions

RECEIVE_MESSAGE, REPLYTO_MESSAGE. Can receive messages from users and reply to them.

### Optional permissions

None

### Considerations

* Outgoing webhooks are similar to bots but have fewer privileges. They must be explicitly mentioned, just like bots.

* When an outgoing webhook is registered, a secret is generated, which allows the outgoing webhook to verify that the sender is Microsoft Teams as opposed to a malicious attacker. This secret should remain a secret; anyone who has access to it can impersonate Microsoft Teams. If the secret is compromised, delete and re-create the outgoing webhook to generate a new secret.

* Although it's possible to create an outgoing webhook that doesn't validate the secret, we recommend against it.

* Other than receiving and replying to messages, outgoing webhooks can't do much: they can't proactively send messages, they can't send or receive files, they can't do anything else that bots can do except receive and reply to messages.
