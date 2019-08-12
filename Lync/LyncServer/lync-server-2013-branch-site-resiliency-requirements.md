---
title: 'Lync Server 2013: Branch-site resiliency requirements'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Branch-site resiliency requirements
ms:assetid: a570922c-52bd-42d7-bd64-226578b3d110
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412772(v=OCS.15)
ms:contentKeyID: 48184984
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Branch-site resiliency requirements for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-25_

This topic will help you to prepare users for branch-site resiliency and voice mail survivability, and also specifies the relevant hardware and software requirements.

<div>

## Preparing Branch Users for Branch-Site Resiliency

Prepare users for branch-site resiliency by setting their Registrar pool as the Survivable Branch Appliance (SBA) or Survivable Branch Server.

<div>

## Registrar Assignments for Branch Users

Regardless of which branch-site resiliency solution you choose, you will need to assign a primary Registrar to each user. Branch site users should always register with the Registrar at the branch site, regardless of whether that Registrar resides in the Survivable Branch Appliance, Survivable Branch Server, or stand-alone Lync Server 2013 Standard or Enterprise Edition server. A domain name system (DNS) service (SRV) resource record is required so that a client can discover its Registrar pool. If the Survivable Branch Appliance becomes unavailable, this is how branch site clients will automatically discover the backup Registrar.

If a branch site does not have a DNS server, there are two alternative ways to configure discovery of the Survivable Branch Appliance or Survivable Branch Server:

  - Configure DHCP option 120 on the branch site’s Dynamic Host Configuration Protocol (DHCP) server to point to the fully qualified domain name (FQDN) of the Survivable Branch Appliance or Survivable Branch Server.

  - Configure the Survivable Branch Appliance or Survivable Branch Server to respond to DHCP 120 queries.

</div>

<div>

## Voice Routing for Branch Users

We recommend that you create a separate user-level Voice over Internet Protocol (VoIP) policy for users in a branch site. This policy should include a primary route that uses the Survivable Branch Appliance or branch server gateway, and one or more backup routes that use a trunk with a public switched telephone network (PSTN) gateway at the central site. If the primary route is unavailable, the backup route that uses one or more central site gateways is used instead. This way, regardless of where a user is registered—on the branch site Registrar or the backup Registrar pool at the central site—the user’s VoIP policy is always in effect. This is an important consideration for failover scenarios. For example, if you need to rename the Survivable Branch Appliance or reconfigure the Survivable Branch Appliance to connect to a backup Registrar pool at the central site, then you must move branch site users to the central site for the duration. (For details about renaming or reconfiguring a Survivable Branch Appliance, see [Appendix B: Managing a Survivable Branch Appliance in Lync Server 2013](lync-server-2013-appendix-b-managing-a-survivable-branch-appliance.md) in the Deployment documentation.) If those users do not have user-level VoIP policies or user-level dial plans, when the users are moved to another site, the site-level VoIP policies and site-level dial plans of the central site apply to the users by default, instead of the branch site site-level VoIP policies and dial plans,. In this scenario, unless the site-level VoIP policies and site-level dial plans used by the backup Registrar pool can also apply to the branch site users, their calls will fail. For example, if users from a branch site located in Japan are moved to a central site in Redmond, then a dial plan with normalization rules that prepend +1425 to all 7-digit calls is unlikely to appropriately translate calls for those users.

<div>


> [!IMPORTANT]  
> When you create a branch office backup route, we recommend that you add two PSTN phone usage records to the branch office user policy and assign separate routes to each one. The first, or primary, route would direct calls to the gateway associated with the Survivable Branch Appliance (SBA) or branch server; the second, or backup, route would direct calls to the gateway at the central site. In directing calls, the SBA or branch server will attempt all routes assigned to the first PSTN usage record before attempting the second usage record.



</div>

To help ensure that inbound calls to branch site users will reach those users when the branch gateway or the Windows component of the Survivable Branch Appliance site is unavailable (which would happen, for example, if the Survivable Branch Appliance or branch gateway were down for maintenance), create a failover route on the gateway (or work with your Direct Inward Dialing (DID) provider) to redirect incoming calls to the backup Registrar pool at the central site. From there, the calls will be routed over the WAN link to branch users. Be sure that the route translates numbers to comply with the PSTN gateway or other trunk peer’s accepted phone number formats. For details about creating a failover route, see [Configuring a failover route in Lync Server 2013](lync-server-2013-configuring-a-failover-route.md). Also create service-level dial plans for the trunk associated with the gateway at the branch site to normalize incoming calls. If you have two Survivable Branch Appliances at a branch site, you can create a site-level dial plan for both unless a separate service-level plan for each is necessary.

<div>


