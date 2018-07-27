---
title: Microsoft Teams Apps: Permissions and Risk Profiles
author: 
ms.author: 
manager: 
ms.date: 07/27/2018
ms.topic: article
ms.service: msteams
ms.reviewer: 
description: Learn what data and permissions apps are requesting from your company. 
ms.custom:
- NewAdminCenter_Update
appliesto: 
- Microsoft Teams
---


# Microsoft Teams Apps: Permissions and Risk Profiles

Microsoft Teams Apps are a way to aggregate one or more capabilities into an "app package" that can be installed, upgraded, and uninstalled. Here are the possible capabilities:

- Bots
- Tabs
- Messaging Extensions
- Connectors


Apps are what are consented to by users, and what are managed by IT from a policy perspective. However, for the most part it's the capabilities that define the permissions and risk profile: an app's permissions and its risk profile is the union of its capabilities' permissions and risk profile. For example, bots send and receive messages from users, and they are located outside the compliance boundary (except for enterprise line-of-business bots). Any app with a bot requires those permissions and has that risk profile, at a minimum. Therefore, this document will focus on the permissions and risk profile at the capability level.

The table below should only be used as a reference guide to understand which permissions the apps you are investigating are requesting. You will still need to do research on the app\service itself to deem whether or not you want to allow access to them within your organization. 

