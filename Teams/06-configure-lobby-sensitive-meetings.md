---
title: Configure the Microsoft Teams meeting lobby for sensitive meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
audience: admin
ms.localizationpriority: high
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
appliesto: 
  - Microsoft Teams
description: 
---

# Configure the Microsoft Teams meeting lobby for sensitive meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

The meeting lobby is a tool that you can use to ensure that inappropriate people are not admitted to meetings. By holding different types of participants in the lobby, meeting organizers can vet incoming participants and make sure it's appropriate for them to attend the meeting.

By default, people in your organization and guests are admitted to meetings directly and participants from trusted domains and anonymous participants must wait in the lobby to be admitted by a meeting organizer. Meeting organizers can change this setting for each meeting they create.

The lobby and other related settings can be controlled by the Teams administrator by using meeting policies, meeting templates, and sensitivity labels to customize the experience for different users and different types of meetings.

The following table lists features that you can use to help manage the lobby experience for your organization and where to configure them.

|Setting|Meeting organizer|Template|Sensitivity label|Teams admin|
|:------|:----------------|:-------|:----------------|:----------|
|Who can bypass the lobby|&check;|&check;|&check;|&check;|
|People calling in by phone can bypass the lobby|&check;|&check;|&check;|&check;|
|Notify when callers join and leave|&check;|&check;|||
|Let anonymous people join a meeting||||&check;|
|Let anonymous people start a meeting||||&check;|
|Let anonymous people start a meeting||||&check;|


## Lobby settings for different types of meetings

The following settings are available for who can bypass the lobby:

- Everyone
- People in my organization, trusted organizations, and guests
- People in my organization and guests
- People in my organization
- Invited people
- Organizers

While the meeting organizer normally chooses which setting to use for each meeting, you can enforce a particular setting using either a meeting template or a sensitivity label.

If your organization requires that certain types of meetings not be attended by people outside the organization, consider a meeting template that only allows people in your organization to bypass the lobby. This ensures that people outside the organization who were accidentally invited or sent a meeting link can't join the meeting directly.

If your organization has meetings where highly sensitive information is shared and you need to be sure that only certain people attend, consider using a meeting template or sensitivity label that only allows meeting organizers to bypass the lobby. This ensures that organizers can vet each incoming participant to make sure they should be in the meeting.

For information about using meeting templates and sensitivity labels together, see [Use Teams custom meeting templates with sensitivity labels](/microsoftteams/meeting-templates-with-sensitivity-labels).


Allow dial-in users to bypass the lobby

Notify when callers join and leave (Template)

People calling in by phone can bypass the lobby (Template)



Set up trusted domains. [Manage external meetings and chat in Microsoft Teams](/microsoftteams/manage-external-access).

Who can bypass the lobby|**People in my organization, people in trusted domains, and guests**|**People I invite**|**Only me and co-organizers**|




This setting controls whether people who dial in by phone join the meeting directly or wait in the lobby regardless of the Automatically admit people setting. By default, this setting is turned off. When this setting is turned off, dial-in users will wait in the lobby until an organization user joins the meeting with a Teams client and admits them. When this setting is turned on, dial-in users will automatically join the meeting when an organization user joins the meeting with a Teams client.






Who can register (meetings) (Policy)



## Meeting with anonymous participants



Let anonymous people join a meeting (Policy & Setting)
Let anonymous people start a meeting (Policy)


Let anonymous people join a meeting
This per-organizer setting allows anyone to join meetings as an anonymous user by selecting the link in the meeting invitation. To learn more, see Join a meeting without a Teams account. Anonymous users' ability to join meetings are also controlled at your organization level, the more restrictive setting will be effective. To learn more, see Using the Microsoft Teams admin center to configure organization-wide policy.

Let anonymous people start a meeting
This setting is a per-organizer policy that allows for leaderless dial-in conferencing meetings. This setting controls whether dial-in users can join the meeting without an authenticated user from the organization in attendance. By default, this setting is turned off, which means dial-in users will wait in the lobby until an authenticated user from the organization joins the meeting.

 Note

If this setting is turned off and a dial-in user joins the meeting first and is placed in the lobby, an organization user must join the meeting with a Teams client to admit the user from the lobby. There are no lobby controls available for dialed in users.

