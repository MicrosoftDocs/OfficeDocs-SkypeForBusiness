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
ms.reviewer: roykuntz
localization_priority: Normal
search.appverid: MET150
description: Configure dynamic emergency calling
appliesto: 
- Microsoft Teams
---

# Plan and configure dynamic emergency calling 

Dynamic emergency calling for Microsoft Calling Plans and Phone System Direct Routing provides the capability to configure and route emergency calls and notify security personnel based on the current location of the Teams client.  

Based on the network topology that the tenant administrator defines, the Teams client provides network connectivity information in a request to the Location Information Service (LIS).  If there is a match, the LIS returns a location to the client. This location data is trasmitted back to the client.  

The Teams client includes location data as part of an emergency call. This data is then used by the emergency service provider to determine the appropriate Public Safety Answering Point (PSAP) and to route the call to that PSAP, which allows the PSAP dispatcher to obtain the caller's location.  

For dynamic emergency calling, the following must occur:

1. The network administrator configures network settings and the LIS to create a network/emergency location map.

   For Direct Routing, additional configuration is required for routing emergency calls and possibly for partner connectivity. The administrator must configure connection to an Emergency Routing Service (ERS) provider (United States) **OR** configure the Session Border Controller (SBC) for an Emergency Location Identification Number (ELIN) application.

