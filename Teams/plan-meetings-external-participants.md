---
title: Plan for meetings with external participants in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: rafarrbronisevsky, alsolom
audience: admin
search.appverid: MET150
ms.localizationpriority: normal
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

You can allow people from outside your organization to join Teams meetings that are hosted by your organization. This article describes the options available for meeting with people outside your organization, which types of external meeting participants can be validated, and which Teams and Microsoft 365 features are used to control their access to meetings in your organization.

## Meeting with validated external participants

How external participants appear in meetings depends on a combination of your Microsoft 365 configuration and their identity provider. Some external participants can be validated by Microsoft 365 and others are considered anonymous.

A *validated* meeting participant is one that is logged in to Microsoft 365 in way that you trust. There are two types of validated external participants:

- **Guests** - people who have an [Azure AD B2B collaboration guest account](/azure/active-directory/external-identities/what-is-b2b) in your directory
- **People from trusted organizations** - people in other Microsoft 365 organizations with which you have configured a two-way trust relationship in [external access](trusted-organizations-external-meetings-chat.md) and who have the required user permissions

External participants who are not validated in one of these two ways are considered *anonymous*.

When planning your configuration for external meetings, consider the types of meetings where you want all participants to be validated and which can allow anonymous participants. You might want all confidential meetings to have only validated participants, whereas there may be marketing or sales meetings where anonymous participants are fine.

The external participant's identity provider determines which type of verified account they would use. People in other Microsoft 365 organizations can join meetings through the external access feature. People who don't have a work or school account in Microsoft 365 must be invited as guests to your organization and can join meetings using guest access.

#### External participants and the Teams meeting lobby

The Teams meeting lobby is a waiting area for meeting participants. Meeting organizers can use the lobby to vet participants before allowing them to join the meeting. Depending on its configuration, certain types of participants - including external participants - can be required to wait in the lobby until they're admitted by an organizer, co-organizer, or presenter.

The lobby can be configured by the meeting organizer or administrators can enforce lobby settings by using meeting templates or sensitivity labels. For details, see [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md) and [Configure the Microsoft Teams meeting lobby for sensitive meetings](configure-lobby-sensitive-meetings.md).

## Meetings with other Microsoft 365 organizations

To have meetings with validated participants in other Microsoft 365 organizations, you must add that organization as a trusted organization in external access. Meeting organizers in your organization and meeting participants from the other organization must be assigned an external access policy that allows them to communicate with external Teams and Skype for Business users.

Note that meeting participants who don't have the correct external access permissions will be considered anonymous when they join meetings.

For information on how to configure external access, see [Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md).

## Meetings with non-Microsoft 365 organizations

Individuals and organizations that don't use Microsoft 365 must be added to your organization's directory as guests in order to be validated meeting participants.

[Guest access in Teams](guest-access.md) must be enabled in order for guests to be able to join meetings. Your users can invite guests to their teams, or you can [add them directly in the Azure AD portal](/azure/active-directory/external-identities/add-users-administrator).

Guests must log in to Teams with their guest account in order to join meetings. If they're not logged in, they may be considered anonymous.

## Meetings with anonymous participants

Any participant attempting to join a Teams meeting who can't be validated will be considered anonymous. Anonymous meeting access is turned on by default. If your compliance requirements or business rules require you to validate all meeting participants, you can turn anonymous access off for certain meeting organizers or for everyone.

For details about configuring anonymous meeting access, see [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md).

## Dial-in users

External participants can dial in to Teams meetings using the conference number provided in the meeting invite. By default, people dialing in must wait in the lobby. Meeting organizers can change this setting, or you can enforce it by using a meeting template.

## Related topics

[Use guest access and external access to collaborate with people outside your organization](communicate-with-users-from-other-organizations.md)
