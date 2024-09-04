---
title: Use guest access and external access to collaborate with people outside your organization
ms.author: jtremper
author: jacktremper
manager: jtremper
ms.reviewer: majaisin
ms.date: 06/28/2024
ms.topic: concept-article
ms.service: msteams
audience: admin
ms.custom: chat-teams-channels-revamp
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-externalcollab
- Tier2
- essentials-manage
search.appverid: MET150
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: Medium
description: Learn how to call, chat, find, and add users from outside the organization in Microsoft Teams using external access and guest access.
---

# Use guest access and external access to collaborate with people outside your organization

This article describes two of the options for collaborating with people outside your organization:

- **External access** - A feature that allows users to find, call, and chat with people who have Microsoft identities, including those from other organizations.
- **Guest access** - A feature that allows you to invite people from outside your organization to join a team. Guests can also call, chat, and meet with people in your organization and you can share files and folders with them. Invited people get an [Microsoft Entra B2B collaboration guest account](/azure/active-directory/external-identities/what-is-b2b) in your directory.

For a complete overview of the external collaboration options in Microsoft 365, see [Overview of external collaboration options in Microsoft 365](/microsoft-365/enterprise/external-guest-access).

## External access

Set up external access if you need to find, call, chat, and set up meetings with people outside your organization who use Teams, Skype for Business Server, or Skype. By default, external access is enabled.

To configure external access, see [Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md).

For information about cross-cloud external access, such as between commercial and GCC, see [Microsoft Teams chat experience when communicating with people outside the organization](native-chat-for-external-users.md).

#### Teams and Skype for Business users in external organizations

For external access with other Microsoft 365 organizations you allow all domains (the default) or you can restrict external access by allowing or blocking specific domains, by blocking all domains (which turns external access off) or by limiting which users can use external access.

#### Teams accounts not managed by an organization

You can control whether users in your organization can communicate with Teams users who are not managed by an organization by turning external access on or off at the organization level or by using a policy to control it for individual users and groups. You can also control if people with unmanaged Teams accounts can start a conversation with people in your organization.

#### Skype users

You can control whether users in your organization can communicate with Skype users by turning external access for Skype users on or off either for the entire organization  or by using a policy to control it for individual users and groups.

## Guest access

Use guest access to add a person from outside your organization to a team, where they can chat, call, meet, and collaborate on files. A guest can be given nearly all the same Teams capabilities as a native team member. For more information, see [Guest experience in Teams](guest-experience.md).

If you need to have meetings with people outside your organization who aren't part of another Microsoft 365 organization, you can use guest access to allow them to log in to your organization for meetings.

Guests are added to your organization's Microsoft Entra ID as B2B collaboration users. They must sign in to Teams using their guest account. If the normally use Teams with another Microsoft 365 organization, they need to switch organizations in Teams to interact with your organization.

Guest access is available between Microsoft 365 cloud environments (such as commercial and GCC) by using cross-cloud guest access. For more information, see [Collaborate with guests from other Microsoft 365 cloud environments](/microsoft-365/solutions/collaborate-guests-cross-cloud).

To configure guest access for Teams, see [Collaborate with guests in a team](/microsoft-365/solutions/collaborate-as-team).

## Compare external access and guest access

The following tables show the differences between using external access and guests.

#### Things your users can do when communicating with people outside the organization

| Your users can | External access users | Guests |
|:---------|:-----------------------|:--------------------|
| Chat with someone in another organization | Yes | Yes |
| Call someone in another organization | Yes | Yes |
| See if someone from another organization is available for call or chat | Yes | Yes<sup>1</sup> |
| Search for people in other organizations | Yes<sup>2</sup> | No |
| Share files | No | Yes |
| See the out-of-office message of someone in another organization | No | Yes |
| Block someone in another organization  | Yes | Yes |
| Use @mentions | Yes<sup>3</sup> | Yes |

#### Things people outside your organization can do

| People outside your organization can | External access users | Guests |
|:---------|:-----------------------|:--------------------|
| Access Teams resources | No | Yes |
| Be added to a group chat | Yes | Yes |
| Be invited to a meeting | Yes | Yes |
| Make private calls | Yes | Yes<sup>5</sup> |
| View the phone number for dial-in meeting participants | No<sup>4</sup> | Yes |
| Use IP video | Yes | Yes<sup>5</sup> |
| Use screen sharing | Yes<sup>3</sup> | Yes<sup>5</sup> |
| Use meet now | No | Yes<sup>5</sup> |
| Edit sent messages | Yes<sup>3</sup> | Yes<sup>5</sup> |
| Delete sent messages | Yes<sup>3</sup> | Yes<sup>5</sup> |
| Use Giphy in conversation | Yes<sup>3</sup> | Yes<sup>5</sup> |
| Use stickers and memes in conversation | Yes<sup>3</sup> | Yes<sup>5</sup> |
| Presence is displayed | Yes | Yes |
| Use @mentions | Yes<sup>3</sup> | Yes |

<br>

<sup>1</sup> Provided that the user has been added as a guest and is signed in with the guest account.<br>
<sup>2</sup> Only by email or Session Initiation Protocol (SIP) address.<br>
<sup>3</sup> Supported for 1:1 chat for Teams Only to Teams Only users from two different organizations. <br>
<sup>4</sup> By default, external participants can't see the phone numbers of dialed-in participants. If you want to maintain the privacy of these phone numbers, select **Tones** for **Entry/exit announcement type** (this prevents the numbers from being read out by Teams). To learn more, read [Turn on or off entry and exit announcements for meetings in Microsoft Teams](turn-on-or-off-entry-and-exit-announcements-for-meetings-in-teams.md). <br>
<sup>5</sup> Allowed by default, but can be turned off by the Teams admin


## Related topics

[Teams and Skype interoperability](teams-skype-interop.md)

[Set up secure file sharing and collaboration with Microsoft Teams](/microsoft-365/solutions/setup-secure-collaboration-with-teams)
