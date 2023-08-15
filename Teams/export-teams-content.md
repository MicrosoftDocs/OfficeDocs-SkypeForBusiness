---
title: Export content with the Microsoft Teams Export APIs
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: reference
audience: admin
ms.service: msteams
ms.reviewer: smahadevan
ms.date: 09/15/2020
description: In this article, you will learn about how to export Teams content using the Microsoft Teams Export APIs.
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - NewAdminCenter_Update
  - seo-marvel-apr2020
ms.collection:
  - M365-collaboration
appliesto:
  - Microsoft Teams
---

# Export content with the Microsoft Teams Export APIs

Teams Export APIs allow you to export 1:1, group chat, meeting chats, and channel messages from Microsoft Teams. If your organization needs to export Microsoft Teams messages, you are able to extract them using Teams Export APIs. *Chat Message* represents an individual chat message within a [channel](/graph/api/resources/channel) or [chat](/graph/api/resources/chat). The chat message can be a root chat message or part of a reply thread that is defined by the **replyToId** property in the chat message.

Here are some examples on how you can use these export APIs:

- **Example 1**: If you have enabled Microsoft Teams in your organization and want to export all the Microsoft Teams messages to date programmatically by passing the date range for a given user or team.
- **Example 2**: If you want to programmatically export all user or team messages daily by providing a date range. Export APIs can retrieve all the messages created or updated during the given date range.

## What is supported by the Teams Export APIs?

