---
title: Integrate custom collaboration applications with Microsoft 365
ms.reviewer: daro
ms.date: 09/27/2023
ms.author: jtremper
author: jacktremper
manager: pamgreen
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
description: Learn about how to integrate custom collaboration applications with Microsoft 365.
---

# Integrate custom collaboration applications with Microsoft 365

This article provides an overview of collaboration-related integrations in Microsoft 365 services. This may be of interest to independent software developers (ISVs) developing applications that integrate with Microsoft 365. Resources to learn how to create these types of integrations in any application are included in the following sections.  APIs are also available to export data from Teams for use in such custom applications.

## Collaboration services in Microsoft 365

Microsoft 365 provides standard application programming interfaces (APIs) to all developers to enable integrations, including the functionality relied upon by Microsoft product and services for such integrations. Developers can use these APIs to create many similar experiences in their own applications.

#### User account management

Microsoft 365 uses Microsoft Entra ID for authentication and authorization of users, including people outside your organization (B2B guests), and for maintaining user profile information.

Microsoft Entra authentication is used by Microsoft 365 web applications such as SharePoint and OneDrive, and by client applications such as Outlook and Teams. User profile information is viewable by users in a variety of places in Microsoft 365 and its associated applications.

Microsoft documents and makes available the APIs necessary to create these experiences in your custom applications:

-	[person resource type](/graph/api/resources/person)
-	[List directReports](/graph/api/user-list-directreports)
-	[List manager](/graph/api/user-list-manager)

Microsoft 365 groups are used to give groups of users access to a set of related applications, including SharePoint, Planner, and Teams. Microsoft documents and makes available the APIs necessary to create these experiences in your custom applications:

-	[group resource type](/graph/api/resources/group)

#### Calendar management

Microsoft 365 uses Exchange Online to manage users’ mailboxes and calendars. Mail and calendar information is made available to users in applications such as Outlook and Teams. Microsoft documents and makes available the APIs necessary to create these experiences in your custom applications:

-	[calendar resource type](/graph/api/resources/calendar)

#### File management

Microsoft 365 uses SharePoint and OneDrive for all file storage and sharing. The files APIs allow any application to access and modify files.

Microsoft 365 uses insights to provide lists of documents that are trending, or that a user has viewed, modified, or shared. For example, OneDrive provides this information to users. These insights are available to any application via the Office Graph Insights API.

Microsoft documents and makes available the APIs necessary to create these experiences in custom applications:

-	[Working with files in Microsoft Graph](/graph/api/resources/onedrive)
-	[Permission resource type](/graph/api/resources/permission)
-	[officeGraphInsights resource type](/graph/api/resources/officegraphinsights)

#### Search

Microsoft 365 uses a unified search engine to cover many different experiences from a single interface. This can be extended to other applications by using the Microsoft Search API. Microsoft documents and makes available the APIs necessary to create these experiences in your custom applications:

-	[Overview of the Microsoft Search API in Microsoft Graph](/graph/search-concept-overview)

## Exporting Messages and other Media from Microsoft Teams

Once you’ve integrated your custom application with Microsoft 365, you can export direct messages, group messages, channel posts (including their replies), call and meeting transcripts and recordings from Teams by using published APIs.

> [!NOTE]
> Some of the APIs listed below are metered and have costs associated with their use.

#### Direct messages, group messages, and meeting messages

Teams includes direct messages (1-on-1 chats), group chats, and chats associated with meetings. Messages in Teams may contain pain text, rich HTML, images, links, etc. Microsoft documents and makes available the APIs necessary to export this data out of Microsoft Teams:

-	[List Chats](/graph/api/chat-list)
-	[Get Chat](/graph/api/chat-get)
-	[List members of a Chat](/graph/api/chat-list-members)
-	[Get chatMessage in a channel or chat](/graph/api/chatmessage-get)
-	[chats: getAllMessages](/graph/api/chats-getallmessages)

#### Channel posts

Channel posts, also known as threaded conversations, are conversations that occur in a Teams channel. Microsoft documents and makes available the APIs necessary to export this data out of Teams:

-	[List joinedTeams](/graph/api/user-list-joinedteams)
-	[List teams](/graph/api/teams-list)
-	[List Channels](/graph/api/channel-list)
-	[List allChannels](/graph/api/team-list-allchannels)
-	[Get Channel](/graph/api/channel-get)
-	[List members of a channel](/graph/api/channel-list-members)
-	[Get chatMessage in a channel or chat](/graph/api/chatmessage-get)
-	[channel: getAllMessages](/graph/api/channel-getallmessages)

#### Meeting recordings and transcripts

Recordings of Teams meetings and calls are stored in OneDrive or SharePoint. Microsoft documents and makes available the APIs necessary to export this data out of Teams:

-	[List recordings](/graph/api/onlinemeeting-list-recordings)
-	[Get callRecording](/graph/api/callrecording-get)
-	[onlineMeeting: getAllRecordings](/graph/api/onlinemeeting-getallrecordings)

> [!NOTE]
> The APIs to list and download call/meeting recordings are currently in beta.

Transcripts of Teams meetings and calls are stored in OneDrive and SharePoint. Microsoft documents and makes available the APIs necessary to export this data out of Teams:

-	[List callTranscripts](/microsoftteams/platform/graph-api/meeting-transcripts/api-transcripts#list-calltranscripts)
-	[Get callTranscript](/microsoftteams/platform/graph-api/meeting-transcripts/api-transcripts#get-calltranscript)
-	[Get callTranscript content](/microsoftteams/platform/graph-api/meeting-transcripts/api-transcripts#get-calltranscript-content)

You can use the following APIs to get Teams meeting recordings and transcripts:

-	[List available drives](/onedrive/developer/rest-api/api/drive_list)
-	[Get Drive](/onedrive/developer/rest-api/api/drive_get)
-	[List items shared with the signed-in user](/onedrive/developer/rest-api/api/drive_sharedwithme)
-	[Download the contents of a DriveItem](/onedrive/developer/rest-api/api/driveitem_get_content)

## Support

As you start working with Microsoft Graph, check out these references to get started:

-	[Get started with Microsoft Graph Toolkit](/graph/toolkit/get-started/overview)
-	[Best practices for working with Microsoft Graph](/graph/best-practices-concept)

Developers who are working with and implementing the scenarios described in this article can obtain assistance from Microsoft and its engineers, including managed technical support, by emailing [InteropHelp@microsoft.com](mailto:InteropHelp@microsoft.com).
