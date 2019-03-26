---
title: Enable Location-Based Routing for Direct Routing
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.date: 2/1/2019
ms.topic: article
ms.reviewer: roykuntz
ms.service: msteams
search.appverid: MET150
description: Learn how to enable Location-Based Routing for Direct Routing.
localization_priority: Normal
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
- M365-voice
appliesto: 
- Microsoft Teams
---

# Enable Location-Based Routing for Direct Routing

> [!INCLUDE [Preview customer token](includes/preview-feature.md)]

Before you follow the steps in this article, make sure you've read [Plan Location-Based Routing for Direct Routing](location-based-routing-plan.md) and completed the steps in [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md).

This article describes how to enable Location-Based Routing for Direct Routing. After you deploy Phone System Direct Routing and set up network regions, sites, and subnets, you're ready to enable Location-Based Routing. To complete the steps in this article, you'll need some familiarity with PowerShell cmdlets. To learn more, see [Teams PowerShell Overview](teams-powershell-overview.md).

 You have to enable Location-Based Routing for the following:
- Users
- Network sites
- Gateway configurations
- Calling policies

## Enable Location-Based Routing for users

1. Use the [Set-CsOnlinePstnUsage](https://docs.microsoft.com/powershell/module/skype/set-csonlinepstnusage?view=skype-ps) cmdlet to set PSTN usages. For multiple usages, separate each usage with a comma.

    ```
    Set-CsOnlinePstnUsage -Usage <usages> 
    ```
    For example:
    ```
    Set-CsOnlinePstnUsage -Usage "Long Distance", "Local", "Internal" 
    ```
2. Use the [New-CsOnlineVoiceRoutingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/new-csonlinevoiceroutingpolicy?view=skype-ps) cmdlet to create a voice routing policy to associate the user with the appropriate PSTN usages.

    ```
    New-CsOnlineVoiceRoutingPolicy -Identity <voice routing policy ID> -Description <voice routing policy name> -OnlinePstnUsages <usages> 
    ```
    
    When you assign PSTN usages to a voice routing policy, make sure you do one of the following:
    - Use PSTN usages associated to voice routes that use a PSTN gateway local to the site
    - Use PSTN usages associated to voice routes that use a PSTN gateway located in a region where Location-Based Routing restrictions aren't needed.

    In this example, we create two new voice routing policies and assign PSTN usages to them. 

    ```
    New-CsOnlineVoiceRoutingPolicy -Identity "DelhiVoiceRoutingPolicy" -Description "Delhi voice routing policy" -OnlinePstnUsages "Long Distance" 
    New-CsOnlineVoiceRoutingPolicy -Identity "HyderabadVoiceRoutingPolicy" -Description " Hyderabad voice routing policy" -OnlinePstnUsages "Long Distance", "Local", "Internal" 
    ```
    The following table shows the voice routing policies defined in this example. 
    
    ||Voice routing policy 1|Voice routing policy 2|
    |---------|---------|---------|
    |Online voice policy ID   |Delhi online voice routing policy   |Hyderabad online voice routing policy    |
    |Online PSTN usages  |Long Distance  |Long Distance, Local, Internal  |

3. Use the [Grant-CsOnlineVoiceRoutingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csonlinevoiceroutingpolicy?view=skype-ps) cmdlet to associate online voice routing policies to users who require routing restrictions to be     enforced.
    ```
    Grant-CsOnlineVoiceRoutingPolicy -Identity <User> -Tenant <TenantId>
    ```
## Enable Location-Based Routing for network sites
1.  Use the [Set-CsTenantNetworkSite](https://docs.microsoft.com/powershell/module/skype/set-cstenantnetworksite?view=skype-ps) cmdlet to enable Location-Based Routing and associate voice routing policies to your network sites that need to enforce routing restrictions.
    ```
    Set-CsTenantNetworkSite -Identity <site ID> -EnableLocationBasedRouting <$true|$false>  
    ```

    In this example, we enable Location-Based Routing for the Delhi site and the Hyderabad site. 

    ```
    Set-CsTenantNetworkSite -Identity "Delhi" -EnableLocationBasedRouting $true  
    Set-CsTenantNetworkSite -Identity "Hyderabad" -EnableLocationBasedRouting $true 
    ```
    The following table shows the sites enabled for Location-Based Routing in this example.

    ||Site 1 (Delhi)  |Site 2 (Hyderabad)  |
    |---------|---------|---------|
|Site name    |Site 1 (Delhi)    |Site 2 (Hyderabad)   
    |EnableLocationBasedRouting    |True    |True    |
    |Subnets     |Subnet 1 (Delhi)     |Subnet 2 (Hyderabad)     |

## Enable Location-Based Routing for gateways
1. Use the [New-CsOnlinePSTNGateway](https://docs.microsoft.com/powershell/module/skype/new-csonlinepstngateway?view=skype-ps) cmdlet to create a gateway configuration for each gateway or network site. 

    ```
    New-CSOnlinePSTNGateway -Fqdn <FDQN registered for the SBC> -Identity <gateway configuration ID> -SipSignallingPort <listening port used> -Enabled $true 
    ```
    If multiple gateways are associated with a system (for example, Gateway or PBX), modify each gateway to enable Location-Based Routing restrictions. 

    In this example, we create one gateway configuration for each gateway. 
    ```
    New-CsOnlinePSTNGateway -Fqdn sbc.contoso.com -Enabled $true -SipSignallingPort 5067 
    ```
    For more information, see [Configure Direct Routing](direct-routing-configure.md).
    
2. Use the [Set-CSOnlinePSTNGateway](https://docs.microsoft.com/powershell/module/skype/set-csonlinepstngateway?view=skype-ps) cmdlet to enable Location-Based Routing for your gateways that need to enforce routing restrictions. 

    Enable Location-Based Routing to gateways that route calls to PSTN gateways that route calls to the PSTN, and associate the network site where the gateway is located.

    ```
    Set-CSOnlinePSTNGateway -Identity <gateway configuration ID> -GatewaySiteLbrEnabled $true -GatewaySiteID <site ID> 
    ```

    In this example, we enable Location-Based Routing for each gateway that's associated to PSTN gateways in the Delhi and Hyderabad sites. 
    ```
    Set-CSOnlinePSTNGateway -Identity sbc.contoso.com  -GatewaySiteLbrEnabled $true –GatewaySiteID “Delhi”
    Set-CSOnlinePSTNGateway -Identity sbc1.contoso.com  -GatewaySiteLbrEnabled $true -GatewaySiteID “Hyderabad” 
    ```
    Don't enable Location-Based Routing for gateways that don't route calls to the PSTN. However, you still have to associate the gateway to the network site where the system is located. This is because Location-Based Routing restrictions need to be enforced for PSTN calls reaching endpoints that are connected via this gateway. In this example, Location-Based Routing isn't enabled for each gateway that's associated to PBX systems in the Delhi and Hyderabad sites.

    ```
    Get-CSONlinePSTNGateway -Identity sbc.contoso.com 
 
    Identity: sbc.contoso.com 
    GatewaySiteLbrEnabled: $false 
 
    Get-CSONlinePSTNGateway -Identity sbc2.contoso.com 
 
    Identity: sbc2.contoso.com 
    GatewaySiteLbrEnabled: $false 
    ```

    Endpoints connected to systems that don't route calls to the PSTN (for example, a PBX) will have similar restrictions as endpoints of Teams users enabled for Location-Based Routing. This means that these users can place and receive calls to and from Teams users regardless of the user’s location. They can also place and receive calls to and from other systems that don't route calls to the PSTN network (for example, an endpoint connected to a different PBX) regardless of the network site to which the system is associated. All inbound calls, outbound calls, call transfers and call forwarding that involve PSTN endpoints will be subject to Location-Based Routing enforcements. These calls must use only PSTN gateways that are defined as local to such systems. 

    The following table shows the gateway configuration of four gateways in two different network sites: two connected to PSTN gateways and two connected to PBX systems. 

    ||GatewaySiteLbrEnabled   |NetworkSiteID  |
    |---------|---------|---------|
    |PstnGateway:Gateway 1 DEL-GW    |    True     |   Site 1 (Delhi)      |
    |PstnGateway:Gateway 2 HYD-GW     |   True      |      Site 2 (Hyderabad)   |
    |PstnGateway:Gateway 3 DEL-PBX    |    False     |     Site 1 (Delhi)    |
    |PstnGateway:Gateway 4 HYD-PBX    |    False     |    Site 2 (Hyderabad)     |

## Enable Location-Based Routing for calling policies

To enforce Location-Based Routing for specific users, set up the users' voice policy to prevent PTSN toll bypass. 

Use the [Grant-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamscallingpolicy?view=skype-ps) cmdlet to enable Location-Based routing by preventing PSTN toll bypass.

```
Grant-CsTeamsCallingPolicy -PolicyName <policy name> -id <user id> 
```
In this example, we prevent PSTN toll bypass to User1's calling policies. 

```
Grant-CsTeamsCallingPolicy –PolicyName “AllowCallingPreventTollBypass” -id “User1” 
```

### Related topics
- [Plan Location-Based Routing for Direct Routing](location-based-routing-plan.md)
- [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md)
- [Location-Based Routing terminology](location-based-routing-terminology.md)