> [!NOTE]  
> To account for the consumption of central site resources by any branch site users that rely on the central site for presence, conferencing, or failover, we recommend that you consider each branch site user as if the user were registered with the central site. There are currently no limits on the number of branch site users, including users registered with a Survivable Branch Appliance.



</div>

We also recommend that you create a user-level dial plan and voice policy, and then assign it to branch site users. For details, see [Create a dial plan in Lync Server 2013](lync-server-2013-create-a-dial-plan.md) and [Create the VoIP routing policy for branch users in Lync Server 2013](lync-server-2013-create-the-voip-routing-policy-for-branch-users.md) in the Deployment documentation.

<div>

## Routing Extension Numbers

When preparing dial plans and voice policies for branch site users, be sure to include normalization rules and translation rules that match the strings and number format used in the msRTCSIP-line (or Line URI) attribute, so that Lync 2013 calls enabled between branch site users and central site users will be routed correctly—particularly when calls must be rerouted over the PSTN because the WAN link is unavailable. Additionally, there are special considerations for dialed numbers that include extension numbers, rather just phone numbers.

Normalization rules and translations rules that match Line URIs that contain an extension number, whether exclusively or in addition to a full E.164 phone number, have additional requirements. This section describes several example scenarios to route calls for Line URIs with an extension number.

If your organization does not have Direct Inward Dial (DID) phone numbers configured for individual users and the Line URI of each user is configured with *only* an extension number, internal users can call one another by dialing only an extension number. However, you must configure normalization rules that can apply to calls from a branch site user to a central site user, that match the extension numbers.

In a scenario where the WAN link between a branch site and a central site is available, calls from branch site users to central site users do not require the matching normalization rule to translate the number because the call is not routed over the PSTN. For example:


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Rule name</th>
<th>Description</th>
<th>Number pattern</th>
<th>Translation</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5digitExtensions</p></td>
<td><p>Does not translate 5-digit numbers</p></td>
<td><p>^(\d{5})$</p></td>
<td><p>$1</p></td>
<td><p>10001 is not translated</p></td>
</tr>
</tbody>
</table>


You must also accommodate extension numbers for specific scenarios, such as when the WAN link between a branch site and central site is unavailable and a call from a branch site must be routed over the PSTN. During a WAN outage, if a branch site user calls a central site user only by dialing the central site user’s extension, you must have an outbound translation rule that adds the central site user’s full phone number. If a user’s Line URI contains your organization’s full phone number and the user’s unique extension number instead of a full phone number that is unique to the user, then you must have an outbound translation rule that adds your organization’s full phone number instead. For example:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Description</th>
<th>Matching pattern</th>
<th>Translation</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Translates 5-digit numbers to a user’s phone number and extension</p></td>
<td><p>^(\d{5})$</p></td>
<td><p>+14255550123;ext=$1</p></td>
<td><p>10001 is translated to +14255550123;ext=10001</p></td>
</tr>
<tr class="even">
<td><p>Translates 5-digit numbers to your organization’s phone number and a user’s extension</p></td>
<td><p>^(\d{5})$</p></td>
<td><p>+14255550100;ext=$1</p></td>
<td><p>10001 is translated to +14255550100;ext=10001</p></td>
</tr>
</tbody>
</table>


In this scenario, if the trunk peer that handles rerouting to the PSTN does not support extension numbers, then the outbound translation rule must also remove the extension number. For example:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Description</th>
<th>Matching pattern</th>
<th>Translation</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Removes extension from phone numbers with extensions</p></td>
<td><p>^\+(\d*);ext=(\d*)$</p></td>
<td><p>+$1</p></td>
<td><p>+14255550123;ext=10001 is translated to +14255550123</p></td>
</tr>
</tbody>
</table>


Whether or not a WAN link is available, if your organization does not have DID numbers configured for individual users and the Line URI for a user contains your organization’s phone number and the user’s unique extension number, then you must configure your organization’s phone number Line URI with a number that is reachable by the trunk peer or PSTN gateway at the branch site. You must also configure your organization’s phone number Line URI to include its own unique extension for calls to be routed to that number.

For details about calls from a central site user to a branch site user when the WAN link between the sites is unavailable, see "Preparing for Voice Mail Survivability" later in this topic. For details about dial plans and normalization rules, including other sample rules, see [Dial plans and normalization rules in Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md) in the Planning documentation and [Configuring dial plans in Lync Server 2013](lync-server-2013-configuring-dial-plans.md) in the Deployment documentation. For details about outbound translation rules, see [Translation rules in Lync Server 2013](lync-server-2013-translation-rules.md) in the Planning documentation and [Defining translation rules in Lync Server 2013](lync-server-2013-defining-translation-rules.md) in the Deployment documentation.

</div>

</div>

</div>

<div>

## Preparing for Voice Mail Survivability

