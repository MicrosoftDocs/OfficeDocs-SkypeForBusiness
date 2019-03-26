---
title: Lync Server 2013 dial-in conferencing requirements
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Dial-in conferencing requirements
ms:assetid: 9aff949e-3dac-481a-be46-a180c72e8066
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398802(v=OCS.15)
ms:contentKeyID: 48184969
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Dial-in conferencing requirements in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-30_

Before you start the Lync Server 2013 deployment process you need to plan for the following:

  - The configuration to use for connecting to the public switched telephone network (PSTN)

  - Your strategy for assigning dial-in conferencing regions to dial-in access numbers

  - Your strategy for creating conference directories

<div>

## Planning for Dial-in PSTN Connectivity

Dial-in conferencing requires at least one Mediation Server and at least one PSTN gateway.

You can deploy a Mediation Server in a central site or in a branch site. In a central site, you can collocate a Mediation Server on a Front End pool or Standard Edition server, or you can deploy it on a stand-alone server or pool. In a branch site, you can deploy a Mediation Server on a stand-alone server or as a component of the Survivable Branch Appliance.

You can deploy a PSTN gateway in a central site or in a branch site. In a branch site, the PSTN gateway can be stand-alone or a component of the Survivable Branch Appliance.

<div>


> [!NOTE]  
> Dial-in conferencing does not use media bypass because A/V Conferencing Server do not support media bypass.



</div>

For details about planning your configuration for Mediation Server and PSTN gateways for dial-in conferencing, see [Components and topologies for Mediation Server in Lync Server 2013](lync-server-2013-components-and-topologies-for-mediation-server.md) in the Planning documentation.

</div>

<span id="bkmk_PlanningforDialinConferencingRegions"></span>

<div>

## Planning for Dial-in Conferencing Regions

During dial-in configuration, you create dial plans and dial-in conferencing access numbers. Dial plans are sets of normalization rules that specify the number and pattern of digits in a phone number and translate the phone number into the standard E.164 format for call routing. Dial-in conferencing access numbers are the numbers participants call to join a conference.

Every dial-in conferencing access number must be associated with at least one dial plan. Dial-in conferencing regions associate a dial-in conferencing access number with its dial plans. When you set up a dial plan, you specify the dial-in conferencing region that applies to the dial plan. When you create the dial-in access number, you select the regions that associate the access number with the appropriate dial plans.

When you create a dial plan, you specify the scope of the dial plan: user scope, pool scope, or site scope. Every user is assigned the dial plan from the narrowest scope that applies to the user. For example, a user is assigned a user-level dial plan, if one applies. If a user-level dial plan does not apply, the user is assigned a pool-level dial plan. If a pool-level dial plan does not apply, the user is assigned a site-level dial plan. If a site-level dial plan does not apply, the user is assigned the global dial plan.

Before you configure the dial plans, is it important to plan how you want to name and use regions. The following considerations apply to dial-in conferencing regions:

  - A region is typically a geographical area that is associated with an office or group of offices.

  - Languages are associated with dial-in access numbers. If you support geographical areas that have multiple languages, you should decide how you want to define regions to support the multiple languages. For example, you might define multiple regions based on a combination of geography and language, or you might define a single region based on geography and have a different dial-in access numbers for each language.

  - When a user schedules a meeting, by default the meeting uses the region specified by that user's dial plan.

  - By default, the all of the dial-in access numbers for the region are included in the meeting invitation.

  - It is important to name regions so that they are clearly recognizable. The user can use the names of the regions to change a meeting's region so that different access numbers are included in the invitation. (When users use Outlook to schedule a meeting, the user uses the Online Meeting Add-in for Lync 2013 to change the region).

  - Regions should be designed so that any invitee who wants to dial into a conference can see a local access number in the conference invitation.

  - You can configure the order in which access numbers within a region appear on the Dial-in Conferencing Settings page (and, therefore, the order in which they appear in the conference invitation) by using Lync Server Management Shell cmdlets.

  - Any user from any location can call any dial-in access number to join a conference.

</div>

<div>

## Planning for Conference Directories

Conference directories maintain a mapping between the alphanumeric meeting ID that a participant uses to join a conference when using Lync 2013, and the numeric-only conference ID that a dial-in conferencing participant uses to join the conference. The format of the conference ID is as follows:

    <housekeeping digit (1 digit)><conference directory (usually 1-2 digits)><conference number (variable number of digits><check digit (1 digit)>

Creating multiple conference directories will ensure that conference IDs will stay short until a significant amount of conferences have been created. In an organization with a typical number of conferences per user, we recommend that you create one conference directory for every 999 users in the pool. Using this guideline the conference IDs can generally be kept small. However, once the number of conference directories (across the pools) exceed 9, the Conference ID number will grow to support additional conferences.

</div>

<div>

## See Also


[Mediation Server component in Lync Server 2013](lync-server-2013-mediation-server-component.md)  
[Dial plans and normalization rules in Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

