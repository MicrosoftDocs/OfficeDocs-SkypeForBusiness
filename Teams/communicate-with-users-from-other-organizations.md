---
title: Call and chat with users from other organizations
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: vinbel
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
description: Learn how to call, chat, find and add users from outside the organization in Microsoft Teams using federation and guest access.
---

# Call, chat, and collaborate with people outside your organization in Microsoft Teams

When you need to communicate and collaborate with people outside your organization, Microsoft Teams has the following options:

- **Federation** - Federation - also know as *external access* - allows users to find, call, and chat with people in other organizations. Federated users cannot be added to teams unless they are invited as guests.
- **Guest access** - Guest access allows you to invite people from outside your organization to join a team. Invited people get a guest account in Azure Active Directory.
- **Anonymous access** - Anonymous access is available only in Teams meetings and allows people to join meetings without signing in.


| User is identified as an external party | Yes | Yes |



## External access

Use federation when you need to find, call, chat, and set up meetings with people outside your organization who use Teams, Skype for Business (online or on premises) or Skype. 

Federation is configured using the Teams external access settings. By default, federation is enabled. You can restrict federation by allowing or blocking specific domains or by turning it off.

![Screenshot of external access settings](media/external-access-federation-settings.png)


To configure federation, see [Manage external access](manage-external-access.md). 


## Guest access

Use guest access to add an individual user (regardless of domain) to a team, where they can chat, call, meet, and collaborate files. A guest user can be given nearly all the same Teams capabilities as a native team member.

- Guests are added to your organization’s Active Directory.
- To communicate with a guest, the guest has to be signed in to Teams using their guest account. This means that a guest may have to sign out of their own Teams account to sign in to your Teams account, or switch organizations if it's the same account.
- Guest users have access to more resources in Teams - such as files, teams, and channels - than external-access (federated) users.
- The Teams admin controls everything that a guest can (or can’t) do in the Teams admin center. To learn more, read [Manage guest access](manage-guests.md).

If you're ready to turn on guest access in your organization, start with the [Collaborate with guests in a team](https://docs.microsoft.com/microsoft-365/solutions/collaborate-as-team).

To configure guest access for Teams, see [Collaborate with guests in a team](https://docs.microsoft.com/microsoft-365/solutions/collaborate-as-team).

## Compare external and guest access



## Things your users can do

| Users can | Federation | Guests |
|---------|-----------------------|--------------------|
| Chat with someone in another organization | Yes |Yes |
| Call someone in another organization | Yes | Yes |
| See if someone from another organization is available for call or chat | Yes | Yes<sup>1</sup> |
| Search for people in other organizations | Yes<sup>2</sup> | No |
| Share files | No | Yes |
| See the out of office message of | No | Yes |
| Block someone in another organization someone in another organization | No | Yes |
| Use @mentions | Yes<sup>4</sup> | Yes |
||||

## Things people outside your organization can do

| People outside your organization can | Federation | Guests |
|---------|-----------------------|--------------------|
| Access Teams resources | No | Yes |
| Be added to a group chat | No | Yes |
| Be invited to a meeting | Yes | Yes |
| Make private calls | Yes | Yes |
| View the phone number for dial-in meeting participants | No<sup>5</sup> | Yes |
| Use IP video | Yes | Yes |
| Use screen sharing mode | Yes<sup>4</sup> | Yes |
| Use meet now | No | Yes |
| Edit sent messages | Yes<sup>4</sup> | Yes |
| Delete sent messages | Yes<sup>4</sup> | Yes |
| Use Giphy in conversation | Yes<sup>4</sup> | Yes |
| Use memes in conversation | Yes<sup>4</sup> | Yes |
| Use stickers in conversation | Yes<sup>4</sup> | Yes |
| Presence is displayed | Yes | Yes |
| Additional users can be added to a chat with an external user | No<sup>3</sup> | N/A |
| Use @mentions | Yes<sup>4</sup> | Yes |


<sup>1</sup> Provided that the user has been added as a guest and is signed in as a guest to the guest tenant.<br>
<sup>2</sup> Only by email or Session Initiation Protocol (SIP) address.<br>
<sup>3</sup> External (federated) chat is 1:1 only.<br>
<sup>4</sup> Supported for 1:1 chat for Teams Only to Teams Only users from two different organizations. <br>
<sup>5</sup> By default, external participants can't see the phone numbers of dialed-in participants. If you want to maintain the privacy of these phone numbers, select **Tones** for **Entry/exit announcement type** (this prevents the numbers from being read out by Teams). To learn more, read [Turn on or off entry and exit announcements for meetings in Microsoft Teams](turn-on-or-off-entry-and-exit-announcements-for-meetings-in-teams.md).


| Feature | Federation | Guests |
|---------|-----------------------|--------------------|
| User can chat with someone in another organization | Yes |Yes |
| User can call someone in another organization | Yes | Yes |
| User can see if someone from another organization is available for call or chat | Yes | Yes<sup>1</sup> |
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

## Related topics

[External access in Teams](manage-external-access.md)

[Guest access in Teams](guest-access.md)

