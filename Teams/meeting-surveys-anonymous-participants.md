---
title: Manage feedback surveys for anonymous participants in Teams meetings
author: lana-chin
ms.author: v-chinlana
manager: jtremper
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jewilcze
ms.date: 02/27/2024
search.appverid: MET150
searchScope:
  - Microsoft Teams
audience: admin
description: Learn how to control whether anonymous participants who join Teams meetings hosted by your organization receive surveys to provide feedback to Microsoft about their meeting experience. 
ms.localizationpriority: medium
ms.collection: 
- M365-collaboration
- m365-frontline
- m365initiative-meetings
- m365-virtual-appointments 
appliesto: 
  - Microsoft Teams
---

# Manage feedback surveys for anonymous participants in Teams meetings

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

## Overview

[Anonymous participants](anonymous-users-in-meetings.md) who join Teams meetings (including virtual appointments), webinars, and town halls hosted by your organization can rate their meeting experience and send us feedback about the rating they give through surveys. We’re continually improving the Teams meeting experience and we use this feedback to help make it better.

By default, this feature is turned on for your organization and anonymous meeting participants receive surveys. When a meeting ends, anonymous participants see a prompt on the screen that gives them the option to provide feedback. When they choose **Give feedback**, the survey is displayed for them to complete and send to Microsoft.

Here’s an example of a survey that anonymous meeting participants might receive.

:::image type="content" source="media/meeting-surveys-anonymous-participants.png" alt-text="Screenshot of a survey that anonymous meeting participants receive to provide feedback about their Teams meeting experience.":::

## Set whether anonymous meeting participants receive surveys

As an admin, you can control whether anonymous participants receive surveys to provide feedback about their meeting experience.

You turn off or turn on this feature for your organization through a policy that you set by using the [Set-CsTeamsMeetingConfiguration](/powershell/module/teams/set-csteamsmeetingconfiguration) PowerShell cmdlet.

- To allow anonymous meeting participants to receive surveys, set the `FeedbackSurveyForAnonymousUsers` parameter to `Enabled`. This is the default value.
- If you don’t want anonymous meeting participants to receive surveys, set the `FeedbackSurveyForAnonymousUsers` parameter to `Disabled`.

    > [!IMPORTANT]
    > To turn off this feature, the value must be set to `Disabled`. Setting the value to `$disabled` won't work.

For example, to turn off feedback surveys for anonymous participants in Teams meetings (including virtual appointments), webinars, and town halls, run the following command:

```PowerShell
Set-CsTeamsMeetingConfiguration -FeedbackSurveyForAnonymousUsers Disabled
```

> [!NOTE]
> You can access and get insights into feedback collected from Net Promoter Score (NPS) survey responses in the Microsoft 365 admin center. To learn more, see [Microsoft product NPS feedback and insights for your organization](/microsoft-365/admin/manage/manage-feedback-product-insights).

## Related articles

- [Manage anonymous participant access to Teams meetings, webinars, and town halls](anonymous-users-in-meetings.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
