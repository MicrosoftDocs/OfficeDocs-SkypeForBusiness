---
title: Manage messaging policies in Teams
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.reviewer: jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-collaboration
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.messagingpolicies.overview
  - seo-marvel-apr2020
description: "Learn about Messaging policies and how they can be used to control chat messaging in Teams."
---

# Manage messaging policies in Teams

<!--- Add zone marker here--->

Messaging policies are used to control which chat and channel messaging features are available to [users (owners and members)](assign-roles-permissions.md) in Microsoft Teams. You can use the global (Org-wide default) policy that's created automatically or create and assign custom messaging policies.

Users in your organization will automatically get the global policy, unless you create and assign a custom policy. Edit the settings in the global policy or create and assign one or more custom policies to turn on or turn off the features that you want.

> [!NOTE]
> To ensure syncing after a policy change, a reboot may be necessary for certain instances. 

## Create a custom messaging policy

1. In the left navigation of the Microsoft Teams admin center, go to **Messaging policies**.
2. Select **Add**.
3. Enter a name and description for the policy.
4. Choose the settings that you want.
5. Select **Save**.

For example, you want to make sure that sent messages aren't deleted or altered. Create a new custom policy named "Retain sent messages" and turn off the following settings:

- Owners can delete sent messages
- Users can delete sent messages
- Users can edit sent messages

Then assign the policy to users.

## Edit a messaging policy

You can edit the global policy and any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Messaging policies**.
2. Select the policy by clicking to the left of the policy name, and then select **Edit**.
3. From here, make the changes that you want.
4. Select **Save**.

## Assign a custom messaging policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

A user can only be assigned one messaging policy at a time.

> [!NOTE]
> You can't delete a policy if users are assigned to it. You must first assign a different policy to all affected users, and then you can delete the original policy.

<!--- End zone marker here--->

## Messaging policy settings

Here are the messaging policy settings that you can configure.

- **Owners can delete sent messages**  Use this setting to let owners delete channel messages or posts that users sent.
- **Delete sent messages** Use this setting to let users delete messages that they sent in chat.
- **Edit sent messages** Use this setting to let users edit the messages that they sent in chat.
- **Read receipts** Read receipts allow the sender of a chat message to be notified when their message was read by the recipient in 1:1 and group chats 20 people or fewer. Message read receipts remove uncertainty about whether a message was read, and improve team communication. Read receipts aren't captured in eDiscovery reporting.  
    - **User controlled** This means that users get to decide if they want read receipts ON or OFF. Default setting within the app is ON. Users can then turn it OFF.
    - **Turned on for everyone** This means everyone in the tenant will have the feature ON with no option to turn it off. When using the **On for everyone** setting, the only way to set receipts for the whole tenant is either to have only one messaging policy for the whole tenant (the default policy named "Global (Org-wide Default)") or to have all messaging policies in the tenant use the same settings for receipts. The read receipts feature is most effective when the feature is enabled to **On for everyone**.
    - **Turned off for everyone** This means the feature is disabled and no one in the tenant has read receipts nor can they turn it on.
<a name="bkchat"> </a>

- **Chat**  Turn this setting on if you want users in your organization to be able to use the Teams app to chat with other people.
- *Use Giphy in conversations**  If you turn on Giphys, users can include Giphys in chat conversations with other people. Giphy is an online database and search engine that allows users to search for and share animated GIF files. Each Giphy is assigned a content rating. In addition to turning on this setting, you need to enable [Optional Connected Experiences](/deployoffice/privacy/manage-privacy-controls#policy-setting-for-optional-connected-experiences) to allow Giphys in conversations.
- **Giphy content rating**
  - **No restriction** This means that your users will be able to insert any Giphy in chats regardless of the content rating.
  - **Moderate**  This means that your users will be able to insert Giphys in chats, but will be moderately restricted from adult content.
  - **Strict**  This means that your users will be able to insert Giphys in chats, but will be strictly restricted from adult content.
- **Memes in conversations** If you turn Memes on, users can include Memes in chat conversations with other people.
- **Stickers in conversations** If you turn this on, users can include Stickers in chat conversations with other people.
- **URL previews** Use this setting to turn automatic URL previewing on or off in messages.
- **Translate messages** Turn this setting on to let users automatically translate Teams messages into the language specified by their personal language settings for Microsoft 365 or Office 365.
- **Immersive reader for messages** Turn this setting on to let users view messages in Microsoft Immersive Reader. Immersive Reader is a learning tool that provides a full screen reading experience to increase readability of text.
- **Send urgent messages using priority notifications** If you turn this on, users can send messages using [priority notifications](https://support.microsoft.com/article/mark-a-message-as-important-or-urgent-in-teams-ea99d5b6-1317-4550-8d75-86ff14cd4462). Priority notifications notify users every 2 minutes for 20 minutes or until messages that are marked as *urgent* are picked up and read by the recipient. This feature increases the likelihood that the message is acted upon in a timely manner. You can't edit an urgent message after you send it.
- **Create voice messages**
  > [!Important]
  > Audio messages are not captured in eDiscovery reporting.
  - **Allowed in chats and channels** This means that users can leave audio messages in both chats and channels.
  - **Allowed in chats only** This means that users can leave audio messages in chats, but not in channels.
  - **Not enabled** This means that users cannot create audio messages in chats or channels.  
- **On mobile devices, display favorite channels above recent chats** Enable this setting to move favorite channels to the top of the mobile device screen so that a user doesn't need to scroll to find them.
- **Remove users from group chats** Turn this setting on to let a user remove other users from a group chat. This feature lets you continue a chat with a smaller group of people without losing the chat history.
- **Text predictions** Turn on this setting to let a user get text predictions for chat messages.
- **Suggested replies**  Turn this setting on to enable suggested replies for chat messages.
- **Chat permission role** Use this setting to define the supervised chat role of the user. Learn more about [supervised chat](supervise-chats-edu.md).
- **Users with full chat permissions can delete any message** Use this setting to let users with full permissions delete any group or meeting chat message.

> [!NOTE]
> Some of these settings, such using Giphys, can also be configured at the team level by team owners and at the private or shared channel level by channel owners.

### Related topics

- [Assign policies to users and groups in Teams](assign-policies-users-and-groups.md)
- [Assign team owners and members in Microsoft Teams](assign-roles-permissions.md)