Exchange Unified Messaging (UM) is usually installed only at a central site and not at branch sites. A caller should be able to leave a voice mail message, even if the WAN link between branch site and central site is unavailable. As a result, configuring the Line URI for the Exchange UM Auto Attendant phone number that provides voice mail for branch site users requires special considerations, in addition to the voice policy, dial plan, and normalization rules applicable to that voice mail number.

Survivable Branch Appliances (SBAs) and Survivable Branch Servers provide voice mail survivability for branch users during a WAN outage. Specifically, if you are using a Survivable Branch Appliance or Survivable Branch Server and the WAN becomes unavailable, the SBA or Survivable Branch Server reroutes unanswered calls over the PSTN to Exchange UM at the central site. With a SBA or Survivable Branch Server, users can also retrieve voice mail messages through the PSTN during a WAN outage. Finally, during a WAN outage the Survivable Branch Appliance or Survivable Branch Server queues missed-call notifications and then uploads them to the Exchange UM server when the WAN is restored. To help ensure that voice mail rerouting is resilient, be sure that you add an entry for the central site pool’s FQDN and an entry for the Edge Server FQDN to the hosts file on the Survivable Branch Server. Otherwise, DNS resolution can time out if you do not have a DNS server at the branch site.

We recommend the following configurations for voice mail survivability for branch site users:

  - An Microsoft Exchange administrator should configure Exchange UM Auto Attendant (AA) to accept messages only. This configuration disables all other generic functionality, such as transfer to a user or transfer to an operator, and limits the AA to only accepting messages. Alternatively, the Exchange administrator can use a generic AA or an AA customized to route the call to an operator.

  - The Lync Server administrator should take the AA phone number and use that phone number as the **exchange um auto attendant** number in the voice mail rerouting settings for the Survivable Branch Appliance or branch server.

  - The Lync Server administrator should get the Exchange UM subscriber access phone number and use that number as the **subscriber access** number in the voice mail rerouting settings for the Survivable Branch Appliance or Survivable Branch Server.

  - The Lync Server administrator should configure Exchange UM so that only one dial plan is associated with all branch users who need access to voice mail during a WAN outage.

  - When the WAN link is unavailable, calls to branch site users can be routed to the user’s Exchange Unified Messaging (UM) voice mailbox, but only if the voice policy applied to the call specifies a voice mail phone number that is unique and does not include an extension number.

</div>

<div>

## Hardware and Software Requirements for Branch-Site Resiliency

The hardware and software requirements vary, depending on your resiliency solution.

<div>

## Requirements for Survivable Branch Appliances

Required hardware and software is built into the Survivable Branch Appliance. However, we also recommend that each branch site deploy a DHCP server to obtain client IP addresses; otherwise, when the DHCP lease expires, clients will not have IP connectivity.

If the enterprise DNS servers are located only in central sites, branch site users will be unable to connect to them during a WAN outage, and therefore Lync Server discovery that uses DNS SRV (service (SRV) resource record) will fail. To assure prompt rerouting during a WAN outage, DNS records must be cached at the branch site. If the branch router supports it, turn on DNS caching. Or, you can deploy a DNS server at the branch. This can be a stand-alone server or a version of the Survivable Branch Appliance that supports DNS capabilities. For details, contact your Survivable Branch Appliance provider.

<div>


> [!NOTE]  
> It is not necessary to have a domain controller at a branch site. The Survivable Branch Appliance authenticates clients by using a special certificate that it sends the client in response to the client’s certificate request when it signs in.



</div>

Lync clients can discover the Lync Server by using DHCP Option 120 (SIP Registrar Option). This can be configured in one of two ways:

  - Configure the DHCP server at the branch site to reply to DHCP 120 queries, which return the FQDN of the Registrar on the Survivable Branch Appliance or Survivable Branch Server.

  - Turn on Lync Server DHCP. When this is turned on, the Lync Server Registrar responds to DHCP Option 120 queries. Note that the Registrar does not respond to any DHCP queries other than DHCP Options 120.

Additionally, for larger branch sites that have multiple subnets, DHCP relay agents should be enabled to forward DHCP Option 120 queries to the DHCP Server (configuration 1) or to the Registrar (configuration 2).

Finally, branch site users must be configured for Enterprise Voice and provisioned with an appropriate unified communications endpoint.

</div>

<div>

## Requirements for Survivable Branch Servers

The requirements for Survivable Branch Servers are the same as the requirements for a Front End Server. For details, see [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md) in the Planning documentation.

</div>

<div>

## Requirements for Full-Scale Lync Server Branch-Site Deployments

For details, see [Determining your infrastructure requirements for Lync Server 2013](lync-server-2013-determining-your-infrastructure-requirements.md) in the Planning documentation.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