- **Bulk Export of Teams Message:** Teams Export APIs support up to 200 RPS Per App Per tenant and 600 RPS for an Application, with these limits you should be able to bulk export of Teams messages.
- **Application Context**: To call Microsoft Graph, your app must acquire an access token from the Microsoft identity platform. The access token contains information about your app and the permissions it has for the resources and APIs available through Microsoft Graph. To get an access token, your app must be registered with the Microsoft identity platform and be authorized by either a user or an administrator for access to the Microsoft Graph resources it needs.

    If you are already familiar with integrating an app with the Microsoft identity platform to get tokens, see the [Next Steps](/graph/auth/auth-concepts#next-steps) section for information and samples specific to Microsoft Graph.
- **Hybrid Environment:** Export APIs support messages sent by users who are provisioned on Hybrid Environment (on-premises Exchange and Teams). Any messages that are sent by users who are configured for hybrid environment will be accessible using Export APIs.
- **User Deleted Messages:** Messages that are deleted by users from the Teams client can be accessed using export APIs up to 21 days from the time of deletion.
- **Message Attachments:** Export APIs include the links to the attachments that are sent as part of messages. Using Export APIs you can retrieve the files attached in the messages.
- **Reactions:** Export APIs support reactions initiated by a user on a Teams message. Reactions currently supported are heart, angry, like, sad, surprised, and laugh. In addition to Reactions, Export API also supports Reaction Edit History which includes changes and updates made to a reaction on a message.
- **Shared Channel Messages:** Export APIs support capturing messages from a Shared Channel.
- **Deleted Teams:** Export API supports [capturing messages from deleted Teams and deleted Private Channels](/graph/api/deletedteam-getallmessages) for more information.
- **Chat Message Properties:** Refer to the [complete list of properties that Teams Export APIs support](/graph/api/resources/chatmessage#properties).
- **Control Messages:** Export API supports capturing control messages in addition to the user generated messages. Control Messages are system generated messages that appear on the Teams client and carry important information such as "User A added User B to the chat and shared all chat history" along with the timestamp. System messages enable the caller to have insights about events that happened in a team, a channel, or a chat. Currently Export API supports the [Add Member and Remove Member event for chats, teams and standard channels](/graph/system-messages#supported-system-message-events) for information and system messages samples specific to Microsoft Graph.

## How to access Teams Export APIs

- **Example 1** is a simple query to retrieve all the messages of a user or team without any filters:

  ```HTTP
  GET https://graph.microsoft.com/v1.0/users/{id}/chats/getAllMessages
  ```

  ```HTTP
  GET https://graph.microsoft.com/v1.0/teams/{id}/channels/getAllMessages
  ```

- **Example 2** is a sample query to retrieve all the messages of a user or team by specifying date time filters and top 50 messages:

  ```HTTP
  GET https://graph.microsoft.com/v1.0/users/{id}/chats/getAllMessages?$top=50&$filter=lastModifiedDateTime gt 2020-06-04T18:03:11.591Z and lastModifiedDateTime lt 2020-06-05T21:00:09.413Z
  ```

  ```HTTP
  GET https://graph.microsoft.com/v1.0/teams/{id}/channels/getAllMessages?$top=50&$filter=lastModifiedDateTime gt 2020-06-04T18:03:11.591Z and lastModifiedDateTime lt 2020-06-05T21:00:09.413Z
  ```

> [!NOTE]
> The API returns response with next page link in case of multiple results. For getting next set of results, simply call GET on the url from @odata.nextlink. If @odata.nextlink is not present or null then all messages are retrieved.

## Prerequisites to access Teams Export APIs

- Microsoft Teams APIs in Microsoft Graph that access sensitive data are considered protected APIs. You can call these APIs as long as the requirements for [accessing without a user](/graph/auth-v2-service) are met.
- Application permissions are used by apps that run without a signed-in user present; application permissions can only be consented by an administrator. The following permissions are needed:
  - *Chat.Read.All*: enables access to all 1:1, Group chat, and meeting chat messages
  - *ChannelMessage.Read.All*: enables access to all channel messages
  - *User.Read.All*: enables access to the list of users for a tenant

## License requirements for Teams Export APIs

Export API supports Security and Compliance (S+C) and general usage scenarios through a model query parameter. S+C scenarios (Model A) include seeded capacity and require an E5 subscription and general usage scenarios (Model B) are available for all subscriptions and is consumption only. For more information about seeded capacity and consumption fees, see [Licensing and payment requirements for Microsoft Graph Teams APIs](/graph/teams-licenses).

### S+C/Model A scenarios

Restricted to applications performing security and/or compliance functions, users must have specific E5 licenses to use this functionality and receive seeded capacity. Seeded capacity is per user and is calculated per month and is aggregated at the tenant level. For usage beyond the seeded capacity, app owners are billed for API consumption. Model A can only access messages from users with an assigned E5 license.

|Partner Name|Partner Solution|
|---|---|
|![logo-of-smarsh](media/smarsh-logo.png) |[Microsoft Teams Archiving and Compliance](https://www.smarsh.com/channel/microsoft-teams/)|

### General usage/Model B scenarios

Available for all non-S+C related scenarios, there are no license requirements or seeded capacity. When consumption meters become available, app owners will be charged for all monthly API calls.

The following partners are certified. Your company may choose to work with any combination of these partners within your enterprise.  

|Partner Name|Partner Solution|
|---|---|
|![logo-of-rubrik](media/rubrik.png) |[Microsoft Teams backup and recovery](https://www.rubrik.com/solutions/microsoft-365) |
|![logo-of-veeam](media/veeam.png) |[Microsoft Teams backup and recovery](https://www.veeam.com/backup-microsoft-office-365.html) |

### Next steps
If you are a vendor seeking to join the certification program, fill out [this form](https://forms.office.com/pages/responsepage.aspx?id=v4j5cvGGr0GRqy180BHbRymC9dkiqEZFkLXIAijLzONUREtFR1JKR1lQVFJCVFc5QlJaS1FDWEhaSS4u) as the next step. If you need to provide additional context and details, mail to MS Teams Ecosystem Team (TeamsCategoryPartner@microsoft.com).

### Evaluation Mode (default)

No model declaration enables access to APIs with limited usage per each requesting application for evaluation purposes.

## JSON representation

The following example is a JSON representation of the resource:

Namespace: microsoft.graph

```JSON
{
"id": "string (identifier)",
"replyToId": "string (identifier)",
"from": {"@odata.type": "microsoft.graph.identitySet"},
"etag": "string",
"messageType": "string",
"createdDateTime": "string (timestamp)",
"lastModifiedDateTime": "string (timestamp)",
"deletedDateTime": "string (timestamp)",
"subject": "string",
"from": {
                "application": null,
                "device": null,
                "conversation": null,
                "user": {

                    "id": \[{"@odata.type": "microsoft.graph.user"}\],
                    "displayName": "User Name",

                    "userIdentityType": "aadUser"                }
            },
"body": {"@odata.type": "microsoft.graph.itemBody"},
"summary": "string",

"chatId": \[{"@odata.type": "microsoft.graph.chat"}\]

"attachments": \[{"@odata.type": "microsoft.graph.chatMessageAttachment"}\],
"mentions": \[{"@odata.type": "microsoft.graph.chatMessageMention"}\],
"importance": "string",
"locale": "string",
}
```

> [!NOTE]
> For more information on chatMessage resource, see the [chatMessage resource type](/graph/api/resources/chatmessage) article.

## Export API filters

Export API hosted on the Teams Graph Service gets all user messages from the Substrate user mailbox using `users/{userId}/chats/getAllMessages`. Export API retrieves both sent and received messages for a user which leads to export of duplicate messages when calling the API for all users in the chat thread.

Export API has filter parameters that help optimize the messages returned for a chat thread. The [API GET](https://graph.microsoft.com/v1.0/users/{id}/chats/getAllMessages) supports new filter parameters that allow a way to extract messages based on the sent user, bot, application and system event messages. The filter parameter supports messages sent by the following: 

 - users (multiple user Ids supported in the same request) 

 - applications (bots, connectors etc.) 

 - anonymous users 

 - federated users (external access users)
   
 - system event messages (control messages)
   
These parameters are part of the request’s `$filter`. If none of these parameters are present in the request, the messages from all the users present in the specified user chats will be returned.   

The filtering scenarios that are supported are as follows: 

```
$filter=from/application/applicationIdentityType eq '<appType>' (bots/tenantBots/connectors, etc.)  
  
$filter=from/user/id eq '<oid>' (any number of id filters)  
  
$filter=from/user/userIdentityType eq 'anonymousGuest'  
  
$filter=from/user/userIdentityType eq 'federatedUser' (guest/external)  
  
$filter=from/application/applicationIdentityType eq '<appType>' or from/user/id eq '<oid>' (sent by app or userid)  
  
$filter=from/application/applicationIdentityType eq '<appType>' or from/user/userIdentityType eq 'anonymousGuest' (sent by app or anonymous)  

$filter=from/application/applicationIdentityType eq '<appType>' or from/user/userIdentityType eq 'federatedUser' (sent by app or federated)  
  
$filter=from/application/applicationIdentityType eq '<appType>' or from/user/userIdentityType eq 'anonymousGuest' or from/user/userIdentityType eq 'federatedUser' (sent by app, anonymous or federated)  
  
$filter=from/user/id eq '<oid>' or from/user/userIdentityType eq 'anonymousGuest' (sent by any number of userid or anonymous)  
  
$filter=from/user/id eq '<oid>' or from/user/userIdentityType eq 'federatedUser' (sent by any number of userid or federated)  

$filter=from/application/applicationIdentityType eq '<appType>' or from/user/id eq '<oid>' or from/user/userIdentityType eq 'anonymousGuest' or from/user/userIdentityType eq 'federatedUser' (sent by any number of userid or federated or anonymous)
 
$filter=from/application/applicationIdentityType eq '<appType>' or from/user/id eq '<oid>' or from/user/userIdentityType eq 'anonymousGuest' or from/user/userIdentityType eq 'federatedUser' (sent by any number of userid or federated or anonymous) or messsageType eq 'systemEventMessage'

(<any of the previous filters>) and (lastModifiedDateTime+gt+<date>+and+lastModifiedDateTime+lt+<date>)  
```

 - The query returns messages sent by the specified user if `from/user/id eq ‘{oid}’` is present.
   
 - The query returns messages sent by the federated users that are part of the user chats, if `from/user/userIdentityType eq ‘federatedUser’` is present.

 - the query returns messages sent by the specified application type if `from/application/applicationIdenitytyType eq '{appType}'` is present.
   
 - the query returns messages sent by the system if `messageType eq 'systemEventMessage'` is present

These parameters can be combined between them using the OR operators as well as by combining with the `lastModifiedDateTime` `$filter` parameter.
