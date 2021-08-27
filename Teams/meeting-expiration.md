---
title: Meeting policies and meeting expiration in Microsoft Teams
author: cichur
ms.author: v-cichur
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: nej
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
description: Learn how to use meeting policy settings to control meeting expiration in Microsoft Teams.
---

# Meeting policies and meeting expiration in Microsoft Teams

[Meeting policies](meeting-policies-in-teams.md) in Microsoft Teams are used to control whether users in your organization can start and schedule meetings and the features that are available to meeting participants for meetings that are scheduled by users. You can use the global (Org-wide default) policy or create and assign custom policies. You manage meeting policies in the Microsoft Teams admin center or by using [Get](/powershell/module/skype/get-csteamsmeetingpolicy), [New](/powershell/module/skype/new-csteamsmeetingpolicy), [Set](/powershell/module/skype/set-csteamsmeetingpolicy), [Remove](/powershell/module/skype/remove-csteamsmeetingpolicy), [Grant](/powershell/module/skype/grant-csteamsmeetingpolicy) -CsTeamsMeetingPolicy PowerShell cmdlets.

The meeting policy settings that control whether users can start and schedule meetings and also control expiration of meetings scheduled by users. When a meeting join link and conference ID for a meeting expires, no one can join the meeting. The following meeting policy settings determine whether users can start and schedule meetings in Teams. We discuss the meeting settings in this article.

