---
title: Manage your network topology in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: jastark, roykuntz
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- M365-voice
f1keywords: 
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to configure network settings for cloud voice features in Microsoft Teams. 
---

# Manage your network topology in Microsoft Teams

If your organization is deploying [Location-Based Routing for Direct Routing](location-based-routing-plan.md) or enhanced emergency services, you must configure network settings for use with these cloud voice features in Microsoft Teams. These features have common configuration requirements for which you must define network regions, network sites, and subnets. For example, you must associate each network site in your topology with a network region and associate each subnet with a network site. To learn more about these terms, see [Network settings for cloud voice features](call-routing-terminology.md).

 You configure network settings by going to **Locations** > **Network topology** in the Microsoft Teams admin center or by using Windows PowerShell.

Manage your network topology using the Microsoft Teams admin center


Manage your network topology using PowerShell 

Define network regions
Define network sites
Definte network subnets
Define external subnets

## Configure network settings in the Microsoft Teams admin center

### Configure network sites, network regions, and subnets

You define network regions, network sites, and subnets on the **Network sites** tab of the **Network topology** page of the Microsoft Teams admin center.

### Add and configure a network site

1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Network sites** tab.
2. Click **New**, and then enter a name and description for the site.

    ![Screenshot of the Add network site page](media/manage-network-topology-add-site.png)

3. To associate the site with a network region, click **Link network region**, select an existing region or click **Add** to add a region, and then click **Link**.  
4. To enable Location-Based Routing for the site, turn on **Location based routing**.
5. To assign emergency services policies to the site, do one or both of the following:

    - If your organization uses Calling Plans or deployed Phone System Direct Routing, under **Emergency calling policy**, select the policy that you want.
    - If your organization deployed Phone System Direct Routing, under **Emergency call routing policy**, select the  policy that you want.

6. To associate a subnet with the site, under **Subnets**, click **Add subnets**. Specify the IP version, IP address, network range, add a description, and then click **Apply**.
7. Click **Save**.

### Modify a network site

1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Network sites** tab.
2. Select the site by clicking to the left of the site name, and then click **Edit**.
3. Make the changes that you want, and then click **Save.**

### Manage trusted IP addresses

You manage trusted IP addresses on the **Trusted IPs** tab on the **Network topology** page of the Microsoft Teams admin center.

#### Add a trusted IP address

1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Trusted IPs** tab.
2. Click **New**.
3. In the **Add trusted IP address** pane, specify the IP version, IP address, network range, add a description, and then click **Apply**.

    ![Screenshot of the Add trusted IP address pane](media/manage-network-topology-add-trusted-ip.png)

#### Edit a trusted IP address

1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Trusted IPs** tab.
2. Select the IP address by clicking to the left of it, and then click **Edit**.
3. In the **Edit trusted IP address** pane, make the changes that you want, and then click **Apply**.

===========================

## Manage network sites

A network site represents a location where your organization has a physical venue, such as an office, a set of buildings, or a campus. Network sites are defined as a collection of IP subnets.

Each network site must be associated with a network region, which is a collection of network sites. And, each subnet in your topology must be associated with a specific network site because subnet information is used to determine the network site on which an endpoint is located while a new session is initiated. When the location of the each party in a session is known, cloud voice features can apply that information to determine how to handle call setup or routing.

You can also enable Location-Based Routing for a site and assign [emergency calling](manage-emergency-calling-policies.md) and [emergency call routing](manage-emergency-call-routing-policies.md) policies to a site.

### Using the Microsoft Teams admin center

#### Add and configure a network site

1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Network sites** tab.
2. Click **New**, and then enter a name and description for the site.

    ![Screenshot of the Add network site page](media/manage-network-topology-add-site.png)

3. To associate the site with a network region, click **Link network region**, select an existing region or add a region, and then click **Link**.  
4. To enable Location-Based Routing for the site, turn on **Location based routing**.
5. To assign emergency services policies to the site, do one or both of the following:

    - If your organization uses Calling Plans or deployed Phone System Direct Routing, under **Emergency calling policy**, select the policy that you want.
    - If your organization deployed Phone System Direct Routing, under **Emergency call routing policy**, select the  policy that you want.

6. To associate a subnet with the site, under **Subnets**, click **Add subnets**. Specify the IP version, IP address, network range, add a description, and then click **Apply**.
7. Click **Save**.

#### Modify a network site

1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Network sites** tab.
2. Select the site by clicking to the left of the site name, and then click **Edit**.
3. Make the changes that you want, and then click **Save.**

### Using PowerShell

Use the [New-CsTenantNetworkSite](https://docs.microsoft.com/powershell/module/skype/new-cstenantnetworksite?view=skype-ps) cmdlet to create a network site.

```
New-CsTenantNetworkSite -NetworkSiteID <site ID> -NetworkRegionID <region ID>
```

In this example, we create two new network sites, Delhi and Hyderabad, in the India region.
```

New-CsTenantNetworkSite -NetworkSiteID "Delhi" -NetworkRegionID "India"
New-CsTenantNetworkSite -NetworkSiteID "Hyderabad" -NetworkRegionID "India"

```
The following table shows the network sites defined in this example.

||Site 1 |Site 2 |
|---------|---------|---------|
|Site ID    |    Site 1 (Delhi)     |  Site 2 (Hyderabad)       |
|Region ID  |     Region 1 (India)    |   Region 1 (India)      |

Also see [Set-CsTenantNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/set-cstenantnetworksite?view=skype-ps).

## Manage trusted IP addresses

Trusted external IP addresses are the internet external IP addresses of the enterprise network and are exempt from certain designated security options. They determine whether the user’s endpoint is inside the corporate network before checking for a specific site match.

### Using the Microsoft Teams admin center

#### Add a trusted IP address

1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Trusted IPs** tab.
2. Click **New**.
3. In the **Add trusted IP address** pane, specify the IP version, IP address, network range, add a description, and then click **Apply**.

    ![Screenshot of the Add trusted IP address pane](media/manage-network-topology-add-trusted-ip.png)

#### Edit a trusted IP address

1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Trusted IPs** tab.
2. Select the IP address by clicking to the left of it, and then click **Edit**.
3. In the **Edit trusted IP address** pane, make the changes that you want, and then click **Apply**.

### Using PowerShell

See [New-CsTenantTrustedIPAddress](https://docs.microsoft.com/powershell/module/skype/new-cstenanttrustedipaddress?view=skype-ps), and [Set-CsTenantTrustedIPAddress](https://docs.microsoft.com/en-us/powershell/module/skype/set-cstenanttrustedipaddress?view=skype-ps).

## Related topics

- [Plan and configure dynamic emergency calling for Calling Plans](configure-dynamic-emergency-calling.md)
- [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md)
- [Teams PowerShell overview](teams-powershell-overview.md)