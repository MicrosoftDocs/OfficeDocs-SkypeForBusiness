---
title: Microsoft Teams apps permissions and considerations
author: rmw2890
ms.author: rowille
manager: serdars
ms.date: 10/18/2018
ms.topic: conceptual
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
search.appverid: MET150
ms.reviewer: rowille
description: Learn what data and permissions apps are requesting from your organization.
localization_priority: Normal
appliesto:
- Microsoft Teams
---


# Microsoft Teams apps permissions and considerations

Microsoft Teams apps are a way to aggregate one or more capabilities into an _app package_ that can be installed, upgraded, and uninstalled. The capabilities include:

-   Bots
-   Messaging extensions
-   Tabs
-   Connectors

Apps are consented to by users and managed by IT from a policy perspective. However, for the most part, an app's permissions and risk profile are defined by the permissions and risk profiles of the capabilities it contains. Therefore, this article focuses on permissions and considerations at the capability level.

The permissions listed below in capital letters, for example RECEIVE_MESSAGE and REPLYTO_MESSAGE, don't appear anywhere in the [Microsoft Teams developer documentation](https://aka.ms/teamsdevdocs) or the [permissions for Microsoft Graph](https://developer.microsoft.com/graph/docs/concepts/permissions_reference). They're simply a descriptive shorthand for the purpose of this article.


|    |     |
|-----------|------------|
| ![An icon depicting a decision point](media/audio_conferencing_image7.png) <br/>Decision point|<ul><li>Use the tables below as a guide to understand which permissions the apps you're investigating are requesting.</li></ul> |
| ![An icon depicting the next step](media/audio_conferencing_image9.png)<br/>Next step|<ul><li>Research the app or service itself to decide whether you want to allow access to it within your organization. For example, bots send and receive messages from users, and—except for enterprise line-of-business bots—they're located outside the compliance boundary. Therefore, any app that includes a bot requires those permissions and has that risk profile, at a minimum. </li></ul>|

## Global app permissions and considerations

<table>
  <tr>
    <th width="25%">Required permissions</th>
    <th width="25%">Optional permissions</th>
    <th width="50%">Considerations</th>
  </tr>
  <tr>
    <td valign="top">None</td>
    <td valign="top">None</td>
    <td valign="top">An app must disclose what data it uses and what the data is used for in its terms of use and privacy policy links.</td>
  </tr>
</table>

## Bots and messaging extensions

<table>
 <thead>
  <tr>
    <th width="0.5%"></th>
    <th width="24.5%">Required permissions</th>
    <th width="25%">Optional permissions</th>
    <th width="50%">Considerations</th>
  </tr>
</thead>
<tbody>
   <tr>
    <td valign="top" colspan="2"><ul><li>   RECEIVE_MESSAGE, REPLYTO_MESSAGE. The bot can receive messages from users and reply to them.<sup>1</sup></li><li>POST_MESSAGE_USER. After a user has sent a message to a bot, the bot can send the user direct messages (also called <em>proactive messages</em>) at any time.</li><li>GET_CHANNEL_LIST. Bots added to teams can get a list of names and IDs of the channels in a team.</li></ul></td>
    <td valign="top"><ul><li>IDENTITY. When it&#39;s used in a channel, the app&#39;s bots can access basic identity information of team members (first name, last name, user principal name [UPN], email address); when it&#39;s used in a personal or group chat, the bot can access the same information for those users.</li><li> POST_MESSAGE_TEAM. Allows an app&#39;s bots to send direct (proactive) messages to any team member at any time, even if the user has never talked to the bot before.</li><li>The following are not explicit permissions, but are implied by RECEIVE_MESSAGE and REPLYTO_MESSAGE and the scopes into which the bots can be used, declared in the manifest: <ul><li>RECEIVE_MESSAGE_PERSONAL, REPLYTO_MESSAGE_PERSONAL</li><li>RECEIVE_MESSAGE_GROUPCHAT, REPLYTO_MESSAGE_GROUPCHAT</li><li>RECEIVE_MESSAGE_TEAM, REPLYTO_MESSAGE_TEAM</li></ul><li>SEND_FILES, RECEIVE_FILES.<sup>3</sup> Controls whether a bot can send and receive files in personal chat (not yet supported for group chat or channels).</li></ul></td>
    <td valign="top"><ul><li>Bots only have access to teams to which they&#39;ve been added or to users who have installed them.</li><li>Bots only receive messages in which they&#39;re explicitly mentioned by users. This data leaves the corporate network.</li><li>    Bots can only reply to conversations in which they&#39;re mentioned.</li><li>After a user has conversed with a bot, if the bot stores that user&#39;s ID, it can send that user direct messages at any time. </li><li>It is theoretically possible for bot messages to contain links to phishing or malware sites, but bots can be blocked by the user, the tenant admin, or globally by Microsoft. </li><li>A bot can retrieve (and might store) very basic identity information for the team members the app has been added to, or for individual users in personal or group chats. To get further information about these users, the bot must require them to sign in to Azure Active Directory (Azure AD). </li><li>Bots can retrieve (and might store) the list of channels in a team; this data leaves the corporate network. </li><li>When a file is sent to a bot, the file leaves the corporate network. Sending and receiving files requires user approval for each file. </li><li>By default, bots don&#39;t have the ability to act on behalf of the user, but bots can ask users to sign in; as soon as the user signs in, the bot will have an access token with which it can do additional things. Exactly what those additional things are depends on the bot and where the user signs in: a bot is an Azure AD app registered at <a href="https://apps.dev.microsoft.com/">https://apps.dev.microsoft.com/</a> and can have its own set of permissions.</li><li>Bots are informed whenever users are added to or deleted from a team.</li><li>Bots don&#39;t see users&#39; IP addresses or other referrer information. All information comes from Microsoft. (There is one exception: if a bot implements its own sign-in experience, the sign-in UI will see users&#39; IP addresses and referrer information.)</li><li>Messaging extensions, on the other hand, do see users&#39; IP addresses and referrer information.</li><li>App guidelines (and our AppSource review process) require discretion in posting personal chat messages to users (via the POST_MESSAGE_TEAM permission) for valid purposes. In the event of abuse, users can block the bot, tenant admins can block the app, and Microsoft can block bots centrally if necessary.</li></ul></td>
