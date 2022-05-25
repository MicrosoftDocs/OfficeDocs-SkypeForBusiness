---
title: Export content with the Microsoft Teams Export APIs
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.topic: reference
audience: admin
ms.service: msteams
ms.reviewer: vikramju
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
- **Chat Message Properties:** Refer to the complete list of properties that Teams Export APIs support [here](/graph/api/resources/chatmessage#properties).

> [!NOTE]
> Export APIs do not support *reactions*.

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

- Microsoft Teams APIs in Microsoft Graph that access sensitive data are considered protected APIs. Export APIs require that you have additional validation, beyond permissions and consent, before you can use them. To request access to these protected APIs, complete the [request form](https://aka.ms/teamsgraph/requestaccess).
- Application permissions are used by apps that run without a signed-in user present; application permissions can only be consented by an administrator. The following permissions are needed:
  - *Chat.Read.All*: enables access to all 1:1, Group chat, and meeting chat messages
  - *ChannelMessage.Read.All*: enables access to all channel messages
  - *User.Read.All*: enables access to the list of users for a tenant

## License requirements for Teams Export APIs

Export API supports Security and Compliance (S+C) and general usage scenarios through a model query parameter. S+C scenarios (Model A) include seeded capacity and require an E5 subscription and general usage scenarios (Model B) are available for all subscriptions and is consumption only. For more information about seeded capacity and consumption fees, see [Licensing and payment requirements for Microsoft Graph Teams APIs](/graph/teams-licenses).

### S+C/Model A scenarios

Restricted to applications performing security and/or compliance functions, users must have specific E5 licenses to use this functionality and receive seeded capacity. Seeded capacity is per user and is calculated per month and is aggregated at the tenant level. For usage beyond the seeded capacity, app owners are billed for API consumption. Model A can only access messages from users with an assigned E5 license.

### General usage/Model B scenarios

Available for all non-S+C related scenarios, there are no license requirements or seeded capacity. When consumption meters become available, app owners will be charged for all monthly API calls.

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
> For more details on chatMessage resource, see the [chatMessage resource type](/graph/api/resources/chatmessage) article.
