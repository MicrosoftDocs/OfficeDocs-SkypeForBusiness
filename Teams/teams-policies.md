---
title: Manage teams policies in Microsoft Teams
author: cichur
ms.author: v-cichur
manager: serdars
ms.reviewer: jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.teams.teamspolicies.new.tooltip.discoverteams
  - ms.teamsadmincenter.teams.teamspolicies.new.tooltip.createchannels
  - ms.teamsadmincenter.teams.teamsandchannelpolicies.overview
  - ms.teamsadmincenter.teamsandchannelpolicies.overview
  - ms.teamsadmincenter.teams.teamspolicies.new.tooltip.discover
  - ms.teamsadmincenter.teams.teamspolicies.new.tooltip.create
description: Learn how to use and manage teams policies in your organization to control what users can do in teams and channels.
---

# Manage teams policies in Microsoft Teams

As an admin, you can use teams policies in Microsoft Teams to control what users in your organization can do in teams and channels. For example, you can set whether users are allowed to create private channels.

You manage teams policies by going to **Teams** > **Teams policies** in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

You can edit the global policy or create and assign a custom policy. After you edit the global policy or assign a policy, it can take a few hours for changes to take effect.

## Create a custom teams policy

1. In the left navigation of the Microsoft Teams admin center, go to **Teams** > **Teams policies**.
2. Click **Add**.
3. Enter a name and description for the policy.

    ![Screenshot of teams policy settings](media/teams-policies.png)
4. Turn on or turn off **Create private channels**, <a name="createchannels"> </a> depending on whether you want to allow users to create private channels.

5. Click **Save**.

## Edit a teams policy

You can edit the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams** > **Teams policies**.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. Turn on or turn off the settings that you want, and then click **Save**.

## Assign a custom teams policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

## Related topics

[Manage Teams connected sites and channel sites](/SharePoint/teams-connected-sites)

[Private channels in Teams](private-channels.md)

[Assign policies to your users in Teams](assign-policies.md)

[New-CsTeamsChannelsPolicy](/powershell/module/skype/new-csteamschannelspolicy?view=skype-ps)
