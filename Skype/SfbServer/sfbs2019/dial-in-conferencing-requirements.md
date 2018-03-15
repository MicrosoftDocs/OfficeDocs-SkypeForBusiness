---
title: "Dial-in conferencing requirements in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9aff949e-3dac-481a-be46-a180c72e8066
description: "In this articlePlanning for Dial-in PSTN ConnectivityPlanning for Dial-in Conferencing RegionsPlanning for Conference Directories"
---

# Dial-in conferencing requirements in Lync Server 2013
[]
 **In this article**
  
[Planning for Dial-in PSTN Connectivity](#sectionSection0)
  
[Planning for Dial-in Conferencing Regions](#bkmk_PlanningforDialinConferencingRegions)
  
[Planning for Conference Directories](#sectionSection2)
  
Before you start the Lync Server 2013 deployment process you need to plan for the following:
  
- The configuration to use for connecting to the public switched telephone network (PSTN)
    
- Your strategy for assigning dial-in conferencing regions to dial-in access numbers
    
- Your strategy for creating conference directories
    
## Planning for Dial-in PSTN Connectivity
<a name="sectionSection0"> </a>

Dial-in conferencing requires at least one Mediation Server and at least one PSTN gateway. 
  
You can deploy a Mediation Server in a central site or in a branch site. In a central site, you can collocate a Mediation Server on a Front End pool or Standard Edition server, or you can deploy it on a stand-alone server or pool. In a branch site, you can deploy a Mediation Server on a stand-alone server or as a component of the Survivable Branch Appliance.
  
You can deploy a PSTN gateway in a central site or in a branch site. In a branch site, the PSTN gateway can be stand-alone or a component of the Survivable Branch Appliance.
  
> [!NOTE]
> Dial-in conferencing does not use media bypass because A/V Conferencing Server do not support media bypass. 
  
For details about planning your configuration for Mediation Server and PSTN gateways for dial-in conferencing, see [Components and topologies for Mediation Server in Lync Server 2013](components-and-topologies-for-mediation-server.md) in the Planning documentation. 
  
## Planning for Dial-in Conferencing Regions
<a name="bkmk_PlanningforDialinConferencingRegions"> </a>

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
    
## Planning for Conference Directories
<a name="sectionSection2"> </a>

Conference directories maintain a mapping between the alphanumeric meeting ID that a participant uses to join a conference when using Lync 2013, and the numeric-only conference ID that a dial-in conferencing participant uses to join the conference. The format of the conference ID is as follows:
  
```
<housekeeping digit (1 digit)><conference directory (usually 1-2 digits)><conference number (variable number of digits><check digit (1 digit)>
```

Creating multiple conference directories will ensure that conference IDs will stay short until a significant amount of conferences have been created. In an organization with a typical number of conferences per user, we recommend that you create one conference directory for every 999 users in the pool. Using this guideline the conference IDs can generally be kept small. However, once the number of conference directories (across the pools) exceed 9, the Conference ID number will grow to support additional conferences.
  
## See also
<a name="sectionSection2"> </a>

#### 

[Mediation Server component in Lync Server 2013](mediation-server-component.md)
  
[Dial plans and normalization rules in Lync Server 2013](dial-plans-and-normalization-rules.md)

