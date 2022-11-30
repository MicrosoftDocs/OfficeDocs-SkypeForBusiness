--- 
title: Control who can bypass the meeting lobby in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: rbronisevsky
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: Learn to use the meeting lobby in Microsoft Teams to allow only certain meeting participants to join the meeting directly
---

# Control who can bypass the meeting lobby in Microsoft Teams


	• Catching anonymous participants
	• Catching people outside the org
	• Catching people without invites
	• Catching people dialing in by phone
	• Catching non-organizers
	• Catching everyone from blocked domains
Prevent anonymous users from starting the meeting


People in the org

external users
guests
anonymous participants

people inside
people outside
anonymous people


Everyone
People in my organization, trusted organizations, and guests
People in my organization and guests
People in my organization
Only people who were invited
Only organizers and co-organizers

Final Lobby experience and outcome is result of interplay between 4 different user groups:
1.	IT Admins set the default Lobby policy in Teams admin center (TAC) for specific groups of users (organizers). 
a.	Their goal is Meeting security, preventing specific types of users from joining the meeting without additional verification
2.	Meeting Organizers can change default Lobby policy before or during the meeting. Their goals are any combination (a, b, ab) of:
a.	Hold on user from joining/starting the meeting before Organizer decides to start the meeting
b.	Verify identity of people joining the call
3.	In-meeting participants with capability to admit or deny people from Lobby to meeting can take an action either from the Lobby notification or Roster/People tab
a.	Their (imposed) goal is to prevent unauthorized people from joining the call by individual admit/deny (sometimes in the form of no action - ignoration). Capability to admit is role-based (Organizer, Co-organizer, Presenters).
4.	Participants waiting in Lobby
a.	Their goal is to end up in the right call and don’t waste time waiting


Who can join the meeting directly
Who can start the meeting

![Screenshot showing a meeting with a user in the lobby.](media/meeting-policies-lobby.png)

## Overview of lobby settings and policies

The following table shows the Teams meeting settings and policies affect how meeting participants interact with the lobby.

|Setting|Description|
|:------|:----------|
|**Anonymous users can join a meeting** (organization setting)|This global setting allows anyone with a meeting link to join the meeting anonymously if they are not signed in to a work or school account or as a guest. (The **Anonymous users can join a meeting** meeting policy must also be **On** for the meeting organizer.)|
|**Anonymous users can join a meeting** (meeting policy)|This per-organizer setting allows anyone with a meeting link to join the meeting anonymously if they are not signed in to a work or school account or as a guest. (The **Anonymous users can join a meeting** organization setting must also be **On**.)|
|**Anonymous users and dial-in callers can start a meeting**|This setting is a per-organizer policy that allows for leaderless dial-in conferencing meetings. This setting controls whether dial-in users can join the meeting without an authenticated user from the organization in attendance. By default, this setting is turned off, which means dial-in users will wait in the lobby until an authenticated user from the organization joins the meeting.|
|**People dialing in can bypass the lobby**|This is a per-organizer policy. This setting controls whether people who dial in by phone join the meeting directly or wait in the lobby. When this setting is **Off**, dial-in users will wait in the lobby until an organization user joins the meeting and admits them. When this setting is **On**, dial-in users will automatically join the meeting once an organization user joins the meeting.|
|**Who can bypass the lobby**|This is a per-organizer policy. This setting controls which types of participants join a meeting directly and which wait in the lobby until they're admitted by an authenticated user. This setting doesn't apply to dial-in users.|

The following table shows how each option for the **Who can bypass the lobby** control affects each type of meeting participant.

|Who can bypass the lobby?|Everyone|People in my organization, trusted organizations, and guests|People in my organization and guests|People in my organization|Only people who were invited|Only organizers and co-organizers|
|:------------------------|:------:|:----------------------------------------------------------:|:-----------------------------------|:------------------------|:---------------------------|:--------------------------------|
|Organizers|Bypass|Bypass|Bypass|Bypass|Bypass|Bypass|
|People in the organization|Bypass|Bypass|Bypass|Bypass|People in the org who were sent or forwarded an invite will bypass; others go to the lobby|Lobby|
|Guests|Bypass|Bypass|Bypass|Lobby|Lobby|Lobby|
|People in trusted organizations|Bypass|Bypass|Lobby|Lobby|Lobby|Lobby|
|Anonymous participants|Bypass|Lobby|Lobby|Lobby|Lobby|Lobby|

Both the **People dialing in can bypass the lobby** and **Who can bypass the lobby** settings set defaults that the meeting organizer can change. If you need to enforce these settings to a particular value, you can use a meeting template or sensitivity label (Teams Premium required). For more information, see [Configure the Microsoft Teams meeting lobby for sensitive meetings](configure-lobby-sensitive-meetings.md).


**Only people who were invited** Users added as a part of a distribution group will have to go through the lobby.

Trusted organizations are domains that you allow federated communications with in Teams. If you enable **Allow all external domains** for external access in the Teams admin center, any authenticated user within any Teams organization will be trusted. If you choose to specify external domains that are allowed and block all others, the allowed domains become trusted organizations. Any blocked domain is considered to not be a trusted organization.



## Control access to meetings by unauthenticated participants

anonymous and dial-in

prevent anonymous from starting

## Control access to meetings by guests and people from trusted organizations

[external access](manage-external-access.md) feature

allowed domains

## Control access to meetings by people without invitations

**Only people who were invited** setting for **Who can bypass the lobby**

## Control access to meetings by non-organizers

**Only organizers and co-organizers** setting for **Who can bypass the lobby**

## Let anonymous people join a meeting

This per-organizer setting allows anyone to join meetings as an anonymous user by selecting the link in the meeting invitation. To learn more, see [Join a meeting without a Teams account](https://support.microsoft.com/office/c6efc38f-4e03-4e79-b28f-e65a4c039508). Anonymous users' ability to join meetings are also controlled at your organization level, the more restrictive setting will be effective. To learn more, see [Using the Microsoft Teams admin center to configure organization-wide policy](meeting-settings-in-teams.md#allow-anonymous-users-to-join-meetings).

## Let anonymous people start a meeting

This setting is a per-organizer policy that allows for leaderless dial-in conferencing meetings. This setting controls whether dial-in users can join the meeting without an authenticated user from the organization in attendance. By default, this setting is turned off, which means dial-in users will wait in the lobby until an authenticated user from the organization joins the meeting.

> [!NOTE]
> If this setting is turned off and a dial-in user joins the meeting first and is placed in the lobby, an organization user must join the meeting with a Teams client to admit the user from the lobby. There are no lobby controls available for dialed in users.

## Dial-in users can bypass the lobby

This is a per-organizer policy. This setting controls whether people who dial in by phone join the meeting directly or wait in the lobby regardless of the **Automatically admit people** setting. By default, this setting is turned off. When this setting is turned off, dial-in users will wait in the lobby until an organization user joins the meeting with a Teams client and admits them. When this setting is turned on, dial-in users will automatically join the meeting when an organization user joins the meeting with a Teams client.

> [!NOTE]
> If a dial-in user joins a meeting before an organization user joins the meeting, they will be placed in the lobby until an organization user joins the meeting using a Teams client and admits them. If you change the default setting for any user, it will apply to all new meetings organized by that user and any prior meetings where the user didn't modify Meeting options.

## Related topics

