---
title: Manage call routing policies for Direct Routing
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: filippse
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
f1.keywords:
- NOCSH
ms.collection: 
- M365-voice
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to create and manage call routing policies for Microsoft Teams Direct Routing. 
---

# Manage call routing policies for Direct Routing

If you've deployed [Direct Routing](direct-routing-landing-page.md) in your organization, you use call routing policies to allow Teams users to receive and make phone calls to the Public Switched Telephone Network (PSTN) using your on-premises telephony infrastructure.

A call routing policy (also called a voice routing policy) is a container for PSTN usage records. You create and manage voice routing policies by going to **Voice** > **Voice routing policies** in the Microsoft Teams admin center or by using Windows PowerShell.

You can use the global (Org-wide default) policy or create and assign custom policies. Users will automatically get the global policy unless you create and assign a custom policy. Keep in mind that you can edit the settings in the global policy but you can't rename or delete it.

It's important to know that assigning a voice routing policy to a user doesn't enable them to make PSTN calls in Teams. You'll also need to enable the user for Direct Routing and complete other configuration steps. To learn more, see [Configure Direct Routing](direct-routing-configure.md).

## Create a custom call routing policy

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Voice routing policies**, and then click **Add**.<br>

2. Enter a name and description for the policy.

3. Under **PSTN usage records**, click **Add PSTN usage**, and then select the records that you want to add. If you need to create a new PSTN usage record, click **Add**.

4. If you added multiple PSTN usage records, arrange them in the order that you want.
5. When you're done, click **Apply**.

6. Click **Save**.

### Using PowerShell

See [New-CsOnlineVoiceRoutingPolicy](/powershell/module/skype/new-csonlinevoiceroutingpolicy).

## Edit a call routing policy

### Using the Microsoft Teams admin center

You can edit the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Voice routing policies**.

2. Select the policy by clicking to the left of the policy name, and then click **Edit**.

3. Click **Add/remove PSTN usage records**, make the changes that you want, and then click **Save**.

### Using PowerShell

See [Set-CsOnlineVoiceRoutingPolicy](/powershell/module/skype/set-csonlinevoiceroutingpolicy).

## Assign a custom call routing policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

See also [Grant-CsOnlineVoiceRoutingPolicy](/powershell/module/skype/grant-csonlinevoiceroutingpolicy).

## Related topics

[Teams PowerShell overview](teams-powershell-overview.md)

[Configure call routing for Direct Routing](direct-routing-voice-routing.md)

[Enable Location-Based Routing for Direct Routing](location-based-routing-enable.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)