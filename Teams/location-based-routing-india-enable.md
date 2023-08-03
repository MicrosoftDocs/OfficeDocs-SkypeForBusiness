---
title: Enable Location-Based Routing for Operator Connect India
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.topic: article
ms.reviewer: roykuntz
ms.date: 02/01/2019
ms.service: msteams
audience: admin
search.appverid: MET150
description: Learn how to enable Location-Based Routing for Operator Connect India, including enabling it for users, network sites, gateway configurations, and calling policies.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-voice
  - Tier1
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Enable Location-Based Routing for Operator Connect India

This article describes how to enable Location-Based Routing for Operator Connect India.

Before you follow the steps in this article, make sure you've read [Plan Location-Based Routing for India](location-based-routing-india-plan.md) and completed the steps in [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md). For more information about managing your network topolocy, see [Manage your network topology](manage-your-network-topology.md).

After you deploy Operator Connect India and set up network regions, sites, and subnets, you're ready to enable Location-Based Routing for your network sites. 

You can use the [Teams admin center](#using-the-microsoft-teams-admin-center) or [PowerShell](#using-powershell) to enable Location-Based Routing. To complete the steps in this article, you'll need some familiarity with PowerShell cmdlets. To learn more, see [Teams PowerShell Overview](teams-powershell-overview.md)



## Use the Microsoft Teams admin center

To enable Location-Based Routing for your sites that need to enforce routing restrictions, follow these steps: 

1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**.

2. Select a network site, click **Edit**, and then turn on **Location based routing**.  

## Use PowerShell

To enable Location-Based Routing to your network sites that need to enforce routing restrictions, use the [Set-CsTenantNetworkSite](/powershell/module/skype/set-cstenantnetworksite?view=skype-ps) cmdlet.

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



## Related topics

- [Plan Location-Based Routing for India](location-based-routing-india-plan.md)
- [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md)
- [Manage your network topology](manage-your-network-topology.md)
