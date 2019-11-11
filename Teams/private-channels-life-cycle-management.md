---
title: Manage the life cycle of private channels in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: suchakr, phlouie
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to manage the life cycle of private channels in your organization. 
---

# Manage the life cycle of private channels in Microsoft Teams

Here you'll find the guidance you need to manage the life cycle of [private channels](private-channels.md) in your organization.

> [!IMPORTANT]
> If you're using the PowerShell steps in this article to manage private channels, you must install and use the latest version of the Teams PowerShell module from the PowerShell Test Gallery. For steps on how to do this, see [Install the latest Teams PowerShell module from the PowerShell Test Gallery](#install-the-latest-teams-powershell-module-from-the-powershell-test-gallery). The latest publicly available version of the Teams PowerShell module (currently [1.0.2](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2)) doesn't support managing private channels.

## Set whether team members can create private channels

Team owners can turn off or turn on the ability for members to create private channels in team settings. To do this, on the **Settings** tab for the team, turn off or turn on **Allow members to create private channels**.

As an admin, you can use Graph API to control whether members can create private channels in specific teams. Here's an example.

```
PATCH /teams/<team_id>​
{"memberSettings": ​
  {​
    "allowCreatePrivateChannels": false​
  }​
}
```

## Set whether users in your organization can create private channels

As an admin, you can set policies by using the Microsoft Teams admin center or PowerShell to control which users in your organization are allowed to create private channels.

### Using the Microsoft Teams admin center

Use teams policies to set which users in your organization are allowed to create private channels. To learn more, see [Manage teams policies in Teams](teams-policies.md).

### Using PowerShell

Use **CsTeamsChannelsPolicy** to set which users in your organization are allowed to create private channels. Set the **AllowPrivateChannelCreation** parameter to **true** to allow users who are assigned the policy to create private channels. Setting the parameter to **false** turns off the ability to create private channels for users who are assigned the policy.