The permissions listed below in capital letters, for example RECEIVE_MESSAGE and REPLYTO_MESSAGE, do not appear anywhere in the [Microsoft Teams developer documentation](https://aka.ms/teamsdevdocs) or the [permissions for Microsoft Graph](https://docs.microsoft.com/en-us/microsoftteams/platform/overview). They are simply a descriptive shorthand.

## App Global

<table>
  <tr>
    <td>Required Permissions</td>
    <td>Optional Permissions</td>
    <td>Risk Profile</td>
    <td>Notes</td>
  </tr>
  <tr>
    <td valign="top"><ul><li>none</li></ul></td>
    <td valign="top"><ul><li>none</li></ul></td>
    <td valign="top"><ul><li>TOU and Privacy Policy. What data an app uses and what it's used for must be disclosed in its terms of service and privacy policy links.</li></ul></td>
    <td valign="top"></td>
  </tr>
</table>

## Bots and Message Extension

<table>
  <tr>
    <td>Required Permissions</td>
    <td>Optional Permissions</td>
    <td>Risk Profile</td>
    <td>Notes</td>
  </tr>
   <tr>
    <td valign="top"><ul><li>	RECEIVE_MESSAGE, REPLYTO_MESSAGE. The bot can receive messages from users and reply to them.</li><li>POST_MESSAGE_USER. Once a user has sent a message to a bot, the bot can send the user direct messages at any time (aka "proactive messages").</li><li>GET_CHANNEL_LIST. Bots added to teams can get a list of names and IDs of the channels in a team. </li></ul></td>
    <td valign="top"><ul><li>IDENTITY. The app's bot(s) can access basic identity information of team members (first name, last name, UPN, email address) when being used in a channel, or the same information for specific users when being used in a personal or group chat with those users.</li><li> POST_MESSAGE_TEAM. Allows an app's bot(s) to send direct (proactive) messages to any team member at any time, even if the user has never talked to the bot before.</li></ul> The following are not explicit permissions but are implied by RECEIVE_MESSAGE and REPLYTO_MESSAGE and the scopes into which the bots can be used, declared in the manifest: <ul><li>RECEIVE_MESSAGE_PERSONAL, REPLYTO_MESSAGE_PERSONAL</li><li>RECEIVE_MESSAGE_GROUPCHAT, REPLYTO_MESSAGE_GROUPCHAT </li><li>RECEIVE_MESSAGE_TEAM, REPLYTO_MESSAGE_TEAM</li></ul>  <ul><li>SEND_FILES, RECEIVE_FILES.  Controls whether a bot can send and receive files in personal chat (not yet supported for group chat or channels).</li></ul></td>
    <td valign="top"><ul><li>Bots only have access to teams to which they have been added, or to users who have installed them.</li><li>Bots only receive messages in which they are explicitly mentioned by users. This data leaves the corporate network.</li><li>	Bots can only reply to conversations in which they are mentioned.</li><li> Once a user has conversed with a bot, if the bot stores that user's ID, it can send that user direct messages at any time. </li><li>It is theoretically possible for bot messages to contain links to phishing or malware sites, but bots can be blocked by the user, the tenant admin, or globally by Microsoft. </li><li>A bot can retrieve (and may store) very basic identity information for the team members the app has been added to and/or individual users in personal/group chat. Further information about these users requires AAD login. </li><li>Bots can retrieve (and may store) the list of channels in a team; this data leaves the corporate network. </li><li>When a file is sent to a bot, the file leaves the corporate network. Sending and receiving files requires user approval for each file. </li><li>By default, bots do not have the ability to act on behalf of the user, but bots can ask users to log in; once logged in, the bot will have an access token with which it can do additional things. Exactly what those "additional things" are depends on the bot and where the user logs in: a bot is an Azure Active Directory app registered at <a href="http://apps.dev.microsoft.com/">http://apps.dev.microsoft.com/</a> and can have its own set of permissions.</li><li>Bots are informed whenever users are added to and deleted from a team.</li><li>Bots do not see users' IP addresses or other referrer information. All information comes from Microsoft. (There is one exception: if a bot implements its own signin experience, the signin UI will see users' IP addresses and referrer information.)</li><li>Messaging extensions, on the other hand, do see users' IP addresses and referrer information.</li><li>App guidelines (and our AppSource review process) require discretion in posting personal chat messages to users (via the POST_MESSAGE_TEAM permission) for valid purposes. In the event of abuse, users can block the bot, tenant admins can block the app, and Microsoft can block bots centrally if necessary.</li></ul></td>
    <td valign="top"><ul><li>If a bot has its own login, there's a second, and different, consent experience the first time the user logs in.</li><li>Currently the AAD permissions associated with any of the capabilities inside a Teams app (e.g. a bot, tab, or messaging extension) are completely separate from the Teams permissions listed here.</li></ul></td>
  </tr>
</table>

## Tabs

<table>
  <tr>
    <td>Required Permissions</td>
    <td>Optional Permissions</td>
    <td>Risk Profile</td>
    <td>Notes</td>
  </tr>
  <tr>
    <td valign="top"><ul><li>SEND_AND_RECEIVE_WEB_DATA. A tab is a website running inside Teams.</li></ul></td>
    <td valign="top"><ul><li>Device permissions (see above).</li></ul></td>
    <td valign="top"><ul><li>The risk profile for a tab is almost identical to that same website running in a browser tab. </li><li>A tab also gets the context in which it's running, including the login name and User Principal Name (UPN) of the current user, the Azure AD Object ID for the current user, the ID of the Office 365 Group (team) in which it resides, the tenant ID, and the current locale of the user. In order to map these ID to user/customer information however, the tab would have to make the user login to Azure AD.</li></ul></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td valign="top"><ul><li>Connectors</li></ul></td>
    <td valign="top"><ul><li>POST_MESSAGE_CHANNEL. A connector posts messages to a channel when events in an external system occur.</li></ul></td>
    <td valign="top"><ul><li>REPLYTO_CONNECTOR_MESSAGE. Certain connectors support "Actionable Messages" which allow users to post targeted replies to the connector message, e.g. by adding a response to a GitHub issue or adding a date to a Trello card.</li></ul></td>
    <td valign="top"><ul><li>The system posting connector messages does not know who it's posting to or who receives it: no information about the recipient is disclosed. (Microsoft is the actual recipient, not the tenant; Microsoft does the actual post to the channel.)</li><li>No data leaves the corporate network when connector messages are posted to a channel.</li><li>Connectors which support "actionable messages" / REPLYTO_CONNECTOR_MESSAGE also do not see IP address and referrer information; this information is sent to Microsoft and then routed to HTTP endpoints previously with registered with Microsoft in the Connectors portal.</li><li>Each time a connector is configured for a channel, a unique URL is created, and if that "connector instance" is deleted, the URL can no longer be used.</li><li>Connector messages cannot contain file attachments.</li><li>The "connector instance" URL should be treated as secret/confidential: anyone who has that URL can post to it, like an email address. As such, there is some risk of spam or links to phishing/malware sites. If that were to happen, team owners can delete the connector instance.</li><li>If the service sending connector messages was to become compromised and start sending spam/phishing/malware links, a tenant administrator can prevent new connector instances from being created and Microsoft can block them centrally.</li></ul></td>
    <td valign="top"><ul><li>It is not currently possible to know which connectors support "actionable messages" / REPLYTO_CONNECTOR_MESSAGE.</li></ul></td>
  </tr>
</table>

## Outgoing webhooks

<table>
  <tr>
    <td>Required Permissions</td>
    <td>Optional Permissions</td>
    <td>Risk Profile</td>
    <td>Notes</td>
  </tr>
    <tr>
    <td valign="top"><ul><li>RECEIVE_MESSAGE, REPLYTO_MESSAGE. Can receive messages from users and reply to them.</li></ul></td>
    <td valign="top"><ul><li>None.</li></ul></td>
    <td valign="top"><ul><li>Outgoing webhooks are similar to bots but have fewer privileges. They must be explicitly mentioned, just like bots.</li><li>When an outgoing webhook is registered, a secret is generated which allows the outgoing webhook to verify that the sender is Microsoft Teams as opposed to a malicious attacker. This secret should remain a secret; anyone who has access to it can impersonate Microsoft Teams. If the secret is compromised, the outgoing webhook can be deleted and recreated; a new secret will be generated.</li><li>While it is possible for developers to create an outgoing webhook that does not validate the secret, this is not recommended.</li><li>Other than receiving and replying to messages, outgoing webhooks can't do much: they can't proactively send messages, they can't send or receive files, or anything else that bots can do except for receive and reply to messages.</li></ul></td>
    <td valign="top"><ul><li>Included here for completeness: outgoing webhooks are created on the fly by team owners or team members if sideloading is enabled for a tenant. They aren't capabilities of Teams apps.</li></ul></td>
  </tr>
</table>