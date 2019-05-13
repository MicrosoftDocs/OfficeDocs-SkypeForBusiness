---
title: 'Lync Server 2013: Voice policies'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Voice policies
ms:assetid: b7433c62-9d8c-48af-89a0-19f0d34806ec
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412891(v=OCS.15)
ms:contentKeyID: 48185223
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Voice policies in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

Lync Server *voice policies* define the following for each user, site, or organization that is assigned the policy:

  - A set of calling features that can be enabled or disabled to determine the Enterprise Voice functionality available to users.

  - A set of public switched telephone network (PSTN) usage records that define what types of calls are authorized.

<div>

## Planning for Voice Policies

The following steps will help you plan the voice policies that you will need for your Enterprise Voice deployment:

  - Determine how you will configure your global voice policy (the default voice policy that is installed with the product). This policy will apply to all Enterprise Voice users who are not explicitly assigned a site-level or per-user policy.

  - Identify any site-level voice policies that you might need.

  - Identify any per-user voice policies that you might need.

  - Decide which call features to enable for each voice policy.

  - Determine what PSTN usage records to configure for each voice policy.

<div>

## Voice Policy Scope

*Voice policy scope* determines the hierarchical level at which the policy can be applied. In Lync Server, you can configure voice policies with the following scope levels (listed from the most specific to the most general).

  - **User voice policy** can be assigned to individual users, groups, or contact objects. This is the lowest level policy. User voice policies can be deployed to enable features for certain users or groups at a site, but not for others in the same site. For example, you may want to disable long distance dialing for some employees. For the purpose of assigning a voice policy, a contact object is treated as an individual user.
    
    <div>
    

    > [!NOTE]  
    > We recommend that you deploy a user voice policy for branch site Enterprise Voice users who are registered with the central site deployment, or users who are registered on a Survivable Branch Appliance.

    
    </div>

  - **Site voice policy** applies to an entire site, except for any users, groups, or contact objects that are assigned a user voice policy. To define a site voice policy, you must specify the site to which the policy applies. If a user voice policy is not assigned, the site voice policy is used.

  - **Global voice policy** is the default voice policy that is installed with the product. You can edit the global voice policy to meet the specific needs of your organization, but you cannot rename or delete it. This voice policy applies to all Enterprise Voice users, groups, and contact objects in your deployment unless you configure and assign a voice policy with more specific scope. If you want to disable this policy entirely, be sure that all sites and users have custom policies assigned to them.

</div>

<div>

## Call Features

You can enable or disable the following call features for each voice policy:

  - **Call forwarding** enables users to forward calls to other phones and client devices. Enabled by default.

  - **Delegation** enables users to specify other users to send and receive calls on their behalf. Enabled by default.

  - **Call transfer** enables users to transfer calls to other users. Enabled by default.

  - **Call park** enables users to park calls and then pick up the call from a different phone or client. Disabled by default.

  - **Simultaneous ringing** enables incoming calls to ring on an additional phone (for example, a mobile phone) or other endpoint devices. Enabled by default.

  - **Team call** enables users on a defined team to answer calls for other members of the team. Enabled by default.

  - **PSTN reroute** enables calls made by users who are assigned this policy to other enterprise users to be rerouted on the public switched telephone network (PSTN) if the WAN is congested or unavailable. Enabled by default.

  - **Bandwidth policy override** enables administrators to override call admission control policy decisions for a particular user. Disabled by default.

  - **Malicious call tracing** enables users to report malicious calls by using the Lync client, and then flags such calls in the call detail records. Disabled by default.

  - **Voicemail escape** prevents calls from being immediately routed to the user’s mobile phone voicemail system when simultaneous ringing is configured and the phone is turned off, out of battery, or out of range, and is based on a timer value. This setting enables and disables the timer and sets the value of the timer. It can be configured only by using the Lync Server Management Shell. Disabled by default.

  - **Call forwarding and simultaneous ringing PSTN usages** enables administrators to specify the same PSTN usage as the voice policy for call forwarding and simultaneous ringing, restrict call forwarding and simultaneous ringing to internal Lync users only, or specify a custom PSTN usage that is different from the voice policy’s PSTN usage. The default is to use the same PSTN usage as the voice policy for call forwarding and simultaneous ringing.

</div>

<div>

## PSTN Usage Records

Each voice policy should have one or more associated PSTN usage records. PSTN usages can be associated with a voice policy for the purpose of simultaneous ringing and call forwarding only. For details about planning PSTN usage records, see [PSTN usage records in Lync Server 2013](lync-server-2013-pstn-usage-records.md).

<div>


> [!NOTE]  
> PSTN usage order is critical because in matching users to routes, the outbound routing functionality compares PSTN usages from top to bottom. If the first usage matches the call route, that route is used. If not, the outbound routing functionality looks at the next PSTN usage on the list and continues until a match is found. In effect, the subsequent PSTN usages provide backup if the first one on the list is unavailable.



</div>

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

