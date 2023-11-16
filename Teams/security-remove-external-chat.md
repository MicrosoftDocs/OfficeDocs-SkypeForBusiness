---
title: Remove an external chat from a user's view in Microsoft Teams (admin)
author: dansimp
ms.author: dansimp
manager: dansimp
ms.date: 11/16/2023
ms.topic: conceptual
ms.service: msteams
ms.reviewer: 
audience: admin
description: Admin instructions for how to remove chat from a user external to an organization
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
  - CSH
appliesto: 
  - Microsoft Teams
---

# Remove an external chat from a user's view in Microsoft Teams (admin)
As a tenant administrator, you can use the new RemoveAllAccessForUser [need to add link to real API doc here when ready] Graph API to remove an externally-initiated chat from your user’s view.  

Microsoft Teams admins might need to remove user chats that were initiated by a user outside of your organization.  For example, if one of your users was contacted in chat by a someone outside of your company, and that chat contained inappropriate or malicious content, you can remove that chat.

To use the RemoveAllAccessForUser Graph API, you need to provide three parameters: the tenantId, the userId, and the chatsId/threadId. The tenantId is the unique identifier of your Teams tenant. The userId is the unique identifier of your user that you want to remove the chat for. The chatsId/threadId is the unique identifier of the Teams chat thread that you want to remove your user from. 

You can obtain these three parameters from the new Unified Audit Log (UAL) events that are generated when an external user communicates with a user in your tenant. The UAL events contain information about the sender, the recipient, the chat thread, and the message. You can use the UAL events to identify the chat thread that you want to revoke access from, and then extract the tenantId, the userId, and the chatsId/threadId from the event details. 

## Steps to use the RemoveAllAccessForUser Graph API
- Step 1: Search for the [UAL events](/purview/audit-teams-audit-log-events.md) that match your criteria.  If you want to find all events where a user was added to a chat, you can use the “MemberAdded” event in your search query. 
- Step 2: Extract the tenantId, the userId, and the chatsId/threadId from the UAL event details 
- Step 3: Call the RemoveAllAccessForUser Graph API with the desired parameters 

### Step 1: Search for the UAL events that match your criteria 
To search for the UAL events that match your criteria, you can use the Search-UnifiedAuditLog graph API, or you can use the audit log search feature in the Microsoft 365 Compliance portal. The rest of this document assumes you are using the interactive version in the Microsoft 365 Compliance Portal.  To accomplish this using the portal, use the following steps: 

1. Sign in to https://compliance.microsoft.com as a global administrator or an audit log administrator. 
2. In the left navigation, click **Audit**.
3. On the Audit log search page, specify the following criteria:

  - On the Audit page, click Search.
  - Activities: Select MemberAdded (and optionally MessageReceived) from the “Activities – operation names” field and choose “MicrosoftTeams” for the “Workload”.
  - Date range: Select a date range that covers the time period when the external user communicated with the user in your tenant.
(optional) Users: Enter the UPN of the user in your tenant who you are interested in.

4. Click Search.  This will queue a search to run in the background. 

Once complete, review the search results and identify the UAL events that involve the chat and user that you are interested in (Step 3 below). 

### Step 2: Extract the tenantId, the userId, and the chatsId/threadId from the UAL event details 
To extract the tenantId, the userId, and the chatsId/threadId from the UAL event details, you can use the OrganizationId, UserKey, and ChatThreadId fields of the event.  If you searched for the MemberAdded event, you may see events where your users were added to an external chat and also where your users added an external user to a chat.  You will want to find the events where your user in your tenant is in the “Members” detail section (this indicates that this is the user that was added – see figure 2 below).  To do this, follow these steps: 

1. Select one of the UAL events that involve the external user that you want to revoke access from. 
2. On the Event details pane: 

  - Copy the value of the OrganizationId field. This is the tenantId of your Teams tenant. 
  - Copy the value of the UserKey field. This is the userId of the user in your tenant that was added to the chat.  
  - Copy the value of the ChatThreatId field. This is the chatsId/threadId of the Teams chat thread that the message belongs to. 

See the following screenshot showing an example of a Purview search result details:

:::image type="content" source="./media/graph-delete-purview-search-detail.png" alt-text="Microsoft Purview search details" lightbox="./media/graph-delete-purview-search-detail.png":::
*Figure 1 (details from UAL MemberAdded event)*

:::image type="content" source="./media/graph-delete-purview-member-detail.png" alt-text="Microsoft Purview member details" lightbox="./media/graph-delete-purview-member-detail.png":::
*Figure 2 (Members detail from MemberAdded UAL event)*

### Step 3 Call the RemoveAllAccessForUser Graph API with the desired parameters 
To call the RemoveAllAccessForUser Graph API with the parameters, you need to use an HTTP POST request to the graph API:

```rest
POST https://graph.microsoft.com/v1.0/chats/{chatsId}/removeAllAccessForUser 
```

Replace {chatsId} with the Id of the chat you want to act on.  The request body should contain a JSON “user” object with the following properties: 

 - tenantId: The tenantID of your Teams tenant. 
 - Id: The userID of the user in your tenant that you want to move the chat from. 

For example, a request might look like this: 

```rest
POST https://graph.microsoft.com/v1.0/chats/19:7d8980.........f94061cf8c2@unq.gbl.spaces/removeAllAccessForUser 
Content-Type: application/json 

{ 
  "user": { 
    "id" : "d864e79f-……..-0eeb4d61fdc2", 
    "tenantId": "2a690434-………-13600199a" 
  } 
} 
```

To authenticate the request, you need to provide a valid access token in the Authorization header. The access token should have the Chat.ReadWrite.All permissions. To obtain the access token, you can use the Azure AD OAuth 2.0 endpoint. For more information, see [Microsoft Graph - Get access without a user](/graph/auth-v2-service). 

If the request is successful, the response will have a status code of “204 No Content” and an empty body. If the request fails, the response will have an error code and a message that explains the reason for the failure. 

There are many ways to call a Microsoft Graph API – if you are unfamiliar with how to do this, you might want to start with an interactive tool such as [Graph Explorer](/graph/graph-explorer/graph-explorer-overview).  Some admins create an app or use PowerShell to interact with Graph APIs as well. 