To learn more, see [New-CsTeamsChannelsPolicy](https://docs.microsoft.com/powershell/module/skype/new-csteamschannelspolicy?view=skype-ps).

## Create a private channel on behalf of a team owner

As an admin, you can use PowerShell or Graph API to create a private channel on behalf of a team owner. For example, you may want to do this if your organization wants to centralize creation of private channels.

### Using PowerShell

```
New-TeamChannel –GroupId <Group_Id> –MembershipType Private –DisplayName “<Channel_Name>” –Owner <Owner_UPN>
```

### Using Graph API

```
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

```
GET /teams/{id}/channels/{id}/messages​
GET /teams/{id}/channels/{id}/messages/{id}/replies/{id}
```

## Find SharePoint URLs for all private channels in a team

Whether you're looking to perform eDiscovery or legal hold on files in a private channel or looking to build a line-of-business app that places files in specific private channels, you'll want a way to query the unique SharePoint site collections that are created for each private channel.

As an admin, you can use PowerShell or Graph APIs commands to query these URLs.

### Using PowerShell

1. Install and connect to the [SharePoint Online Management Shell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) with your admin account.
2. Run the following, where &lt;group_id&gt; is the group Id of the team. (You can easily find the group Id in the link to the team.)

    ```
    $sites = get-sposite -template "teamchannel#0"
    $groupID = “<group_id>"
    foreach ($site in $sites) {$x= Get-SpoSite -Identity
    $site.url -Detail; if ($x.RelatedGroupId -eq $groupID)
    {$x.RelatedGroupId;$x.url}}
    ```

### Using Graph API

You can try these commands through [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

1. Use the following to get the list of private channel Ids for a given team, where <group_id> is the group Id of the team. You'll need this in subsequent calls. (You can easily find the group Id in the link to the team).

    **Request**

    ```
    GET https://graph.microsoft.com/beta/teams/<group_id>/channels?$filter=membershipType eq 'private'
    ```

    **Response**

    ```
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

2. For each private channel which you want to get the SharePoint URL, make the following request, where &lt;channel_id&gt; is the channel Id.

    **Request**

    ```
    GET https://graph.microsoft.com/beta/teams/<group_id>/channels/<channel_id>/filesFolder
    ```

    **Response**

    ```
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

As an admin, you can use PowerShell or Graph APIs commands to query these URLs.

### Using PowerShell

1. Install and connect to the [Microsoft Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams) with your admin account.
2. Run the following, where &lt;group_id&gt; is the group Id of the team and &lt;channel_id&gt; is the channel Id.

    **Request**

    ```
    Get-TeamChannelUser -GroupId <group_id> -MembershipType Private -DisplayName "<channel_name>" 
    ```
    
    **Response**

    ```
    HTTP/1.1 200 OK Content-type: application/json
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

3. Promote a member to an owner.

    ```
    Add-TeamChannelUser -GroupId <group_id> -MembershipType Private -DisplayName "<channel_name>" -User <UPN> -Role Owner
    ```

### Using Graph API

You can try these commands through [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

1. Use the following, where &lt;group_id&gt; is the group Id of the team and &lt;channel_id&gt; is the channel Id.

    **Request**

    ```
    GET https://graph.microsoft.com/beta/teams/<group_id>/channels/<channel_id>/members
    ```
    
    **Response**

    ```
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
2. 	Use the following to promote the member to an owner, where &lt;group_id&gt;, &lt;channel_id&gt;, and &lt;id&gt; are returned from the previous call. Note that &lt;id&gt; and &lt;userId&gt; returned from the previous call aren't the same and aren't interchangeable. Make sure you use &lt;id&gt;.

    **Request**

    ```
    PATCH 
    https://graph.microsoft.com/beta/teams/<group_id>/channels/<channel_id>/members/<id>
      
    {
    "@odata.type": "#microsoft.graph.aadUserConversationMember",
    "roles": ["owner"]
    }
    ```

    **Response**

    ```
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

## Teams Powershell module

### Install the latest Teams PowerShell module from the PowerShell Test Gallery

The latest publicly available version of the Teams PowerShell module (currently [1.0.2](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2)) doesn't support managing private channels. Use these steps to install the latest version of the Teams PowerShell module with private channel support (currently 1.0.18) from the PowerShell Test Gallery.

> [!NOTE]
> Don't install the Teams PowerShell module from the PowerShell Test Gallery side-by-side with a version of the module from the public PowerShell Gallery. Follow these steps to first uninstall the Teams PowerShell module from the public PowerShell Gallery, and then install the latest version of the module from the PowerShell Test Gallery.

1. Close all existing PowerShell sessions.
2. Start a new instance of the Windows PowerShell module.
3. Run the following to uninstall the Teams PowerShell module from the public PowerShell Gallery:

    ```
    Uninstall-Module -Name MicrosoftTeams
    ```

4. Close all existing PowerShell sessions.
5. Start the Windows PowerShell module again, and then run the following to register the PowerShell Test Gallery as a trusted source:

    ```
    Register-PSRepository -Name PSGalleryInt -SourceLocation https://www.poshtestgallery.com/ -InstallationPolicy Trusted
    ```

6. Run the following to install the latest Teams PowerShell module from the PowerShell Test Gallery:

    ```
    Install-Module -Name MicrosoftTeams -Repository PSGalleryInt -Force
    ```

7. Run the following to verify that the latest version of the Teams PowerShell module from the PowerShell Test Gallery is successfully installed:

    ```
    Get-Module -Name MicrosoftTeams
    ```

#### Update to the latest version of the Teams PowerShell module from the PowerShell Test Gallery

If you already installed the Teams PowerShell module from the PowerShell Test Gallery, use the following steps to update to the latest version.

1. Close all existing PowerShell sessions.
2. Start a new instance of the Windows PowerShell module.
3. Run the following to update the currently installed version of the Teams PowerShell module from the PowerShell Test Gallery:

    ```
    Update-Module -Name MicrosoftTeams -Force
    ```

4. Run the following to verify that the latest version of the Teams PowerShell module from the PowerShell Test Gallery is successfully installed:

    ```
    Get-Module -Name MicrosoftTeams
    ```

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
- [Use the Microsoft Graph API to work with Teams](https://docs.microsoft.com/graph/api/resources/teams-api-overview?view=graph-rest-1.0)
    - [List channels](https://docs.microsoft.com/graph/api/channel-list)
    - [Create channel](https://docs.microsoft.com/graph/api/channel-post)
    - [Add member to channel](https://docs.microsoft.com/graph/api/conversationmember-add)
    - [Update member in channel](https://docs.microsoft.com/graph/api/conversationmember-update)
    - [Remove member from channel](https://docs.microsoft.com/graph/api/conversationmember-delete)