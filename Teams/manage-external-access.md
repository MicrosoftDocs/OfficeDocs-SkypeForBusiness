---
title: Manage external access (federation) in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 12/10/2018
ms.topic: article
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
ms.reviewer: karvell
search.appverid: MET150
description: Your IT admin can configure external access for other domains (federation) to let users from those domains participate in Teams. 
appliesto: 
- Microsoft Teams
---

Manage external access (federation) in Microsoft Teams
======================================================

With Microsoft Teams external access, users from other domains can participate in your chats and channels. You can also allow external users who are still using Skype for Business to participate. External access differs from guest access in that an entire domain is given access permission, not an individual. See the following table for a comparison of external and guest access features.

| Feature | External access users | Guest access users |
|=========|=======================|====================|
| User can chat with someone in another company | Yes |Yes |
| User can call someone in another company | Yes | Yes |
| User can see if someone from another company is available for call or chat | Yes | Yes |
| User can search for users across external tenants | Yes<sup>1</sup> | No |
| User can share files | No | Yes |
| User can be added to a group chat | No | Yes |
| User can be added to a meeting | Yes | Yes |
| Additional users can be added to a chat with an external user | No | N/A |
| User is identified as an external party | Yes | Yes |
| Presence is displayed | Yes | Yes |
| Out of office message is shown | | |
| Individual user can be blocked | No | Yes |
| @mentions are supported | No | Yes |

<sup>1</sup> Only by email of Session Initiation Protocol (SIP) address.

## Turn on or turn off external access

You can use the Microsoft Teams & Skype for Business Admin Center to manage external access.

1. In the Microsoft Teams & Skype for Business Admin Center, select **Org-wide settings** > **External access**.

     ![Screenshot of Org-wide settings external access](media/manage-external-access-1.png).

2. Toggle the **External access** switch to **On** or **Off**.

     ![Screenshot of external access switch turned On](media/manage-external-access-2.png).

3. Click **Save**. 

## Add or block a domain

Follow these steps to add a domain or turn off external access for a domain.

1. In the Microsoft Teams & Skype for Business Admin Center, select **Org-wide settings** > **External access**.

2. Select **Add a domain**. 
 
    ![Screenshot of External access page with add a domain link](media/manage-external-access-3.png).

   The **Add a domain pane** appears.

    ![Screenshot of Add a domain pane](media/manage-external-access-4.png).


3. Under **Add a domain**, type the name of the domain; for example, type Contoso.com.

4. Select **Allowed** or **Blocked**. You can change this setting at any time.

2. Select **Done**.

After you add a domain, you will see the domain name and status added to the list of domains on the External access page.

## More information

For information about guest access in Microsoft Teams, see [Manage guest access in Microsoft Teams](manage-guests.md).