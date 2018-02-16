---
title: Configure permissions for Who
author: ChuckEdmonson
ms.author: chucked
manager: lolaj
ms.date: 12/07/2017
ms.topic: article
ms.service: msteams
description: Practical guidance for deploying cloud voice features in Microsoft Teams.
Set_Free_Tag: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

Configure permissions for Who
=============================

Users can use the Who app with Microsoft Teams to help them ask questions and find anyone in the organization based on what they're working on and who they work with.

To ensure users get the most out of Who, you must turn on the following member permissions in Microsoft Graph.

- Calendars.Read

- Calendars.Read.Shared

- Mail.Read

- MailboxSettings.ReadWrite

- People.Read

- People.Read.All

- Sites.Read.All

- User.Read.All

For more information about how to manage Microsoft Graph permission scopes, see [Permission scopes](https://msdn.microsoft.com/Library/Azure/Ad/Graph/howto/azure-ad-graph-api-permission-scopes).
 
For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://developer.microsoft.com/graph/docs/concepts/permissions_reference).