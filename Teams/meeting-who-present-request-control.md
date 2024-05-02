--- 
title: Manage who can present and request control in Teams meetings and webinars
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: nakulm, bryannyce
ms.date: 04/29/2024
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - Tier2
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.participantandguests
description: Learn to manage who can present and take control in Teams meetings.
---

# Manage who can present and request control in Teams meetings and webinars

**APPLIES TO:** ✔️Meetings ✔️Webinars ✖️Town halls

As an admin, you can manage who can present in meetings and webinars and whether participants and external participants can request control of the presentation.

## Manage who can present and request control

To manage who can present and request control, follow these steps:

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
2. Select the policy that you want to edit or create a new one.
3. Navigate to the **Content sharing** section.
4. Select your desired values for [**Who can present**](#manage-who-can-present), [**Participants can give or request control**](#participants-can-give-or-request-control), [**External participants can give or request control**](#external-participants-can-give-or-request-control) (described in the following sections).
5. Select **Save**.

### Manage who can present

**Who can present** lets organizers choose who can be presenters in a meeting or webinar. To learn more, see [Change participant settings for a Teams meeting](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e) and [Roles in a Teams meeting](https://support.microsoft.com/office/c16fa7d0-1666-4dde-8686-0a0bfe16e019).

This setting is a per-user policy that and lets you choose the default value for the **Who can present** setting that organizers see in their Meeting options. The **Who can present** policy setting affects all meetings and webinars, including Meet Now meetings.

To specify the default value of the **Who can present** setting in Teams, select one of the following settings in the **Who can present** policy:

| Option | Behavior |
|---|---|
| Only organizers and co-organizers | Only the organizer and chosen co-organizers can present during the meeting or webinar. All the other  participants join the meeting or webinar as attendees. |
| People in my org and guests | Authenticated users in your org, including guests, join the meeting or webinar as a presenter and can present. |
| Everyone | **This is the default.**  Everyone attending the meeting or webinar joins as a presenter and can present. This setting corresponds to the **Everyone** setting in Teams.  |

After you set the default value, organizers can still change this setting through their Meeting options in Teams to choose who can present in their meetings and webinars.

### Participants can give or request control

This setting is a per-user policy that controls whether users with this assigned policy can give, be given, or request control of the shared desktop or window. To give control, your users can hover over the top of the screen.

You can toggle this setting **On** or **Off** in the Teams admin center or manage this policy in PowerShell.

When this assigned policy is **On** for a user, the **Give Control** option is displayed in the top bar during a sharing session.

When this assigned policy is **Off** for a user, the **Give Control** option isn't available.

Let's look at the following example.

| User | Meeting policy | Allow participant to give or request control |
|---|---|---|
| Daniela | Global | On |
| Adele | Location1MeetingPolicy | Off |

Daniela can give control of the shared desktop or window to other participants in a meeting or webinar Adele organizes. However, Adele can't give control to other participants.

> [!NOTE]
> To give and take control of shared content during sharing, both users must be using the Teams desktop client. Control isn't supported when either user is using Teams in a browser.

#### PowerShell

Use the **`-AllowExternalParticipantGiveRequestControl`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet to control whether or not external participants can give, be given, and request control during meetings and webinars.

To allow users to give, be given, and request control during meetings and webinars, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowParticipantGiveRequestControl $True
```

To prevent users from giving, being given, and requesting control during meetings and webinars, use the following script, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowParticipantGiveRequestControl $False
```

### External participants can give or request control

This setting is a per-user policy. This policy controls whether external participants can give, be given, or request control of the sharer's screen in meetings and webinars organizers with this policy create.

You can toggle this setting **On** or **Off** in the Teams admin center or manage this policy in PowerShell.

**External participants can give or request control**  doesn't control what external participants can do in meetings and webinars they attend. The organizer's **Who can present** and **Who can bypass the lobby** settings in their **Meeting options** determines what external participants can do in their meeting or webinar.

External participants in Teams meetings can be categorized as follows:  

- Anonymous participant
- Guests
- External access users

For external access users to give control to other external participants, both you and the other org's admin must have this policy set to **On**.

#### PowerShell

Use the **`-AllowExternalParticipantGiveRequestControl`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet to control whether or not external participants can give, be given, and request control during meetings and webinars.

For external participants to give, be given, and request control in meetings and webinars organizers with this policy create, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowExternalParticipantGiveRequestControl $True
```

To prevent external participants from being given, giving, and requesting control in meetings and webinars organizers with this policy create, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowExternalParticipantGiveRequestControl $False
```

## Related topics

- [Teams policy reference - Meetings](settings-policies-reference.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
- [Plan meetings](plan-meetings.md)
- [Plan webinars](plan-webinars.md)
