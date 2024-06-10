---
ms.date: 07/01/2023
title: Plan for meetings with external participants in Microsoft Teams
ms.author: jtremper
author: jacktremper
manager: pamgreen
ms.topic: conceptual
ms.service: msteams
ms.reviewer: alsolom
audience: admin
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.orgwidesettings.guestaccess.overview
  - chat-teams-channels-revamp
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
appliesto: 
  - Microsoft Teams
description: Learn how to plan for meetings with people outside your organization in Microsoft Teams.
---

# Plan for meetings with external participants in Microsoft Teams

You can allow people from outside your organization to join Teams meetings that are hosted by users in your organization. This article describes the options available for hosting meetings with people outside your organization, which types of external meeting participants can be verified, and which Teams features are used to control their access to meetings.

How external participants can attend meetings depends on a combination of your Teams admin configuration and their identity provider. Some external participants can be verified by Teams and others are considered anonymous.

There are three types of external participants who can attend meetings hosted by your organization:

- **Guests** - people who are logged in to Teams in your organization using a guest account. Guests appear with "(Guest)" appended to their name in meetings.
- **People from trusted organizations** - people who are logged in to Teams in other Microsoft 365 organizations that you have a mutual trust relationship with. People from trusted organizations appear with "(External)" appended to their name in meetings.
- **Anonymous** - people whose identity can't be verified. They may be logged in to an organization without a mutual trust relationship or they may not have an account. Anonymous participants appear with "(Unverified)" appended to their name in meetings.

## Meeting with verified external participants

A *verified* external meeting participant is one that is logged in to Teams in Microsoft 365 in way that you trust. There are two types of verified external meeting participants:

- **Guests** - people who are logged in to Teams with a [guest account](guest-access.md) in your directory. Guests can be anyone with an email address, including people from other Microsoft 365 organizations.
- **People from trusted organizations** - people in other Microsoft 365 organizations with which you have configured a trust relationship in [external access](trusted-organizations-external-meetings-chat.md) and who have the required user-level external access permissions

External participants who aren't verified in one of these two ways are considered *[anonymous](#meetings-with-anonymous-participants)*.

People who don't have a work or school account in Microsoft 365 must be invited as guests to your organization and can join meetings using guest access. People in other Microsoft 365 organizations can join meetings through the external access feature. (They can also join as guests if they have guest accounts.)

When planning your configuration for external meetings, consider the types of meetings where you want all participants to be verified and which can allow anonymous participants. You might want all confidential meetings to have only verified participants, whereas there may be marketing or sales meetings where anonymous participants are fine.

### Meetings with non-Microsoft 365 organizations

When meeting with people from non-Microsoft 365 organizations, you must add each individual who you want to meet with to your organization's directory as guests in order for them to be verified meeting participants.

[Guest access in Teams must be enabled](/microsoft-365/solutions/collaborate-as-team) in order for guests to be able to join meetings. Your users can invite guests to their teams (which will add them to the directory), or you can [add them directly in the Microsoft Entra admin center](/azure/active-directory/external-identities/add-users-administrator).

Guests must log in to Teams with their guest account in order to join meetings. If they're not logged in, they will be considered anonymous.

### Meetings with other Microsoft 365 organizations

To have meetings with verified participants in other Microsoft 365 organizations, you can either use guest access as described above, or you can use the external access feature in Teams. For more information about the differences between guest access and external access, see [Use guest access and external access to collaborate with people outside your organization](communicate-with-users-from-other-organizations.md).

In external access, you define which Microsoft 365 organizations you want to trust and which users in your organization you want to allow to host meetings with them. The other organization must similarly configure external access to trust your organization and to allow their users to communicate with external Teams and Skype for Business users.

Note that meeting participants from other organizations who don't have the correct external access permissions will be considered anonymous when they join meetings.

Similarly, if a meeting organizer in your organization doesn't have external access permissions, all external participants joining their meetings will be considered anonymous unless they're logged in with a guest account.

If [anonymous meeting join](anonymous-users-in-meetings.md) is turned off, anonymous participants won't be able to join meetings at all.

For information on how to configure external access, see [Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md).

### Meetings with Microsoft 365 organizations in other clouds

Cross-cloud meetings are supported as follows:

|Meet with:|Commercial|GCC|GCC High|DoD|China|
|:---------|:--------:|:-:|:------:|:-:|:---:|
|Commercial|          |✔️|✔️      |✔️ |✔️  |  
|GCC       |✔️       |   |✔️      |✔️ |✔️  |  
|GCC High  |✔️       |✔️|         |✔️ |     |  
|DoD       |✔️       |✔️|✔️      |    |     |  
|China     |✔️       |✔️|         |    |     |  

[Meet with people in other Microsoft 365 clouds](cross-cloud-meetings.md)

## Meetings with anonymous participants

Any participant attempting to join a Teams meeting who can't be verified will be considered anonymous. Anonymous meeting access is turned on by default. If your compliance requirements or business rules require that all meeting participants be verified, you can turn anonymous access off for certain meeting organizers or for everyone.

For details about configuring anonymous meeting access, see [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md) and [Manage chat in Teams meetings](manage-meeting-chat.md).

## Dial-in users

External participants can dial in to Teams meetings using the conference number provided in the meeting invite. By default, people dialing in must wait in the lobby. Meeting organizers can change this setting, or you can enforce it by using a [meeting template](custom-meeting-templates-overview.md).

## External participants and the Teams meeting lobby

The Teams meeting lobby is a waiting area for meeting participants. Meeting organizers can use the lobby to vet participants before allowing them to join the meeting. Depending on its configuration, certain types of participants can be required to wait in the lobby until they're admitted by an organizer, co-organizer, or presenter. The lobby includes options for guests, people from trusted organizations, and anonymous participants.

The lobby can be configured by the meeting organizer before or during the meeting, or administrators can enforce lobby settings by using meeting templates or sensitivity labels. For details, see [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md) and [Configure the Microsoft Teams meeting lobby for sensitive meetings](configure-lobby-sensitive-meetings.md).

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[External participants receive "Sign in to Teams to join, or contact the meeting organizer"](/microsoftteams/troubleshoot/meetings/external-participants-join-meeting-blocked)
