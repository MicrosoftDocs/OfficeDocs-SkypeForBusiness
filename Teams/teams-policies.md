---
title: Manage channel policies in Microsoft Teams
author: MikePlumleyMSFT
ms.author: mikeplum
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
ms.localizationpriority: medium
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
description: Learn how to use and manage teams channel policies in your organization to control what users can do in teams and channels.
---

# Manage channel policies in Microsoft Teams

As an admin, you can use policies in Microsoft Teams to control what users in your organization can do in teams and channels. For example, you can set whether users are allowed to create private or shared channels.

You manage teams policies by going to **Teams** > **Teams policies** in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

You can edit the global policy or create and assign a custom policy. After you edit the global policy or assign a policy, it may take 24 hours for changes to take effect.

## Channel policies

The following policies are available for teams channels:

|Policy|Description|
|:-----|:----------|
|**Create private channels**|When **On**, team owners and members can create private channels. (Team owners can control if members can create private channels in each team.)|
|**Create shared channels**|When **On**, team owners can create shared channels. Teams apps that are available for your organization are also available in shared channels.|
|**Invite external users to shared channels**|When **On**, owners and members of shared channels can invite external participants from organizations where a cross-organization trust has been configured. Teams policies for your organization apply to these channels.|
|**Join external shared channels**|When **On**, users can participate in shared channels created by other organizations where a cross-organization trust has been configured. Teams policies for the other organization apply to these channels.|

## Create a custom teams policy

1. In the left navigation of the Microsoft Teams admin center, go to **Teams** > **Teams policies**.
2. Click **Add**.
3. Enter a name and description for the policy.

    ![Screenshot of teams policy settings.](media/teams-policies.png)
4. Turn on or turn off the settings that you want, and then click **Save**.

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

[Assign policies to your users in Teams](policy-assignment-overview.md)

[New-CsTeamsChannelsPolicy](/powershell/module/skype/new-csteamschannelspolicy)
