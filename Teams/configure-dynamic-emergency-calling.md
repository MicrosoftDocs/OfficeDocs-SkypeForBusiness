---
title: Configure dynamic emergency calling
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection:  
- Teams_ITAdmin_Help
- M365-voice
ms.reviewer: roykuntz
search.appverid: MET150
description: Configure dynamic emergency calling
appliesto: 
- Microsoft Teams
---

# Plan and configure dynamic emergency calling for Calling Plans
Dynamic emergency calling for Microsoft Calling Plans provides the capability to configure and route emergency calls based on the current location of the Teams client.  The ability to do automatic routing to the appropriate Public Safety Answering Point (PSAP) or to notify security desk personnel varies depending on the country of usage of the Teams user.  

> [!Note] 
> Dynamic emergency calling is currently available only in the United States. Security desk notification, however, is supported across country boundaries.

**Within the United States**, you can configure dynamic emergency call routing as follows:
  
- If a Teams client is located at a tenant-defined dynamic emergency location, emergency calls from that client are automatically routed to the PSAP serving that geographic location.  

- If a Teams client is not located at a tenant-defined dynamic emergency location, emergency calls from that client are screened by a national call center to determine the location of the caller before transferring the call to the PSAP serving that geographic location.

You can configure security desk notification as follows:

- If a Teams client is located at a tenant-defined network site, the security group members configured for that site will be notified.

- If a Teams client is not located at a tenant-defined network site, the security group members configured for the user will be notified.

**Outside of the United States**, emergency calls are routed to the PSAP that is mapped to the phone number assigned to the user.  Some countries, such as the Great Britain and Canada, screen the calls nationally before transferring the caller to the appropriate PSAP, while others route directly to the PSAP regardless of where the user is currently located. 

Note that you can configure dynamic security desk notification for all Calling Plan users.


## Supported clients

The following clients are currently supported.  Check back often to see updates to this list.

- Teams desktop client for Windows
- Teams desktop client for Mac

## Configure dynamic emergency calling

To configure dynamic emergency calling, you need to perform the following tasks:

- [Configure emergency addresses](#configure-emergency-addresses)
- [Configure network settings](#configure-network-settings)
- [Configure Location Information Service](#configure-location-information-service)
- [Configure emergency policies](#configure-emergency-policies)
- [Enable users and sites](#enable-users-and-sites)
- [Test emergency calling](#test-emergency-calling)


### Configure emergency addresses

To support automated routing within the United States, you must fully configure the civic address that is part of the emergency locations that are assigned to network identifiers--and include the associated geo codes. (Emergency addresses without geo-codes cannot be assigned to the network identifiers that are required for dynamic locations.)

- If you enter an emergency address via the Microsoft Teams admin center, the geo codes are automatically included if a match is found.

- If a match is not automatically found, you will have the opportunity to manually create an emergency address.  

This means that if an existing emergency address is configured for emergency calling, the same address needs to be re-created to include the geo codes.  To distinguish between the two addresses, you should include a different description. The new emergency address can be assigned to the users who have the old address. When fully migrated, the old address can be deleted. 

For more information about configuring emergency addresses, see [What are emergency locations, places, and call routing?](what-are-emergency-locations-addresses-and-call-routing.md).

### Configure network settings

You need to configure network settings to dynamically obtain an emergency location used for routing emergency calls and, optionally, to provide dynamic configuration of security desk notifications. The emergency calling experience desired will dictate which network settings need to be configured. 

Keep the following definitions in mind:

- Trusted IP’s contain a collection of the Internet external IPs of the enterprise network and are used to determine if the user’s endpoint is inside the corporate network. Dynamic locations will only be enabled if the user’s external IP matches an IP in the Trusted IP collection.  A match can be made against either IPv4 or IPv6 IP addresses and is dependent upon the format of the IP packet sent to the network settings.

- A network region contains a collection of network sites. 

- A network site represents a location where your organization has a physical value, such as an office, a set of buildings, or a campus. These sites are defined as a collection of IP subnets.

- A network subnet must be associated with a specific network site. A client's location is determined based on the network subnet and the associated network site.  


For Calling Plan users:

- If dynamic configuration of security desk notification is required, then you must configure both Trusted IP addresses and network sites.

- If only dynamic locations are required, then you must configure only Trusted IP addresses. 

- If neither are required, then configuration of network settings is not required. 

For more information, see [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md), which describes how to configure network settings. (The information in this article applies to both Calling Plans and Direct Routing.)


### Configure Location Information Service

A Teams client obtains emergency addresses from the emergency locations associated with different network identifiers.  Subnets and Wireless Access Points are both supported. (Support for Ethernet switch/port is pending.)

To configure the Location Information Service (LIS) with network identifiers and emergency locations, use the following cmdlets:

- Get, Set, Remove -CsOnlineLisPort
- Get, Set, Remove -CsOnlineLisSwitch
- Get, Set, Remove -CsOnlineLisSubnet
- Get, Set, Remove -CsOnlineLisWirelessAccessPoint 

> [!Important] 
> If subnets are being used as part of network sites, they must be redefined in the Location Information Service to render dynamic locations.


### Configure emergency policies

Emergency policies determine what happens when a user in your organization makes an emergency call.  You can set who to notify and how they are notified when a user calls emergency services. For example, you can configure policy settings to automatically notify your organization's security desk and have them listen in on emergency calls.

You manage emergency policies by using the New-, Set- and Grant-CsTeamsEmergencyCalling Policy cmdlets.  For more information, see [Manage emergency calling policies in Teams](manage-emergency-calling-policies.md).


### Enable users and sites

While Calling Plan users are automatically enabled for emergency calling, you must enable users for security desk notification by configuring the emergency calling policy as shown in the following example:


```
Grant-CsTeamsEmergencyCallingPolicy -Identity user1 -PolicyName SecurityDeskNotification
```

You can also assign the emergency calling policy to a network site as shown in the following example, which assigns a policy called "Contoso Emergency Calling Policy 1" to Site 1:

```
Set-CsTenantNetworkSite -identity "site1" -EmergencyCallingPolicy "Contoso Emergency Calling Policy 1"
```

If you assigned an emergency calling policy to a network site and to a user, and if that user is at that network site, the policy that's assigned to the network site overrides the policy that's assigned to the user.


### Test emergency calling

To test emergency calling in the United States, use the predefined test emergency number 933.  This number is routed to a bot, which then echoes back the caller phone number (calling line ID), emergency address or location, and whether the call is automatically routed to the PSAP or screened first.  