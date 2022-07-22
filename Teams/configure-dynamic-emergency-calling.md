---
title: Configure dynamic emergency calling
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection:  
  - M365-voice
  - m365initiative-voice
ms.reviewer: roykuntz
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn how to configure the Microsoft Calling Plans and Phone System Direct Routing dynamic emergency calling feature.
ms.custom: seo-marvel-mar2020
appliesto: 
- Microsoft Teams
---

# Plan and configure dynamic emergency calling 

Dynamic emergency calling for Microsoft Calling Plans, Operator Connect, and Direct Routing provides the capability to configure and route emergency calls and notify security personnel based on the current location of the Teams client.  

Based on the network topology (network elements associated with emergency addresses) that the tenant administrator defines, the Teams client provides network connectivity information in a request to the Location Information Service (LIS). If there's a match, the LIS returns a location to the client.

The Teams client includes location data as part of an emergency call. This data is then used by the emergency service provider to determine the appropriate Public Safety Answering Point (PSAP) and to route the call to that PSAP, which allows the PSAP dispatcher to obtain the caller's location.  

For dynamic emergency calling, the following must occur:

1. The network administrator configures network settings and the LIS to create a network/emergency location map.

2. During startup and periodically afterwards, or when a network connection is changed, the Teams client sends a location request that contains its network connectivity information to the network settings and the LIS.

   - If there's a network settings site match – emergency calling policies are returned to the Teams client from that site. (For more information about policies, see [Configure emergency policies](#configure-emergency-policies)).

   - If there's an LIS match – an emergency location from the network element the Teams client is connected to is returned to the Teams client. The match is performed in the following order with the first matched result being returned:
       - WAP
       - Ethernet switch/port
       - Ethernet switch
       - Subnet

3. When the Teams client makes an emergency call, the emergency location is conveyed to the PSTN network.

The ability to do automatic routing to the appropriate Public Safety Answering Point (PSAP) varies depending on the country of usage of the Teams user.

Microsoft Calling Plans and Operator Connect partners include dynamic emergency routing services for users in the United States and Canada.

