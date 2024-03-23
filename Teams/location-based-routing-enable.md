---
title: Enable Location-Based Routing for Direct Routing
ms.author: crowe
author: CarolynRowe
manager: pamgreen
ms.topic: article
ms.reviewer: roykuntz
ms.date: 08/10/2023
ms.service: msteams
audience: admin
search.appverid: MET150
description: Learn how to enable Location-Based Routing for Direct Routing, including enabling it for users, network sites, gateway configurations, and calling policies.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Enable Location-Based Routing for Direct Routing

This article describes how to enable Location-Based Routing for Direct Routing. Before you follow the steps in this article, make sure you've read [Plan Location-Based Routing for Direct Routing](location-based-routing-plan.md) and completed the steps in [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md).

After you deploy Direct Routing and set up network regions, sites, and subnets, you're ready to enable Location-Based Routing. To complete the steps in this article, you'll need some familiarity with PowerShell cmdlets. To learn more, see [Teams PowerShell Overview](teams-powershell-overview.md)

 You have to enable Location-Based Routing for the following:

- Users
- Network sites
- Gateway configurations
- Calling policies

You can use the [Teams admin center](#using-the-microsoft-teams-admin-center) or [PowerShell](#using-powershell) to enable Location-Based Routing.

## Using the Microsoft Teams admin center

### Enable Location-Based Routing for users

1. Create a voice routing policy and assign PSTN usages to the policy. When you assign PSTN usages to a policy, make sure you do one of the following:

    - Use PSTN usages associated to voice routes that use a PSTN gateway local to the site.

    - Use PSTN usages associated to voice routes that use a PSTN gateway located in a region where Location-Based Routing restrictions aren't needed.

2. Assign the voice routing policy to users who require routing restrictions to be enforced.

To learn more about how to create voice routing policies and assign them to users, see [Manage voice routing policies in Microsoft Teams](manage-voice-routing-policies.md).

### Enable Location-Based Routing for network sites

Enable Location-Based Routing for your sites that need to enforce routing restrictions. To do this, in the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, select a network site, select **Edit**, and then turn on **Location based routing**.  

To learn more, see [Manage your network topology](manage-your-network-topology.md).

### Enable Location-Based Routing for gateways

Enable Location-Based Routing to gateways that route calls to PSTN gateways that route calls to the PSTN, and associate the network site where the gateway is located.

1. In the left navigation of the Teams admin center, go to **Voice** > **Direct Routing**, and then select the **SBCs** tab.

2. Select the SBC, and then select **Edit**.

3. Under **Location based routing and media optimization**, turn on **Enable location based routing**.

4. Specify the gateway site ID, and then set the bypass mode.

5. Select **Save**.

### Enable Location-Based Routing for calling policies

To enforce Location-Based Routing for specific users, set up the user's calling policy to prevent PSTN toll bypass.

To do this, turn on the **Prevent toll bypass and send calls through the PSTN** setting in the calling policy.

1. In the left navigation, go to **Voice** > **Calling policies**.
1. Select the calling policy that you want to edit.
1. Turn on **Prevent toll bypass and send calls through the PSTN**.
1. Select **Save**.

## Using PowerShell

### Enable Location-Based Routing for users

1. To set PSTN usages, use the [Set-CsOnlinePstnUsage](/powershell/module/teams/set-csonlinepstnusage) cmdlet. For multiple usages, separate each usage with a comma.

    ```PowerShell
    Set-CsOnlinePstnUsage -Usage <usages> 
    ```

    For example:

    ```PowerShell
    Set-CsOnlinePstnUsage -Usage "Long Distance", "Local", "Internal" 
    ```

2. To create a voice routing policy to associate the user with the appropriate PSTN usage, use the [New-CsOnlineVoiceRoutingPolicy](/powershell/module/teams/new-csonlinevoiceroutingpolicy) cmdlet.

    ```PowerShell
    New-CsOnlineVoiceRoutingPolicy -Identity <voice routing policy ID> -Description <voice routing policy name> -OnlinePstnUsages <usages> 
    ```

    When you assign PSTN usages to a voice routing policy, make sure you do one of the following:

    - Use PSTN usages associated to voice routes that use a PSTN gateway local to the site.

    - Use PSTN usages associated to voice routes that use a PSTN gateway located in a region where Location-Based Routing restrictions aren't needed.

    The following example creates two new voice routing policies and assigns PSTN usages to them. 

    ```PowerShell
    New-CsOnlineVoiceRoutingPolicy -Identity "DelhiVoiceRoutingPolicy" -Description "Delhi voice routing policy" -OnlinePstnUsages "Long Distance" 
    New-CsOnlineVoiceRoutingPolicy -Identity "HyderabadVoiceRoutingPolicy" -Description " Hyderabad voice routing policy" -OnlinePstnUsages "Long Distance", "Local", "Internal" 
    ```

    The following table shows the voice routing policies defined in this example. 

    |&nbsp;|Voice routing policy 1|Voice routing policy 2|
    |---------|---------|---------|
    |Online voice policy ID   |Delhi online voice routing policy   |Hyderabad online voice routing policy    |
    |Online PSTN usages  |Long Distance  |Long Distance, Local, Internal  |

3. To associate online voice routing policies to users who require routing restrictions to be enforced, use the [Grant-CsOnlineVoiceRoutingPolicy](/powershell/module/teams/grant-csonlinevoiceroutingpolicy) cmdlet.

    ```PowerShell
    Grant-CsOnlineVoiceRoutingPolicy -Identity <User> -Tenant <TenantId>
    ```

### Enable Location-Based Routing for network sites

1. To enable Location-Based Routing and associate voice routing policies to your network sites that need to enforce routing restrictions, use the [Set-CsTenantNetworkSite](/powershell/module/teams/set-cstenantnetworksite) cmdlet.

    ```PowerShell
    Set-CsTenantNetworkSite -Identity <site ID> -EnableLocationBasedRouting <$true|$false>  
    ```

    This example enables Location-Based Routing for the Delhi site and the Hyderabad site.

    ```PowerShell
    Set-CsTenantNetworkSite -Identity "Delhi" -EnableLocationBasedRouting $true  
    Set-CsTenantNetworkSite -Identity "Hyderabad" -EnableLocationBasedRouting $true 
    ```

    The following table shows the sites enabled for Location-Based Routing in this example.

    |&nbsp;|Site 1 (Delhi)  |Site 2 (Hyderabad)  |
    |---------|---------|---------|
    |Site name    |Site 1 (Delhi)    |Site 2 (Hyderabad)|
    |EnableLocationBasedRouting    |True    |True    |
    |Subnets     |Subnet 1 (Delhi)     |Subnet 2 (Hyderabad)     |

### Enable Location-Based Routing for gateways

1. To create a gateway configuration for each gateway or network site, use the [New-CsOnlinePSTNGateway](/powershell/module/teams/new-csonlinepstngateway) cmdlet.

    ```PowerShell
    New-CSOnlinePSTNGateway -Fqdn <FDQN registered for the SBC> -Identity <gateway configuration ID> -SipSignalingPort <listening port used> -Enabled $true 
    ```

    If multiple gateways are associated with a system (for example, Gateway or PBX), modify each gateway to enable Location-Based Routing restrictions.

    The following example creates one gateway configuration for each gateway.

    ```PowerShell
    New-CsOnlinePSTNGateway -Fqdn sbc.contoso.com -Enabled $true -SipSignalingPort 5067 
    ```

    For more information, see [Configure Direct Routing](direct-routing-configure.md).

2. To enable Location-Based Routing for your gateways that need to enforce routing restrictions, use the [Set-CSOnlinePSTNGateway](/powershell/module/teams/set-csonlinepstngateway) cmdlet.

    Enable Location-Based Routing to gateways that route calls to PSTN gateways that route calls to the PSTN, and associate the network site where the gateway is located.

    ```PowerShell
    Set-CSOnlinePSTNGateway -Identity <gateway configuration ID> -GatewaySiteLbrEnabled $true -GatewaySiteID <site ID> 
    ```

   The following example enables Location-Based Routing for each gateway that's associated to PSTN gateways in the Delhi and Hyderabad sites.

    ```PowerShell
    Set-CSOnlinePSTNGateway -Identity sbc.contoso.com  -GatewaySiteLbrEnabled $true –GatewaySiteID "Delhi"
    Set-CSOnlinePSTNGateway -Identity sbc1.contoso.com  -GatewaySiteLbrEnabled $true -GatewaySiteID "Hyderabad" 
    ```

    Don't enable Location-Based Routing for gateways that don't route calls to the PSTN. However, you still have to associate the gateway to the network site where the system is located. This is because Location-Based Routing restrictions need to be enforced for PSTN calls reaching endpoints that are connected through this gateway. In this example, Location-Based Routing isn't enabled for each gateway that's associated to PBX systems in the Delhi and Hyderabad sites.

    ```PowerShell
    Get-CSONlinePSTNGateway -Identity sbc.contoso.com 
 
    Identity: sbc.contoso.com 
    GatewaySiteLbrEnabled: $false 
 
    Get-CSONlinePSTNGateway -Identity sbc2.contoso.com 
 
    Identity: sbc2.contoso.com 
    GatewaySiteLbrEnabled: $false 
    ```

### Enable Location-Based Routing for calling policies

To enforce Location-Based Routing for specific users, set up the users' voice policy to prevent PTSN toll bypass. 

To enable Location-Based routing by preventing PSTN toll bypass, use the [Grant-CsTeamsCallingPolicy](/powershell/module/teams/grant-csteamscallingpolicy) cmdlet.

```PowerShell
Grant-CsTeamsCallingPolicy -PolicyName <policy name> -id <user id> 
```

In this example, we prevent PSTN toll bypass to User1's calling policies.

```PowerShell
Grant-CsTeamsCallingPolicy –PolicyName "AllowCallingPreventTollBypass" -id "User1" 
```

## Related articles

- [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md)
- [Configure calling policies](teams-calling-policy.md)
