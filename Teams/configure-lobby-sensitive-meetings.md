---
title: Configure the Microsoft Teams meeting lobby for sensitive meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 05/19/2023
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
  - highpri
  - Tier1
appliesto: 
  - Microsoft Teams
description: Learn how to configure the Teams meeting lobby to enhance security for sensitive meetings by using admin policies, sensitivity labels, and meeting templates.
---

# Configure the Microsoft Teams meeting lobby for sensitive meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

The meeting lobby is a tool that you can use to ensure that inappropriate people are not admitted to meetings. By holding different types of participants in the lobby, meeting organizers can vet them and make sure it's appropriate for them to attend the meeting.

By default, people in your organization and [guests](guest-access.md) are admitted to meetings directly and participants from trusted domains and anonymous participants must wait in the lobby to be admitted by a meeting organizer. Meeting organizers can change this default setting for each meeting they create.

The lobby and other related settings can be controlled by the Teams Administrator by using meeting policies, meeting templates, and sensitivity labels to customize the experience for different users and different types of meetings.

The following table lists features that you can use to help manage the lobby experience for your organization and where to configure them.

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|Announce when dial-in callers join or leave|No|No|Yes|Yes|
|Anonymous users and dial-in callers can start a meeting|Yes|No|No|No|
|Anonymous users can join a meeting|Yes|No|No|No|
|People dialing in can bypass the lobby|Yes|Yes|Yes|Yes|
|Who can bypass the lobby|Yes|Yes|Yes|Yes|

For information about how to use templates and sensitivity labels to configure meeting settings, see [Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md) and [Use sensitivity labels to protect calendar items, Teams meetings, and chat](/microsoft-365/compliance/sensitivity-labels-meetings).

> [!Note]
> Meeting settings in sensitivity labels and custom meeting templates require Teams Premium.

## Lobby settings for different types of meetings

The following settings are available for **Who can bypass the lobby**:

- Everyone
- People in my org, trusted orgs, and guests
- People in my org and guests
- People in my org
- People who were invited
- Only organizers and co-organizers

An additional setting, **People dialing in can bypass the lobby**, controls if people calling in by phone can bypass the lobby.

While the meeting organizer normally chooses which setting to use for each meeting, you can enforce a particular setting using either a meeting template or a sensitivity label.

If your organization requires that certain types of meetings not be attended by people outside the organization, consider a meeting template that only allows people in your organization to bypass the lobby. This ensures that people outside the organization who were accidentally invited or sent a meeting link can't join the meeting directly.

If your organization has meetings where highly sensitive information is shared and you need to be sure that only certain people attend, consider using a meeting template or sensitivity label that only allows meeting organizers to bypass the lobby. This ensures that organizers can vet each incoming participant to make sure they should be in the meeting. This also prevents the meeting from starting until an organizer joins.

For sensitive meetings in general, consider using the **People who were invited** option. This ensures that people who don't have a meeting invite (included forwarded invites) go through the lobby. (The meeting organizer can also prevent forwarding when they create the meeting.)

For more information about the meeting lobby, see [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md).

For information about using meeting templates and sensitivity labels together, see [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md).

### Attendees calling in by phone

By default, attendees who are dialing in by phone go through the lobby. Administrators can change this default with the **People dialing in can bypass the lobby** admin meeting policy. If you want to enforce this setting to be on or off, you must use a meeting template or sensitivity label.

If there are circumstances where you want to allow callers to bypass the lobby, meeting organizers can control this setting, or you can enforce it through a meeting template or sensitivity label.

#### Join and leave notifications

Meeting organizers have the option of having attendees calling in by phone announced when they join or leave a meeting. If you want to ensure that phone attendees are announced for certain types of meetings, you can enforce this setting with a meeting template.

## Meeting with anonymous participants

Unless you allow everyone to bypass the lobby, anonymous participants must go through the lobby to attend the meeting. Meeting organizers can then decide if these participants should be admitted.

If your organization does not allow anonymous participants to join meetings at all, you can turn off the **Anonymous users can join a meeting** setting in the Teams admin center. For more information, see [Manage meeting settings in Microsoft Teams](/microsoftteams/meeting-settings-in-teams).

If you have certain groups in your organization - such as marketing - who need to organize meetings with anonymous participants and others - such as research - who should not, you can use Teams meeting policies to configure anonymous meeting join for different groups. (You'll need to turn the **Anonymous users can join a meeting** setting mentioned above on for this to work.) For details, see [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md).

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Manage external meetings and chat in Microsoft Teams](/microsoftteams/manage-external-access)
