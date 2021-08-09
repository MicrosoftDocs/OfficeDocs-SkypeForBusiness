---
title: Use guest access and external access to collaborate with people outside your organization
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: vinbel, luises
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-externalcollab
search.appverid: MET150
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
localization_priority: Priority
description: Learn how to call, chat, find, and add users from outside the organization in Microsoft Teams using external access (federation) and guest access.
---

# Use guest access and external access to collaborate with people outside your organization

When you need to communicate and collaborate with people outside your organization, Microsoft Teams has two options:

- **External access** - A type of federation that allows users to find, call, and chat with people in other organizations. These people cannot be added to teams unless they are invited as guests.
- **Guest access** - Guest access allows you to invite people from outside your organization to join a team. Invited people get a guest account in Azure Active Directory.

Note that Teams allows you to invite people outside your organization to meetings. This does not require external or guest access to be configured.

## External access (federation)

Set up external access if you need to find, call, chat, and set up meetings with people outside your organization who use Teams, Skype for Business (online or on premises) or Skype. 

By default, external access is enabled for all domains. You can restrict external access by allowing or blocking specific domains or by turning it off.

![Screenshot of external access settings](media/external-access-federation-settings.png)

To configure external access, see [Manage external access](manage-external-access.md). 

>[!NOTE]
>Microsoft Teams free licenses do not support external access.

## Guest access

Use guest access to add a person from outside your organization to a team, where they can chat, call, meet, and collaborate on files. A guest can be given nearly all the same Teams capabilities as a native team member.

Guests are added to your organization's Azure Active Directory as B2B users and must sign in to Teams using their guest account. This means that they may have to sign out of their own organization to sign in to your organization.

To configure guest access for Teams, see [Collaborate with guests in a team](/microsoft-365/solutions/collaborate-as-team).

## Compare external and guest access

The following tables show the differences between using external access (federation) and guests. In both cases, people outside your organization are identified to your users as being external.

### Things your users can do

| Users can | External access users | Guests |
|---------|-----------------------|--------------------|
| Chat with someone in another organization | Yes | Yes |
| Call someone in another organization | Yes | Yes |
| See if someone from another organization is available for call or chat | Yes | Yes<sup>1</sup> |
| Search for people in other organizations | Yes<sup>2</sup> | No |
| Share files | No | Yes |
| See the out-of-office message of someone in another organization | No | Yes |
| Block someone in another organization  | No | Yes |
| Use @mentions | Yes<sup>3</sup> | Yes |

### Things people outside your organization can do

| People outside your organization can | External access users | Guests |
|---------|-----------------------|--------------------|
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
| Use memes in conversation | Yes<sup>3</sup> | Yes<sup>5</sup> |
| Use stickers in conversation | Yes<sup>3</sup> | Yes<sup>5</sup> |
| Presence is displayed | Yes | Yes |
| Use @mentions | Yes<sup>3</sup> | Yes |

<br>

<sup>1</sup> Provided that the user has been added as a guest and is signed with the guest account.<br>
<sup>2</sup> Only by email or Session Initiation Protocol (SIP) address.<br>
<sup>3</sup> Supported for 1:1 chat for Teams Only to Teams Only users from two different organizations. <br>
<sup>4</sup> By default, external participants can't see the phone numbers of dialed-in participants. If you want to maintain the privacy of these phone numbers, select **Tones** for **Entry/exit announcement type** (this prevents the numbers from being read out by Teams). To learn more, read [Turn on or off entry and exit announcements for meetings in Microsoft Teams](turn-on-or-off-entry-and-exit-announcements-for-meetings-in-teams.md). <br>
<sup>5</sup> Allowed by default, but can be turned off by the Teams admin

## Related topics

[External access in Teams](manage-external-access.md)

[Guest access in Teams](guest-access.md)