For Direct Routing, however, additional configuration is required for routing emergency calls and possibly for partner connectivity. The administrator must ensure that the PSTN gateway routing the emergency call has been configured to add location information to the outgoing INVITE (by setting the parameter PidfloSupported to True on the online PSTN gateway object. In addition the administrator must configure connection to an Emergency Routing Service (ERS) provider (United States and Canada) **OR** configure the Session Border Controller (SBC) for an Emergency Location Identification Number (ELIN) application. For information about ERS providers, see [Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).

This article contains the following sections.

- [Assign emergency addresses](#assign-emergency-addresses)
- [Configure network settings](#configure-network-settings)
- [Configure Location Information Service](#configure-location-information-service)
- [Configure emergency policies](#configure-emergency-policies)
- [Enable users and sites](#enable-users-and-sites)
- [Test emergency calling](#test-emergency-calling)

For more information about emergency calling, including information about emergency addresses and emergency call routing, information specific to countries, and information about network settings and network topology, see the following:

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage network settings for cloud voice features](cloud-voice-network-settings.md)
- [Manage your network topology for cloud voice features](manage-your-network-topology.md)

For more information about which features are available in the government clouds, see [Government support](#government-support) at the end of this article.


## Supported clients

The following clients are currently supported.  Check back often to see updates to this list.

- Teams desktop client for Microsoft Windows
- Teams desktop client for Apple macOS
- Teams mobile client for Apple iOS client version 1.0.92.2019121004 and App Store version 1.0.92 and greater
- Teams mobile client for Android client and Google Play store version 1416/1.0.0.2019121201 and greater
- Teams phone version 1449/1.0.94.2019110802 and greater
- Teams Rooms version 4.4.25.0 and greater

> [!NOTE]
> Subnet and WiFi-based locations are supported on all supported Teams clients. <br><br>
> Ethernet/Switch (LLDP) is supported on:
> - Windows versions 10.0 and later at this time.<br>
> - Mac OS, which requires [LLDP enablement software](https://www.microsoft.com/download/details.aspx?id=103383).<br>
> - Teams phone with Teams app version 1449/1.0.94.2021110101 and later.

> [!NOTE]
> Dynamic emergency calling, including security desk notification, isn't supported on the Teams web client. To prevent users from using the Teams web client to call PSTN numbers, you can set a Teams calling policy and turn off the **Allow web PSTN calling** setting. To learn more, see [Calling policies in Teams](teams-calling-policy.md) and [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy?view=skype-ps). 

> [!NOTE]
> 3PIP phones do not support dynamic emergency calling. 



## Assign emergency addresses

You can assign emergency addresses as follows:

- To Calling Plan users.

- To Operator Connect users&mdash;depending on the capabilities assigned to the number when the carrier uploads them into a customer's inventory.

- To the network identifiers that are required for dynamically obtaining a location. 

To support automated routing of emergency calls within the United States, you must ensure that the emergency locations that are assigned to network identifiers include the associated geo codes. (Emergency addresses without geo codes can't be assigned to the network identifiers that are required for dynamic locations.)

Azure Maps is used for location-based services. When you enter an emergency address by using the Microsoft Teams admin center, Teams checks Azure Maps for the address:

- If a match is found, the geo codes are automatically included.

- If a match isn't found, you will have the opportunity to manually create an emergency address. You can use the PIN drop feature to do this. 

> [!NOTE]
> Emergency addresses that are more than a couple of years old cannot be assigned to network identifiers. You will need to re-create older addresses.

You add and assign emergency addresses in the Microsoft Teams admin center or by using PowerShell. For more information, see [Add an emergency location for your organization](add-change-remove-emergency-location-organization.md) and [Assign an emergency location for a user](assign-change-emergency-location-user.md).

## Configure network settings

Network settings are used to determine the location of a Teams client, and to dynamically obtain emergency calling policies and an emergency location. You can configure network settings according to how your organization wants emergency calling to function.

Network settings include sites that include a collection of subnets and these are used exclusively for dynamic policy assignment to users. For example, an emergency calling policy and an emergency call routing policy might be assigned to the "Redmond site" so that any user that roams from home or another Microsoft location is configured with emergency numbers, routing, and security desk specific to Redmond.  

Trusted IP addresses contain a collection of the internet external IP addresses of the enterprise network and are used to determine if the user's endpoint is inside the corporate network. An attempt to obtain a dynamic policy or location will only be made if the user's external IP address matches an IP address in the trusted IP address.

For more information about IP addresses, network regions, sites, and subnet addresses,  see [Network settings for cloud voice features](cloud-voice-network-settings.md).

You configure network settings in the Microsoft Teams admin center or by using PowerShell. To learn more, see [Manage your network topology for cloud voice features](manage-your-network-topology.md).

Note that it can take some time (up to a couple of hours) for some changes to network settings (such as a new address, network identifier, and so on) to propagate and be available to Teams clients.  

> [!Note]
> Subnets can also be defined in LIS and can be associated with an emergency location.  LIS subnets must be defined by the Network ID matching the subnet IP range assigned to clients. For example, the network ID for a client IP/mask of 10.10.10.150/25 is 10.10.10.128. For more information, see [Understand TCP/IP addressing and subnetting basics](/troubleshoot/windows-client/networking/tcpip-addressing-and-subnetting).

> [!Important]
> Network configuration setting lookups are not supported with cloud proxy service deployments that modify the source IP addresses from Teams clients.



**For Calling Plan and Operator Connect users:**

- If dynamic configuration of security desk notification is required, you must configure both trusted IP addresses and network sites.

- If only dynamic locations are required, you must configure only trusted IP addresses; configuring network settings isn't required.

- If neither are required, configuring network settings isn't required. 

**For Direct Routing users:**

- If dynamic enablement of emergency calling or dynamic configuration of security desk notification is required, then you must configure both Trusted IP addresses and network sites.

- If only dynamic locations are required, you must configure only trusted IP addresses; configuring metwork settings isn't required.

- If neither are required, configuring network settings isn't required.


## Configure Location Information Service

A Teams client obtains emergency addresses from the locations associated with different network identifiers. 

For a client to obtain a location, you must populate the LIS with network identifiers (subnets, WAPs, switches, ports) and emergency locations. You can do this in the Microsoft Teams admin center or by using PowerShell.

### Using the Microsoft Teams admin center

1. In the left navigation, go to **Locations** > **Networks & locations**.
2. Click the tab that represents the network identifier that you want to add. For example, click **Subnets**, **Wi-Fi access points**, **Switches**, or **Ports**. Then click **Add**.
3. Complete the fields, add an emergency location, and then click **Apply**.

### Using PowerShell

Use the following cmdlets to add ports, switches, subnets, and WAPs to the LIS.

- [Get](/powershell/module/skype/get-csonlinelissubnet?view=skype-ps), [Set](/powershell/module/skype/set-csonlinelissubnet?view=skype-ps), [Remove](/powershell/module/skype/remove-csonlinelissubnet?view=skype-ps) -CsOnlineLisSubnet
- [Get](/powershell/module/skype/get-csonlinelisport?view=skype-ps), [Set](/powershell/module/skype/set-csonlinelisport?view=skype-ps), [Remove](/powershell/module/skype/remove-csonlinelisport?view=skype-ps) -CsOnlineLisPort
- [Get](/powershell/module/skype/get-csonlineliswirelessaccesspoint?view=skype-ps), [Set](/powershell/module/skype/set-csonlineliswirelessaccesspoint?view=skype-ps), [Remove](/powershell/module/skype/remove-csonlineliswirelessaccesspoint?view=skype-ps) -CsOnlineLisWirelessAccessPoint
- [Get](/powershell/module/skype/get-csonlinelisswitch?view=skype-ps), [Set](/powershell/module/skype/set-csonlinelisswitch?view=skype-ps), [Remove](/powershell/module/skype/remove-csonlinelisswitch?view=skype-ps) -CsOnlineLisSwitch

>[!Important]
>If subnets are being used as part of network sites, they must be redefined in the Location Information Service to render dynamic locations.

## Configure emergency policies

Use the following policies to configure emergency calling. You can manage these policies in the Microsoft Teams admin center or by using PowerShell.

- **Emergency call routing policy – Applies only to Direct Routing**. This policy configures the emergency numbers, masks per number if desired, and the PSTN route per number. You can assign this policy to users, to network sites, or to both. To  learn more, see [Manage emergency call routing policies for Direct Routing](manage-emergency-call-routing-policies.md).  

   (Calling Plan and Operator Connect users are automatically enabled for emergency calling with the emergency numbers from the country based upon their Microsoft 365 or Office 365 usage location.)

- **Emergency calling policy - Applies to Calling Plans, Operator Connect, and Direct Routing.** This policy configures the security desk notification experience when an emergency call is made. You can set who to notify and how they are notified. For example, to automatically notify your organization's security desk and have them listen in on emergency calls.  This policy can either be assigned to users or network sites or both. To learn more, see [Manage emergency calling policies in Teams](manage-emergency-calling-policies.md).

## Enable users and sites

You can assign emergency call routing policies and emergency calling policies to users and to sites. Keep in mind that emergency call routing policies apply to Direct Routing only. (Although it's possible to assign this policy to a Calling Plan or Operator Connect user, the policy will have no effect.)

You assign policies in the Microsoft Teams admin center or by using PowerShell. To learn more, see:

- [Manage emergency call routing policies for Direct Routing](manage-emergency-call-routing-policies.md)
- [Manage emergency calling policies in Teams](manage-emergency-calling-policies.md)

The following are PowerShell examples:

To enable a specific user for security desk notification, use the following command:

```PowerShell
Grant-CsTeamsEmergencyCallingPolicy -Identity user1 -PolicyName SecurityDeskNotification
```

To assign a policy called "Contoso Emergency Calling Policy 1" to Site 1, use the following command:

```PowerShell
Set-CsTenantNetworkSite -identity "site1" -EmergencyCallingPolicy "Contoso Emergency Calling Policy 1"
```

To enable a specific Direct Routing user for emergency calling, use the following command:

```PowerShell
Grant-CsTeamsEmergencyCallRoutingPolicy -Identity user1 -PolicyName UnitedStates
```

To assign a policy called "Contoso New York Emergency Call Routing" to Site 1, use the following command:

```PowerShell
Set-CsTenantNetworkSite -identity "site1" -EmergencyCallRoutingPolicy "Contoso New York Emergency Call Routing"
```

If you assigned an emergency calling policy to a network site and to a user, and if that user is at that network site, the policy that's assigned to the network site overrides the policy that's assigned to the user.

## Test emergency calling

Some Emergency Routing Service Providers (ERSPs) in the United States offer an emergency calling test bot.

- **Calling Plan and Operator Connect users in the United States or Canada** can use the predefined test emergency number 933 to validate their emergency calling configuration. This number is routed to a bot, which then echoes back the caller phone number (calling line ID), emergency address or location, and whether the call would be automatically routed to the PSAP or screened first.

- **Direct Routing customers in the United States** should coordinate with their ERSP for a test service.

## Government support

The following table shows support for dynamic emergency calling in the government clouds:

| Cloud | Availability |
| :------------|:-------|
| World Wide Multi Tenant | Available on all Teams clients |
| GCC | Available on all Teams clients |
| GCCH | -Available on Teams desktop <br> -Available on Teams mobile clients <br> -Available on Teams phone app version: 1449/1.0.94.2022061702 |
| DoD | Pending |

 ## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Manage emergency call routing policies ](manage-emergency-call-routing-policies.md)
- [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Assign or change an emergency location for your user](assign-change-emergency-location-user.md)
- [Network settings for cloud voice features](cloud-voice-network-settings.md)
- [Manage your network topology for cloud voice features](manage-your-network-topology.md)