</tr>
</tbody>
<tfoot>
<tr><td align="right"><sup>1</sup></td><td colspan="3">Some bots only send messages (POST_MESSAGE_USER). They&#39;re called &quot;notification-only&quot; bots, but the term doesn&#39;t refer to what a bot is allowed or not allowed to do, it means that the bot doesn&#39;t want to expose a conversational experience. Teams uses this field to disable functionality in the UI that would ordinarily be enabled; the bot isn&#39;t restricted in what it&#39;s allowed to do compared to bots that do expose a conversational experience.</td></tr>
<tr><td align="right"><sup>3</sup></td><td colspan="3">Governed by the <code>supportsFiles</code> Boolean property on the bot object in the manifest.json file for the app.</td>
</tr>
</tfoot>
</table>

> [!Note]
> <ul><li>If a bot has its own sign-in, there's a second—different—consent experience the first time the user signs in.</li><li>Currently, the Azure AD permissions associated with any of the capabilities inside a Teams app (bot, tab, connector, or messaging extension) are completely separate from the Teams permissions listed here.</li></ul>


## Tabs

A tab is a website running inside Teams.

<table>
  <tr>
    <th width="25%">Required permissions</th>
    <th width="25%">Optional permissions</th>
    <th width="50%">Considerations</th>
  </tr>
  <tr>
    <td valign="top">SEND_AND_RECEIVE_WEB_DATA</td>
    <td valign="top">None (currently).</td>
    <td valign="top"><ul><li>The risk profile for a tab is almost identical to that same website running in a browser tab. </li><li>A tab also gets the context in which it&#39;s running, including the sign-in name and UPN of the current user, the Azure AD Object ID for the current user, the ID of the Office 365 Group in which it resides (if it's a team), the tenant ID, and the current locale of the user. However, to map these IDs to a user&#39;s information, the tab would have to make the user sign in to Azure AD.</li></ul></td>
  </tr>
  </table>

## Connectors

A connector posts messages to a channel when events in an external system occur.

  <table>
  <tr>
    <th width="25%">Required permissions</th>
    <th width="25%">Optional permissions</th>
    <th width="50%">Considerations</th>
  </tr>
  <tr>
    <td valign="top">POST_MESSAGE_CHANNEL</td>
    <td valign="top">REPLYTO_CONNECTOR_MESSAGE. Certain connectors support <em>actionable messages</em>, which allow users to post targeted replies to the connector message, for example by adding a response to a GitHub issue or adding a date to a Trello card.</td>
    <td valign="top"><ul><li>The system that posts connector messages doesn&#39;t know who it&#39;s posting to or who receives the messages: no information about the recipient is disclosed. (Microsoft is the actual recipient, not the tenant; Microsoft does the actual post to the channel.)</li><li>No data leaves the corporate network when connector messages are posted to a channel.</li><li>Connectors that support actionable messages (REPLYTO_CONNECTOR_MESSAGE permission) also don&#39;t see IP address and referrer information; this information is sent to Microsoft and then routed to HTTP endpoints that were previously registered with Microsoft in the Connectors portal.</li><li>Each time a connector is configured for a channel, a unique URL for that connector instance is created. If that connector instance is deleted, the URL can no longer be used.</li><li>Connector messages can&#39;t contain file attachments.</li><li>The connector instance URL should be treated as secret/confidential: anyone who has that URL can post to it, like an email address. Therefore, there&#39;s some risk of spam or links to phishing or malware sites. If that were to happen, team owners can delete the connector instance.</li><li>If the service that sends connector messages were to become compromised and start sending spam/phishing/malware links, a tenant administrator can prevent new connector instances from being created and Microsoft can block them centrally.</li></ul></td>
  </tr>
</table>

> [!Note]
> It's not currently possible to know which connectors support actionable messages (REPLYTO_CONNECTOR_MESSAGE permission).


## Outgoing webhooks

_Outgoing webhooks_ are created on the fly by team owners or team members if sideloading is enabled for a tenant. They aren't capabilities of Teams apps; this information is included for completeness.

<table>
  <tr>
    <th width="25%">Required permissions</th>
    <th width="25%">Optional permissions</th>
    <th width="50%">Considerations</th>
  </tr>
    <tr>
    <td valign="top">RECEIVE_MESSAGE, REPLYTO_MESSAGE. Can receive messages from users and reply to them.</td>
    <td valign="top">None</td>
    <td valign="top"><ul><li>Outgoing webhooks are similar to bots but have fewer privileges. They must be explicitly mentioned, just like bots.</li><li>When an outgoing webhook is registered, a <em>secret</em> is generated, which allows the outgoing webhook to verify that the sender is Microsoft Teams as opposed to a malicious attacker. This secret should remain a secret; anyone who has access to it can impersonate Microsoft Teams. If the secret is compromised, the outgoing webhook can be deleted and re-created, and a new secret will be generated.</li><li>Although it&#39;s possible to create an outgoing webhook that doesn&#39;t validate the secret, we recommend against it.</li><li>Other than receiving and replying to messages, outgoing webhooks can&#39;t do much: they can&#39;t proactively send messages, they can&#39;t send or receive files, they can&#39;t do anything else that bots can do except receive and reply to messages.</li></ul></td>
  </tr>
</table>