2. During startup and periodically afterwards, or when a network connection is changed, the Teams client sends a location request that contains its network connectivity information to the network settings and the LIS.

   - If there is a network settings site match – emergency calling policies are returned to the Teams client from that site. (For more information about policies, see [Configure emergency policies](#configure-emergency-policies)).

   - If there is an LIS match – an emergency location from the network element the Teams client is connected to is returned to the Teams client.

3. When the Teams client makes an emergency call, the emergency location is conveyed to the PSTN network.

   For Direct Routing, the administrator msut configure the SBC to send emergency calls to the ERS provider or configure the SBC ELIN application.

This article contains the following sections.

- [Configure emergency addresses](#assign-emergency-addresses)
- [Configure network settings](#configure-network-settings)
- [Configure Location Information Service](#configure-location-information-service)
- [Configure emergency policies](#configure-emergency-policies)
- [Enable users and sites](#enable-users-and-sites)
- [Test emergency calling](#test-emergency-calling)


The ability to do automatic routing to the appropriate Public Safety Answering Point (PSAP) varies depending on the country of usage of the Teams user. 

For more information about emergency calling--including information about emergency addresses and emergency call routing, information specific to countries, and information about network settings and network topology--see the following:

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage network settings for cloud voice features](cloud-voice-network-settings.md)
- [Manage your network topology for cloud voice features](manage-your-network-topology.md)


## Supported clients

The following clients are currently supported.  Check back often to see updates to this list.

- Teams desktop client for Windows
- Teams desktop client for Mac

## Assign emergency addresses

You can assign emergency addresses to both Calling Plan users and to the network identifiers that are required for dynamically obtaining a location. (Subnet and WiFi AP are supported; support for Ethernet switch/port is pending).

To support automated routing of emergency calls within the United States, you must ensure that the emergency locations that are assigned to network identifiers include the associated geo codes. (Emergency addresses without geo codes cannot be assigned to the network identifiers that are required for dynamic locations.)

Azure Maps is used for location-based services.  When you enter an emergency address by using the Microsoft Teams admin center, Teams checks Azure Maps for the address:

- If a match is found, the geo codes are automatically included.

- If a match is not found, you will have the opportunity to manually create an emergency address. You can use the PIN drop feature to do this.   

This means that if an existing emergency location that is created for assigning to Calling Plan users is intended for a dynamic location, the same address needs to be re-created to include the geo codes. To distinguish between the two locations, you should include a different description. The new emergency location can be assigned to the users who have the old location. When fully migrated, the old location can be deleted.

For more information about configuring emergency addresses, see [Add an emergency location for your organization](add-change-remove-emergency-location-organization.md) and [Assign an emergency location for your user](assign-change-emergency-location-user.md).

## Configure network settings

Network settings are used to determine the location of a Teams client, and to dynamically obtain emergency calling policies and an emergency location. You can configure network settings according to how your organization wants emergency calling to function.

Network settings include sites that include a collection of subnets--these are used exclusively for dynamic policy assignment to users.  For example, a TeamsEmergencyCalling Policy and TeamsEmergencyCallRouting Policy might be assigned to the “Redmond site” so that any user that roams from home or another Microsoft location is configured with emergency numbers, routing, and security desk specific to Redmond.  

>[!Note]
>Subnets can also be defined in LIS and can be associated with an emergency location.  

Keep the following definitions in mind:

- Trusted IP’s contain a collection of the Internet external IPs of the enterprise network and are used to determine if the user’s endpoint is inside the corporate network. An attempt to obtain a dynamic policy or location will only be made if the user’s external IP matches an IP in the Trusted IP address. A match can be made against either IPv4 or IPv6 IP addresses and is dependent upon the format of the IP packet sent to the network settings.  (If a public IP address has both IPv4 and IPv6, you need to add both as trusted IP addresses.)

- A network region contains a collection of network sites. 

- A network site represents a location where your organization has a physical value, such as an office, a set of buildings, or a campus. These sites are defined as a collection of IP subnets.

- A network subnet must be associated with a specific network site. A client's location is determined based on the network subnet and the associated network site.  

For more information, see [Network settings for cloud voice features](cloud-voice-network-settings.md) and [Manage your network topology for cloud voice features](manage-your-network-topology.md).

Note that it can take some time (up to a couple of hours) for some changes to network settings (such as a new address, network identifier, and so on) to propagate and be available to Teams clients.  

**For Calling Plan users:**

- If dynamic configuration of security desk notification is required, then you must configure both Trusted IP addresses and network sites.

- If only dynamic locations are required, then you must configure only Trusted IP addresses. 

- If neither are required, then configuration of network settings is not required. 

**For Direct Routing users:**

- If dynamic enablement of emergency calling or dynamic configuration of security desk notification is required, then you must configure both Trusted IP addresses and network sites.

- If only dynamic locations are required, then you must configure only Trusted IP addresses.

- If neither are required, then configuration of network settings is not required.


## Configure Location Information Service

A Teams client obtains emergency addresses from the locations associated with different network identifiers. Both subnets and Wireless Access Points (WAPs) are supported. (Support for Ethernet switch/port is pending.)

For a client to obtain a location, you must populate the Location Information Service (LIS) with network identifers and emergency locations by using the following cmdlets:  


- [Get](https://docs.microsoft.com/powershell/module/skype/get-csonlinelisport?view=skype-ps), [Set](https://docs.microsoft.com/powershell/module/skype/set-csonlinelisport?view=skype-ps), [Remove](https://docs.microsoft.com/powershell/module/skype/remove-csonlinelisport?view=skype-ps) -CsOnlineLisPort
- [Get](https://docs.microsoft.com/powershell/module/skype/get-csonlinelisswitch?view=skype-ps), [Set](https://docs.microsoft.com/powershell/module/skype/set-csonlinelisswitch?view=skype-ps), [Remove](https://docs.microsoft.com/powershell/module/skype/remove-csonlinelisswitch?view=skype-ps) -CsOnlineLisSwitch
- [Get](https://docs.microsoft.com/powershell/module/skype/get-csonlinelissubnet?view=skype-ps), [Set](https://docs.microsoft.com/powershell/module/skype/set-csonlinelissubnet?view=skype-ps), [Remove](https://docs.microsoft.com/powershell/module/skype/remove-csonlinelissubnet?view=skype-ps) -CsOnlineLisSubnet
- [Get](https://docs.microsoft.com/powershell/module/skype/get-csonlineliswirelessaccesspoint?view=skype-ps), [Set](https://docs.microsoft.com/powershell/module/skype/set-csonlineliswirelessaccesspoint?view=skype-ps), [Remove](https://docs.microsoft.com/powershell/module/skype/remove-csonlineliswirelessaccesspoint?view=skype-ps
) -CsOnlineLisWirelessAccessPoint 


>[!Important] 
>If subnets are being used as part of network sites, they must be redefined in the Location Information Service to render dynamic locations.


## Configure emergency policies

You use the following policies to configure emergency calling:

- **TeamsEmergencyCallRoutingPolicy** – Applies only to Direct Routing. This policy configures the emergency numbers, masks per number if desired, and the PSTN route per number.  You can assign this policy to users, to network sites, or to both. (Calling Plans Teams clients are automatically enabled for emergency calling with the emergency numbers from the country based upon their Office 365 usage location.)  You manage this policy by using the New-, Set-, and Grant-CsTeamsEmergencyCallRouting cmdlets. 

- **TeamsEmergencyCallingPolicy** - Applies to Calling Plan and Direct Routing. This policy configures the security desk notification experience when an emergency call is made. You can set who to notify and how they are notified. For example, to automatically notify your organization's security desk and have them listen in on emergency calls.  This policy can either be assigned to users or network sites or both. You manage this policy by using the New-, Set- and Grant-CsTeamsEmergencyCallingPolicy  cmdlets. 

For more information, see [Manage emergency calling policies in Teams](manage-emergency-calling-policies.md) and [Manage emergency call routing policies for Direct Routing](manage-emergency-call-routing-policies.md).


## Enable users and sites

You can assign **TeamsEmergencyCalling** and **TeamsEmergencyCallROuting** policies to users and to sites.  

The TeamsEmergencyCallRouting policy applies to Direct Routing only. (Although it's possible to assign this policy to a Calling Plan user, the policy will have no effect.)

For example, to enable a specific user for security desk notification, use the following command:

```
Grant-CsTeamsEmergencyCallingPolicy -Identity user1 -PolicyName SecurityDeskNotification
```

To assign a policy called "Contoso Emergency Calling Policy 1" to Site 1, use the following command:

```
Set-CsTenantNetworkSite -identity "site1" -EmergencyCallingPolicy "Contoso Emergency Calling Policy 1"
```

To enable a specific Direct Routing user for emergency calling, use the following command:

```
Grant-CsTeamsEmergencyCallRoutingPolicy -Identity user1 -PolicyName UnitedStates
```

To assign a policy called "Contoso New York Emergency Call Routing" to Site 1, use the following command:

```
Set-CsTenantNetworkSite -identity "site1" -EmergencyCallRoutingPolicy "Contoso New York Emergency Call Routing"
```

If you assigned an emergency calling policy to a network site and to a user, and if that user is at that network site, the policy that's assigned to the network site overrides the policy that's assigned to the user.


## Test emergency calling

Some Emergency Routing Service Providers (ERSPs) in the United States offer an emergency calling test bot.

- **Calling Plan users in the United States** can use the predefined test emergency number 933 to validate their emergency calling configuration. This number is routed to a bot, which then echoes back the caller phone number (calling line ID), emergency address or location, and whether the call would be automatically routed to the PSAP or screened first.

- **Direct Routing customers in the United States** should coordinate with their ERSP for a test service.

 ## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Manage emergency call routing policies ](manage-emergency-call-routing-policies.md)
- [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Assign or change an emergency location for your user](assign-change-emergency-location-user.md)
- [Network settings for cloud voice features](cloud-voice-network-settings.md)
- [Manage your network topology for cloud voice features](manage-your-network-topology.md)
