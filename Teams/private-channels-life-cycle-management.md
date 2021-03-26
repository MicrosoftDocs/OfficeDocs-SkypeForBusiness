---
title: Manage the private channels in Microsoft Teams with Graph API
author: MikePlumleyMSFT
ms.author: mikeplum
manager: serdars
ms.reviewer: suchakr, phlouie
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to manage private channels in your organization using Graph API.
---

# Manage the life cycle of private channels in Microsoft Teams

Here you'll find the guidance you need to manage use the Graph API to manage [Teams private channels](./private-channels.md) in your organization.

## Set whether team members can create private channels

As an admin, you can use Graph API to control whether members can create private channels in specific teams. Here's an example.

```Graph API
PATCH /teams/<team_id>​
{"memberSettings": ​
  {​
    "allowCreatePrivateChannels": false​
  }​
}
```

## Create a private channel on behalf of a team owner

As an admin, you can use the Graph API to create a private channel on behalf of a team owner. For example, you may want to do this if your organization wants to centralize creation of private channels.

```Graph API
POST /teams/{id}/channels​
{ "membershipType": "Private",​
  "displayName": "<Channel_Name>",​
  "members":[{    ​
           "@odata.type":"#microsoft.graph.aadUserConversationMember",​
           "user@odata.bind":"https://graph.microsoft.com/beta/users('<user_id>')",​
           "roles":["owner"]​
            }]
```

## Get a list of all private channel messages

You may want to get a list of all messages and replies posted in a private channel for archiving and auditing purposes.  Here's how to use Graph API to do this.

```Graph API
GET /teams/{id}/channels/{id}/messages​
GET /teams/{id}/channels/{id}/messages/{id}/replies/{id}
```

## Find SharePoint URLs for all private channels in a team

Whether you're looking to perform eDiscovery or legal hold on files in a private channel or looking to build a custom app that places files in specific private channels, you'll want a way to query the unique SharePoint site collections that are created for each private channel.

As an admin, you can use Graph APIs commands to query these URLs.

You can try these commands through [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

1. Use the following to get the list of private channel IDs for a given team, where <group_id> is the group ID of the team. You'll need this in subsequent calls. (You can easily find the group ID in the link to the team).

    **Request**

    ```Graph API
    GET https://graph.microsoft.com/beta/teams/<group_id>/channels?$filter=membershipType eq 'private'
    ```

    **Response**

    ```Graph API
    HTTP/1.1 200 OK
    Content-type: application/json
    Content-length:
    
    {
      "value": [
        {
          "description": "description-value",
          "displayName": "display-name-value",
          "id": "channel_id",
          "membershipType": "membership-type-value",
          "isFavoriteByDefault": false,
          "webUrl": "webUrl-value",
          "email": "email-value"
        }
      ]
    }
    ```

2. For each private channel which you want to get the SharePoint URL, make the following request, where &lt;channel_id&gt; is the channel ID.

    **Request**

    ```Graph API
    GET https://graph.microsoft.com/beta/teams/<group_id>/channels/<channel_id>/filesFolder
    ```

    **Response**

    ```Graph API
    HTTP/1.1 200 OK
    Content-type: application/json
    Content-length:
      
    {
      "value": [
        {
          "description": "description-value",
          "displayName": "display-name-value",
          "id": "channel_id",
          "membershipType": "membership-type-value",
          "isFavoriteByDefault": false,
          "webUrl": "webUrl-value",
          "email": "email-value"
        }
      ]
    }
    ```

## List and update roles of owners and members in a private channel

You may want to list out the owners and members of a private channel to decide whether you need to promote certain members of the private channel to an owner. This can happen when you have owners of private channels who have left the organization and the private channel requires admin help to claim ownership of the channel.

As an admin, you can use the Graph API to perform these actions.

You can try these commands through [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

1. Use the following, where &lt;group_id&gt; is the group ID of the team and &lt;channel_id&gt; is the channel ID.

    **Request**

    ```Graph API
    GET https://graph.microsoft.com/beta/teams/<group_id>/channels/<channel_id>/members
    ```
    
    **Response**

    ```Graph API
    HTTP/1.1 200 OK Content-type: application/json
    Content-length: 
    {
          "@odata.context": "https://graph.microsoft.com/beta/$metadata#teams({group_id}')/channels('{channel_id}')/members",
          "@odata.count": 2,
          "value": [
              {
                  "@odata.type": "#microsoft.graph.aadUserConversationMember",
                  "id": "id-value",
                  "roles": [],
                  "displayName": "display-name-value",
                  "userId": "userId-value",
                  "email": "email-value"
              },
              {
                  "@odata.type": "#microsoft.graph.aadUserConversationMember",
              "id": "id-value",
              "roles": ["owner"],
              "displayName": "display-name-value",
              "userId": "userId-value",
              "email": "email-value"
              }
          ]
    }
    ```    
2. Use the following to promote the member to an owner, where &lt;group_id&gt;, &lt;channel_id&gt;, and &lt;id&gt; are returned from the previous call. Note that &lt;id&gt; and &lt;userId&gt; returned from the previous call aren't the same and aren't interchangeable. Make sure you use &lt;id&gt;.

    **Request**

    ```Graph API
    PATCH 
    https://graph.microsoft.com/beta/teams/<group_id>/channels/<channel_id>/members/<id>
      
    {
    "@odata.type": "#microsoft.graph.aadUserConversationMember",
    "roles": ["owner"]
    }
    ```

    **Response**

    ```Graph API
    HTTP/1.1 200 OK
    Content-type: application/json

    {
      "@odata.context": "https://graph.microsoft.com/beta/$metadata#teams('{group_id}')/channels('{channel_id}')/members/$entity",
      "@odata.type": "#microsoft.graph.aadUserConversationMember",
      "id": "id-value",
      "roles": ["owner"],
      "displayName": "display-name-value",
      "userId": "userId-value",
      "email": "email-value"
     }
    ```

## Related topics

[Use the Microsoft Graph API to work with Teams](/graph/api/resources/teams-api-overview?view=graph-rest-1.0)

[List channels](/graph/api/channel-list)

[Create channel](/graph/api/channel-post)

[Add member to channel](/graph/api/conversationmember-add)

[Update member in channel](/graph/api/conversationmember-update)

[Remove member from channel](/graph/api/conversationmember-delete)