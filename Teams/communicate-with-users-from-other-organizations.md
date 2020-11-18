---
title: Call and chat with users from other organizations
author: serdars
ms.author: serdars
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-externalcollab
ms.reviewer: vinbel
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn how to call, chat, find and add users from outside the organization in Microsoft Teams using external access (federation) and guest access.
appliesto: 
- Microsoft Teams
localization_priority: Priority
---
Call and chat with users from other organizations in Microsoft Teams
======================================================

When you need to communicate and collaborate with people outside your organization, Microsoft Teams gives you two different ways to make that happen. The first – **external access** (federation) – lets  you find, call, and chat with users in other domains (for example, contoso.com). The second – **guest access** – lets you add individuals to your teams, as guests, using their email address. You can collaborate with guests as you would with any other users in your organization.

You can use both external access and guest access if you want - one doesn't preclude the other.

At a high level, here’s how to choose (for a detailed comparison, jump down to [Compare external and guest access](#compare-external-and-guest-access)):

## External access

Use **external access** (federation) when you need a solution that lets external users in other domains find, call, chat, and set up meetings with you. External users have no access to your organization's teams or team resources. Choose external access when you want to communicate with users outside your organization who are still on Skype for Business (online or on premises) or Skype (coming in early 2020). 

External access is turned on by default in Teams, which means your org can communicate with all external domains. The Teams admin can turn it off or specify which domains to include (or exclude). To learn more, read [Manage external access](manage-external-access.md). 

If you want external users to have access to teams and channels, [guest access](#guest-access) might be a better way to go. 


## Guest access

Use **guest access** to add an individual user (regardless of domain) to a team, where they can chat, call, meet, and collaborate on organization files (stored in SharePoint or OneDrive for Business), using Microsoft 365 or Office 365 apps such as Word, Excel, or PowerPoint. A guest user can be given nearly all the same Teams capabilities as a native team member. To learn more, read [Guest access in Teams](guest-access.md).

- Guests are added to your organization’s Active Directory.
- To communicate with a guest, the guest has to be signed in to Teams using their guest account. This means that a guest may have to sign out of their own Teams account to sign in to your Teams account, or switch organizations if it's the same account.
- Guest users have access to more resources in Teams - such as files, teams, and channels - than external-access (federated) users.
- The Teams admin controls everything that a guest can (or can’t) do in the Teams admin center. To learn more, read [Manage guest access](manage-guests.md).

If you're ready to turn on guest access in your organization, start with the [Collaborate with guests in a team](https://docs.microsoft.com/microsoft-365/solutions/collaborate-as-team).


## Compare external and guest access

| Feature | External access users | Guest access users |
|---------|-----------------------|--------------------|
| User can chat with someone in another company | Yes |Yes |
| User can call someone in another company | Yes | Yes |
| User can see if someone from another company is available for call or chat | Yes | Yes<sup>1</sup> |
| User can search for users across external tenants | Yes<sup>2</sup> | No |
| User can share files | No | Yes |
| User can access Teams resources | No | Yes |
| User can be added to a group chat | No | Yes |
| User can be invited to a meeting | Yes | Yes |
| Additional users can be added to a chat with an external user | No<sup>3</sup> | N/A |
| User is identified as an external party | Yes | Yes |
| Presence is displayed | Yes | Yes |
| Out of office message is shown | No | Yes |
| Individual user can be blocked | No | Yes |
| @mentions are supported | Yes<sup>4</sup> | Yes |
| Make private calls | Yes | Yes |
| View the phone number for dial-in meeting participants | No<sup>5</sup> | Yes |
| Allow IP video | Yes | Yes |
| Screen sharing mode | Yes<sup>4</sup> | Yes |
| Allow meet now | No | Yes |
| Edit sent messages | Yes<sup>4</sup> | Yes |
| Can delete sent messages | Yes<sup>4</sup> | Yes |
| Use Giphy in conversation | Yes<sup>4</sup> | Yes |
| Use memes in conversation | Yes<sup>4</sup> | Yes |
| Use stickers in conversation | Yes<sup>4</sup> | Yes |
||||

<sup>1</sup> Provided that the user has been added as a guest and is signed in as a guest to the guest tenant.<br>
<sup>2</sup> Only by email or Session Initiation Protocol (SIP) address.<br>
<sup>3</sup> External (federated) chat is 1:1 only.<br>
<sup>4</sup> Supported for 1:1 chat for Teams Only to Teams Only users from two different organizations. <br>
<sup>5</sup> By default, external participants can't see the phone numbers of dialed-in participants. If you want to maintain the privacy of these phone numbers, select **Tones** for **Entry/exit announcement type** (this prevents the numbers from being read out by Teams). To learn more, read [Turn on or off entry and exit announcements for meetings in Microsoft Teams](turn-on-or-off-entry-and-exit-announcements-for-meetings-in-teams.md).

## Related topics

[External access in Teams](manage-external-access.md)

[Guest access in Teams](guest-access.md)

