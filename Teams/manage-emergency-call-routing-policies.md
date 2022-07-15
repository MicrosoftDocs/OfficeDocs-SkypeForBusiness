---
title: Manage emergency call routing policies for Direct Routing
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jastark, roykuntz
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
f1.keywords:
- NOCSH
- ms.teamsadmincenter.voice.emergencycallroutingpolicies.overview
ms.collection: 
- M365-voice
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use and manage emergency call routing policies in Microsoft Teams to set up emergency numbers and specify how emergency calls are routed. 
ms.custom: 
- seo-marvel-apr2020
- ms.teamsadmincenter.voice.emergencycallroutingpolicies.overview
---

# Manage emergency call routing policies for Direct Routing

If you've deployed [Direct Routing](direct-routing-landing-page.md) in your organization, you can use emergency call routing policies in Microsoft Teams to set up emergency numbers and specify how emergency calls are routed. An emergency call routing policy determines whether enhanced emergency services are enabled for users who are assigned the policy, the numbers used to call emergency services (for example, 911 in the United States), and how calls to emergency services are routed. 

> [!Note]
> **Note that these call routing policies apply only to Direct Routing--they do not apply to Calling Plans or Operator Connect.**

You manage emergency call routing policies by going to **Voice** > **Emergency policies** in the Microsoft Teams admin center or by using Windows PowerShell. The policies can be assigned to users and [network sites](cloud-voice-network-settings.md).

For users, you can use the global (Org-wide default) policy or create and assign custom policies. Users will automatically get the global policy unless you create and assign a custom policy. Keep in mind that you can edit the settings in the global policy but you can't rename or delete it. For network sites, you create and assign custom policies.

If you assigned an emergency call routing policy to a network site and to a user and if that user is at that network site, the policy that's assigned to the network site overrides the policy that's assigned to the user.

## Create a custom emergency call routing policy

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Emergency policies**, and then click the **Call routing policies** tab.
2. Click **Add**.
3. Enter a name and description for the policy.
4. To enable dynamic emergency calling, turn on **Dynamic emergency calling**. When dynamic emergency calling is enabled, Teams retrieves policy and location information from the service and includes that information as part of the emergency call.
5. Define one or more emergency numbers. To do this, under **Emergency numbers**, click **Add**, and then do the following:
    1. **Emergency dial string**: Enter the emergency dial string. This dial string indicates that a call is an emergency call and the route pattern must match this dial string exactly. 
        > [!NOTE]
        > **For Direct Routing, Teams clients no longer send emergency calls with a "+" in front of the emergency dial string. Be sure the voice route pattern to match an emergency dial string reflects this change.**
    2. **Emergency dial mask**: For each emergency number, you can specify zero or more emergency dial masks. A dial mask is the number that you want to translate into the value of the emergency dial string. This allows for alternate emergency numbers to be dialed and still have the call reach emergency services. <br>For example, you add 112 as the emergency dial mask, which is the emergency service number for most of Europe, and 911 as the emergency dial string. A Teams user from Europe who is visiting may not know that 911 is the emergency number in the United States, and when they dial 112, the call is made to 911. To define multiple dial masks, separate each value by a semicolon. For example, 112;212.
    3. **PSTN usage record**: Select the Public Switched Telephone Network (PSTN) usage record. The PSTN usage record is used to determine which route is used to route emergency calls from users who are authorized to use them. The route associated with this usage should point to a Session Initiation Protocol (SIP) trunk dedicated to emergency calls or to an Emergency Location Identification Number (ELIN) gateway that routes emergency calls to the nearest Public Safety Answering Point (PSAP).

    > [!NOTE]
    > Dial strings and dial masks must be unique within a policy. This means that for a policy, you can define multiple emergency numbers and you can set multiple dial masks for a dial string, but each dial string and dial mask must only be used one time.

6. Click **Save**.

### Using PowerShell

See [New-CsTeamsEmergencyCallRoutingPolicy](/powershell/module/skype/new-csteamsemergencycallroutingpolicy).

## Edit an emergency call routing policy

### Using the Microsoft Teams admin center

You can edit the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Emergency policies**, and then click the **Call routing policies** tab.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. Make the changes that you want, and then click **Save**.

### Using PowerShell

See [Set-CsTeamsEmergencyCallRoutingPolicy](/powershell/module/skype/set-csteamsemergencycallroutingpolicy).

## Assign a custom emergency call routing policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

See also [Grant-CsTeamsEmergencyCallRoutingPolicy](/powershell/module/skype/grant-csteamsemergencycallroutingpolicy).

## Assign a custom emergency call routing policy to a network site

### Using the Microsoft Teams admin center

You can assign the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and click the **Network sites** tab.
2. Select the site by clicking to the left of the name, and then click **Edit**.
3. Under **Emergency call routing policy**, select the policy, and then click **Save**.

### Using PowerShell

Use the [Set-CsTenantNetworkSite](/powershell/module/skype/set-cstenantnetworksite) cmdlet to assign an emergency call routing policy to a network site.

This example shows how to assign a policy called Emergency Call Routing Policy 1 to the Site1 site.

```PowerShell
Set-CsTenantNetworkSite -identity "site1" -EmergencyCallRoutingPolicy "Emergency Call Routing Policy 1"
```

## Related topics

[Manage emergency calling policies in Teams](manage-emergency-calling-policies.md)

[Teams PowerShell overview](teams-powershell-overview.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)