- [Allow Meet now in channels](meeting-policies-in-teams-general.md#allow-meet-now-in-channels): Controls whether a user can start an impromptu meeting in a channel.
- [Allow channel meeting scheduling](meeting-policies-in-teams-general.md#allow-channel-meeting-scheduling): Controls whether a user can schedule a meeting in a channel.
- [Allow scheduling private meetings](meeting-policies-in-teams-general.md#allow-scheduling-private-meetings): Controls whether a user can schedule a private meeting in Teams. A meeting is private when it's not published to a channel in a team.
- [Allow the Outlook add in](meeting-policies-in-teams-general.md#allow-the-outlook-add-in): Controls whether a user can schedule a private meeting from Outlook. A meeting is private when it's not published to a channel in a team.
- [Allow Meet now in private meetings](meeting-policies-in-teams-general.md#allow-meet-now-in-private-meetings): Controls whether a user can start an impromptu private meeting.

By default, these settings are on. When any of these settings are turned off, any user who is assigned the policy can't start or schedule new meetings of that type. At the same time, the meeting join links and conference IDs of all existing meetings of that type that the user previously started or scheduled expire.

For example, if a user is assigned a meeting policy in which these meeting policy settings are set to **On**, and then you turn off the **Allow Meet now in channels** setting, that user can no longer start impromptu meetings in channels, and the channel Meet now join links that the user previously created are expired. The user can still start and schedule other meeting types and join meetings organized by other people.

## What happens when the meeting join link and conference ID expire?

When the meeting join link and conference ID for a meeting expires, no one can join the meeting. When a user tries to join the meeting through the link or by phone, they'll get a message that says the meeting is no longer available. Conversations, files, whiteboards, recordings, transcripts, and other content related to the meeting are retained and users can still access them.

## What happens when you turn on and turn off a meeting policy setting?

### Switch a meeting policy setting from on to off

When a meeting policy setting is set to **On**, users who are assigned the policy can start or schedule meetings of that type and everyone can join. When you switch the meeting policy setting to **Off**, users who are assigned the policy can't start or schedule new meetings of that type, and the meeting join links and conference IDs of existing meetings that the user previously scheduled are expired.

Keep in mind that the user can still join meetings organized by other people.

### Switch a meeting policy setting from off to on

When you switch a meeting policy setting from **Off** to **On**, users who are assigned the policy can start or schedule meetings of that type. If a meeting policy setting is turned off and then turned on again for a user, all previously scheduled (and expired) meetings organized by the user become active and people can join them using the meeting join link or by phone.  

## Meeting expiration scenarios

Here's a summary of how meeting expiration works for each of the meeting policy settings discussed in this article.

|If you want to...&nbsp;&nbsp; |Do this&nbsp;&nbsp;&nbsp;&nbsp;  |Meeting join behavior&nbsp;&nbsp;&nbsp;&nbsp;  |
|---------------------------|---------------------|---------|
|Expire private Meet now meetings started by a user&nbsp;&nbsp;|Turn off **Allow Meet now in private meetings**.&nbsp;&nbsp;|No one can join private **Meet now** meetings started by the user.|
|Expire private meetings scheduled by a user&nbsp;&nbsp;|Turn off **Allow scheduling private meetings** _and_ turn off **Allow the Outlook add-in**. &nbsp;&nbsp;|No one can join private meetings scheduled by the user. This prevents people from joining the following meetings:<ul><li>Private meetings that occurred in the past.</li><li>Private meetings that are scheduled for the future and have not yet occurred.</li><li>Future instances of recurring private meetings.</li></ul><br>Both **Allow scheduling private meetings** and **Allow the Outlook add-in** must be off to expire private meetings scheduled by a user. If one setting is off and the other is on, meeting join links and conference IDs of existing meetings remain active and won't be expired.|
|Expire channel **Meet now** meetings started by a user&nbsp;&nbsp;|Turn off **Allow Meet now in channels** _and_ turn off **Allow channel meeting scheduling**.&nbsp;&nbsp;|No one can join channel **Meet now** meetings started by the user.|
|Expire channel meetings scheduled by a user&nbsp;&nbsp;|Turn off **Allow channel meeting scheduling**.&nbsp;&nbsp;|No one can join channel meetings scheduled by the user. This prevents people from joining the following meetings:<ul><li>Channel meetings that occurred in the past.</li><li>Channel meetings that are scheduled for the future and haven't yet occurred.</li><li>Future instances of recurring channel meetings.</li></ul>|

If you want people to access meetings that were previously scheduled or started by a particular user, you can:

- Turn on the meeting policy setting for that user.
- Turn off the meeting policy setting for that user and have another user who has the policy setting enabled create a new meeting to replace the expired meeting.

> [!NOTE]
> If the meeting was sent by a delegate, who was given permissions to send meeting invitations on behalf of another person, such as a manager, the meeting policy setting is applied to the person who granted permission (the manager).

## Changes to meeting expiration

**What is the change?**

We are introducing a default 60-day expiration setting for *all* newly created Teams meeting recordings (TMRs). This is on by default for all tenants. This means that by default, all TMRs created after we enable this feature will be deleted 60 days after their creation date. If admins want meeting recordings to expire sooner or later than the default, they can modify the expiration setting. The OneDrive and SharePoint system will monitor the expiration date set on all TMRs and will automatically move TMRs to the recycle bin on their expiration date.

**Why are we introducing this change?**

We've answered your requests for the meeting recording expiration feature. This is a lightweight housekeeping mechanism to reduce storage clutter created by older TMRs. On average, across all customers, 99% of TMRs are never rewatched after 60 days.

**Why is this being turned on by default?**

We believe nearly all customers will benefit from the reduced storage load on their tenant by removing recordings that will likely never be rewatched after 60 days. It's our goal to provide as clean an experience as possible for all customers by default.

**How is the expiration date calculated?**

The expiration date is calculated as the day it's created plus the default number of days set in the Teams policy by the admin.

**Does playing the recording change the expiration date?**

No, playback doesn't impact the expiration date.

**How can an Admin change the default** **expiration date** **in their tenant?**

Admins can edit the default expiration setting in PowerShell or their Teams policy console. That change will affect only newly created TMRs from that point forward. It won't impact any recordings created before that date.

Admins can't change the expiration date on existing TMRs. This is done to protect the decision of the user that owns the TMR.

Example PowerShell command:

`PowerShellCopy`

`Set-CsTeamsMeetingPolicy -Identity Global -MeetingRecordingExpirationDays 50`

**What is the scope of control for the admin policy?**

Both meetings and calls will be controlled by the same CsTeamsMeetingPolicy setting, MeetingRecordingExpirationDays.

**How can end users modify the expiration date?**

Anyone who has edit and delete permissions on a TMR can modify the expiration date in the file’s details pane in Microsoft OneDrive and SharePoint.

Users can defer the expiration using a quick select drop-down of 7, 30, or 60 days, or they can choose a specific date in the future. Another option is that they can select that the file never auto-expires.

**Whom does this impact?**

Anyone storing TMRs in OneDrive or SharePoint.

**Why should I use this feature?**

You should use this to limit the OneDrive or SharePoint for Cloud storage consumption driven by Teams meeting records. A typical meeting recording consumes around 400 MB per hour of recording.

**Should I rely on this feature for strict security and compliance adherence?**

No, you shouldn't rely on this for legal protection since end users can modify the expiration date of any recordings they control.

**Will this feature enforce file retention?**

No, files won't be retained due to this feature or its settings. If a user with delete permissions attempts to delete a TMR that has an expiration setting, that user’s delete action will be executed.

**Will a retention and/or deletion policy I've set in the Security & Compliance center override the Teams meeting recording expiration setting?**

Yes, any policies you have set in the compliance center will take full precedence.

For example:

- If you have a policy that says all files in a site must be retained for 100 days, and the expiration setting for a Teams meeting recording is 30 days, then the recording will be retained for the full 100 days.

- If you have a deletion policy that says all Teams meeting recordings will be deleted after five days and you have an expiration setting for a Teams meeting recording of 30 days, then the recording will be deleted after five days.

**What happens when a TMR expires?**

On the expiration date, the TMR is moved into the OneDrive or SharePoint recycle bin and the expiration date field is cleared. This action by the system is exactly the same as if a user deleted the file. The recycle bin lifecycle will then follow the normal path. If the user recovers the TMR from the recycle bin, the TMR will not be deleted by this feature again since the expiration date has been cleared, unless the end user sets a new expiration date on the file.

**How will end users be notified about a file’s expiration?**

- Everyone will see a notification about the expiration date in the recording chicklet in the Teams chat window.

- Everyone can see the TMR’s expiration date in the details pane of the TMR file.

- The file owner will receive an email notification when the recording expires and will be directed to the recycle bin to recover the recording.

**What SKUs are required for this feature?**

- All SKUs will have this feature by default.

- A1 users will be defaulted to a 30-day expiration period and won't be able to modify the expiration date.

**Is the file expiration an audited event and will I be able to see it in my audit logs?**

Yes, these will show up as system deletion events in the audit log.

**What if I want the admin to have full control over the lifecycle of meeting recordings and don't want to give end users the ability to override the expiration date?**

We recommend using the Security and Compliance retain and/or delete policies available as part of the E5 compliance SKU. That offering is targeted to solve complex policy and SLA-driven administrative legal concerns.

The auto-expiration feature is solely meant as a lightweight housekeeping mechanism to reduce storage clutter created from old Teams meeting recordings.

**When will the file be deleted?**

The file will be deleted within five days of the expiration date, though this isn't a strict guarantee.

**Will future TMRs migrated from Classic Stream after this feature is released have auto-expiration applied to them too?**

No, migrated TMRs will not come with an expiration set on them. Instead, we encourage admins to only migrate TMRs that they want to retain. More details will be provided in the migration documentation.

## Related topics

[Manage meeting policies in Teams](meeting-policies-in-teams.md)

[Assign policies to your users in Teams](assign-policies.md)

[Teams PowerShell overview](teams-powershell-overview.md)
