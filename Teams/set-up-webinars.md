---
title: Set up for webinars in Microsoft Teams 
author: mkbond007
ms.author: mabond
manager: serdars
ms.reviewer: sachung, emryan
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Learn how to manage Webinar policies for Teams meetings.
---

# Set up for webinars in Microsoft Teams

This article will help you set up your organization to host webinars.

## What are webinars?

Webinars are structured meetings where presenters and participants have clear roles, often used for training purposes or sales and marketing lead generation scenarios.

After setting up webinars in your organization, your users can schedule webinars and open registration to attendees. Unlike traditional meetings that include many discussions and task assignment, webinars are meant for interactive presentations and provide tools for attendee analysis.

> [!IMPORTANT]
> To let users set up webinars, Microsoft Lists must be configured in SharePoint by enabling the creation of personal lists. To learn more, see [Control settings for Microsoft Lists](/sharepoint/control-lists).

## Allow users to schedule webinars in the Teams admin center

You can use the Teams admin center to set up webinars for your organization. You'll find the policies to set up webinars in the Teams admin center under **Meetings** > **Meeting policies**.

### Meeting registration

If you turn this on, users can schedule webinars. By default, this is turned on. If you want to turn off meeting registration, set this policy to **Off**.

> [!IMPORTANT]
> **Private meeting scheduling** must be on for meeting registration to work. By default, this policy is turned on in the Teams admin center. For students in education tenants, this policy is turned off by default. For more information on how to enable private meeting scheduling for students, see [Teams for Education policies and policy packages](policy-packages-edu.md).

### Who can register

If you select **Everyone**, all users, including anonymous users, can register for and attend webinars. If you select **Everyone in the organization**, only users in your organization can register for webinars. If meeting registration is turned off, this option will not be available and no one can register for webinars.

> [!NOTE]
> The default value for **Who can register** is **Everyone in the organization** in education tenants. For more information, see [Teams for Education Policy Wizard](easy-policy-setup-edu.md).

### Engagement report

When this is on, organizers can see reports of who registered and attended the webinars they set up. This policy is on by default. For more information, see [Meeting policies in Teams - Engagement report](meeting-policies-in-teams-general.md#engagement-report). For information on the end-user experience, see [View and download meeting attendance reports](https://support.microsoft.com/office/view-and-download-meeting-attendance-reports-in-teams-ae7cf170-530c-47d3-84c1-3aedac74d310?ui=en-US&#x26;rs=en-US&#x26;ad=US).

## Allow users to schedule webinars using PowerShell

You can use the following attributes within the Windows PowerShell **Set-CsTeamsMeetingPolicy** cmdlet to set up for webinars in Teams.

- AllowMeetingRegistration
- WhoCanRegister
- AllowPrivateMeetingScheduling

Read [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) for more information on the cmdlet.

> [!NOTE]
> Before you can run these cmdlets you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

### Allow users to schedule webinars

You can restrict registration to users only in your organization or open it up to everyone both inside and outside your tenant. By default, **WhoCanRegister** is enabled and set to **Everyone** for the **Global (Org-wide default)** policy. If you want to turn off meeting registration, set **AllowMeetingRegistration** to **False**.

> [!IMPORTANT]
> **AllowPrivateMeetingScheduling** must be set to **True** for **AllowMeetingRegistration** to work.

1. Turn on meeting registration

```powershell
Set-CsTeamsMeetingPolicy -AllowMeetingRegistration $True
```

2. Turn on private meeting scheduling

```powershell
Set-CsTeamsMeetingPolicy -AllowPrivateMeetingScheduling $True
```

3. Configure who can register for webinars

**Allow *only* users in your organization to register for webinars**

```powershell
Set-CsTeamsMeetingPolicy -WhoCanRegister EveryoneInCompany
```

**To allow anyone, including anonymous users, to register for webinars, run:**

```powershell
Set-CsTeamsMeetingPolicy -WhoCanRegister Everyone
```

> [!CAUTION]
> If anonymous join is turned off in meeting settings, anonymous users can't join webinars. To learn more and enable this setting, see [Meeting settings in Teams](meeting-settings-in-teams.md).

### Collect meeting attendance

The **AllowEngagementReport** parameter lets you see who registered and attended webinars. This policy is turned on by default. To turn it off, run the following command in PowerShell:

```powershell
Set-CsTeamsMeetingPolicy -AllowEngagementReport Disabled
```

## Configure webinar settings

After enabling your environment for webinars, no further admin management is required. The policy controls which options show up for webinar organizers.

## Related topics

- [Meeting policies in Teams - General](meeting-policies-in-teams-general.md)
- [Set-CsTeamsMeetingPolicy documentation](/powershell/module/skype/set-csteamsmeetingpolicy)
- [Teams for Education Policy Wizard](easy-policy-setup-edu.md)
