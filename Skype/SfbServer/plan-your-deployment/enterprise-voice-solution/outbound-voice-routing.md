---
title: "Plan for outbound voice routing in Skype for Business Server"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: fde45195-6eb4-403c-9094-57df7fc0bd2a
description: "Learn about outbound voice routing in Skype for Business Server Enterprise Voice, including call routing settings, dial plans, normalization rules, voice policies, PSTN usage records, and voice routes."
---

# Plan for outbound voice routing in Skype for Business Server
 
Learn about outbound voice routing in Skype for Business Server Enterprise Voice, including call routing settings, dial plans, normalization rules, voice policies, PSTN usage records, and voice routes.
  
Outbound call routing applies to Enterprise Voice calls that are destined for a public switched telephone network (PSTN) gateway, trunk, or private branch exchange (PBX). When a Skype for Business user places a call, the server normalizes the phone number to E.164 format, if necessary, and attempts to match it to a SIP URI. If the server cannot make the match, it applies outbound call routing logic based on the supplied dial string. You define that logic by configuring the server settings that are described in the following table.
  
**Skype for Business Server Outbound Call Routing Settings**

|**Object**|**Description**|
|:-----|:-----|
|Dial Plan  <br/> |A dial plan is a named set of normalization rules that translates phone numbers for a named location, individual user, or contact object into a single standard (E.164) format for purposes of phone authorization and call routing.  <br/> |
|Normalization rule  <br/> |Normalization rules define how phone numbers expressed in various formats are to be routed for each specified location, user, or contact object. The same dial string may be interpreted and translated differently, depending on the location from which it is dialed and the person or contact object that makes the call. A set of normalization rules associated with a particular location constitutes a dial plan.  <br/> |
|Voice policy  <br/> |A voice policy associates one or more PSTN usage records with one user or a group of users. A voice policy also provides a list of calling features that you can enable or disable.  <br/> |
|PSTN usage record  <br/> |A PSTN usage record specifies a class of call (such as internal, local, or long distance) that can be made by various users, or groups of users, in an organization.  <br/> |
|Call Route  <br/> |A call route associates destination phone numbers with particular trunks and PSTN usage records. A PSTN gateway is considered a trunk.  <br/> |
   
## Dial plans and normalization rules

A dial plan is a named set of normalization rules that translates phone numbers for a named location, individual user, or contact object into a single standard (E.164) format for purposes of phone authorization and call routing. 
  
Normalization rules define how phone numbers expressed in various formats are to be routed for each specified location, user, or contact object. The same dial string may be interpreted and translated differently, depending on the location from which it is dialed and the person or contact object making the call.
  
### Dial Plan Scope

A dial plan's scope determines the hierarchical level at which the dial plan can be applied. In Skype for Business Server, a user can be assigned a specific per-user dial plan. If a user dial plan is not assigned, the Front End pool dial plan is applied. If there is no Front End pool dial plan, the site dial plan is applied. Finally, if there is no other dial plan applicable to the user, the global dial plan is applied.
  
Clients obtain dial plan scope levels through in-band provisioning settings that are provided when users log on to Skype for Business. As the administrator, you can manage and assign dial plan scope levels by using Skype for Business Server Control Panel.
  
> [!NOTE]
> The service level public switched telephone network (PSTN) gateway dial plan is applied to the incoming calls from a particular gateway. 
  
Dial plan scope levels are defined as follows:
  
- **User dial plan**: Can be assigned to individual users, groups, or contact objects. Voice applications can look up a per-user dial plan when a call is received with the phone-context set to user-default. For the purpose of assigning a dial plan, a contact object is treated as an individual user.
    
- **Pool dial plan**: Can be created at the service level for any PSTN gateway or Registrar in your topology. To define a pool dial plan, you must specify the particular service (PSTN gateway or Registrar pool) to which the dial plan applies. 
    
- **Site dial plan**: Can be created for an entire site, except for any users, groups, or contact objects that are assigned a pool dial plan or user dial plan. To define a site dial plan, you must specify the site to which the dial plan applies.
    
- **Global dial plan**: The default dial plan installed with the product. You can edit the global dial plan, but you cannot delete it. This dial plan applies to all Enterprise Voice users, groups, and contact objects in your deployment, unless you configure and assign a dial plan with a more specific scope.
    
### Planning for Dial Plans

To plan a dial plan, follow these steps:
  
- List all the locales in which your organization has an office.
    
    The list must be up-to-date and complete. It will need to be revised as company organization evolves. In a large, multinational company with numerous small branch offices, this can be a time-consuming task.
    
- Identify valid number patterns for each site.
    
    The most time-consuming part of planning your dial plans is identifying the valid number patterns for each site. In some cases, you may be able to copy normalization rules that you have written for one dial plan to other dial plans, especially if the corresponding sites are within the same country/region or even continent. In other cases, small changes to numbers in one dial plan may be enough to use them in other dial plans.
    
- Develop an organization-wide scheme for naming dial plans.
    
    Adopting a standard naming scheme assures consistency across an organization and makes maintenance and updates easier.
    
- Decide whether multiple dial plans are required for a single location. 
    
    If your organization maintains a single dial plan across multiple locations, you may still need to create a separate dial plan for Enterprise Voice users who are migrating from a private branch exchange (PBX) and who need to have their existing extensions retained.
    
- Decide whether per-user dial plans are required. For example, if you have users at a branch site who are registered with the central site or if you have users who are registered on a Survivable Branch Appliance, you can consider special dialing scenarios for such users using per-user dial plans and normalization rules. For details, see [Plan for Enterprise Voice resiliency in Skype for Business Server](enterprise-voice-resiliency.md).
    
- Determine dial plan scope (as previously described in this topic).
    
To create a dial plan, you specify values in the following fields, as required, by using Skype for Business Server Control Panel or Skype for Business Server Management Shell.
  
#### Name and Simple Name

For user dial plans, you should specify a descriptive name that identifies the users, groups, or contact objects to which the dial plan will be assigned. For site dial plans, the Name field is pre-populated with the site name and cannot be changed. For pool dial plans, the Name field is pre-populated with the PSTN gateway or Front End pool fully qualified domain name (FQDN) and cannot be changed.
  
The dial plan Simple Name is pre-populated with a string that is derived from the dial plan name. The Simple Name field is editable, which enables you to create a more descriptive naming convention for your dial plans. TheSimple Name value cannot be empty and must be unique. A best practice is to develop a naming convention for your entire organization and then use this convention consistently across all sites and users.
  
#### Description

We recommend that you type the common, recognizable name of the geographic location to which the corresponding dial plan applies. For example, if the dial plan name is London.Contoso.com, the recommended description would be London. 
  
#### Dial-in Conferencing Region

If you are deploying dial-in conferencing, you will need to specify a dial-in conferencing region to associate dial-in conferencing access numbers with a dial plan. 
  
#### External Access Prefix

You can specify an external access prefix of up to four characters (#, \*, and 0-9) if users need to dial one or more additional leading digits (for example, 9) to get an external line.
  
> [!NOTE]
> If you specify an external access prefix, you do not need to create an additional normalization rule to accommodate the prefix. 
  
### Normalization Rules

Normalization rules define how phone numbers expressed in various formats are to be routed for the named location. The same number string may be interpreted and translated differently, depending on the locale from which it is dialed. Normalization rules are necessary for call routing because users can, and do, use various formats when entering phone numbers in their Contacts lists.
  
Normalizing user-supplied phone numbers provides a consistent format that facilitates the following tasks:
  
- Match a dialed number to the intended recipient's SIP-URI.
    
- Apply dialing authorization rules to the calling party.
    
The following number fields are among those that your normalization rules may need to account for:
  
- Dial plan
    
- Country code
    
- Area code
    
- Length of extension
    
- Site prefix
    
#### Creating Normalization Rules

Normalization rules use .NET Framework regular expressions to specify numeric match patterns that the server uses to translate dial strings to E.164 format for the purpose of performing reverse number lookup. You create normalization rules in the Skype for Business Server Control Panel either by entering the expressions manually, or by entering the starting digits and the length of the dial strings to be matched and letting the Skype for Business Server Control Panel generate the corresponding regular expression for you. Either way, when you finish, you can enter a test number to verify that the normalization rule works as expected.
  
For details about using .NET Framework regular expressions, see [".NET Framework Regular Expressions"](https://go.microsoft.com/fwlink/p/?linkId=140927).
  
#### Sample Normalization Rules
<a name="BKMK_SampleNormalizationRules"> </a>

The following table shows sample normalization rules that are written as .NET Framework regular expressions. The samples are examples only and are not meant to be a prescriptive reference for creating your own normalization rules.
  
**Table 1.Normalization Rules Using .NET Framework Regular Expressions**

|**Rule name**|**Description**|**Number pattern**|**Translation**|**Example**|
|:-----|:-----|:-----|:-----|:-----|
|4digitExtension  <br/> |Translates 4-digit extensions  <br/> |^(\d{4})$  <br/> |+1425555$1  <br/> |0100 is translated to +14255550100  <br/> |
|5digitExtension  <br/> |Translates 5-digit extensions  <br/> |^5(\d{4})$  <br/> |+1425555$1  <br/> |50100 is translated to +14255550100  <br/> |
|7digitcallingRedmond  <br/> |Translates 7-digit numbers to Redmond local numbers  <br/> |^(\d{7})$  <br/> |+1425$1  <br/> |5550100 is translated to +14255550100  <br/> |
|7digitcallingDallas  <br/> |Translates 7-digit numbers to Dallas local numbers  <br/> |^(\d{7})$  <br/> |+1972$1  <br/> |5550100 is translated to +19725550100  <br/> |
|10digitcallingUS  <br/> |Translates 10-digit numbers in the United States  <br/> |^(\d{10})$  <br/> |+1$1  <br/> |2065550100 is translated to +12065550100  <br/> |
|LDCallingUS  <br/> |Translates numbers with long distance prefixes in the United States  <br/> |^1(\d{10})$  <br/> |+$1  <br/> |12145550100 is translated to +2145550100  <br/> |
|IntlCallingUS  <br/> |Translates numbers with international prefixes in the United States  <br/> |^011(\d\*)$  <br/> |+$1  <br/> |01191445550100 is translated to +91445550100  <br/> |
|RedmondOperator  <br/> |Translates 0 to Redmond Operator  <br/> |^0$  <br/> |+14255550100  <br/> |0 is translated to +14255550100  <br/> |
|RedmondSitePrefix  <br/> |Translates numbers with on-net prefix (6) and Redmond site code (222)  <br/> |^6222(\d{4})$  <br/> |+1425555$1  <br/> |62220100 is translated to +14255550100  <br/> |
|NYSitePrefix  <br/> |Translates numbers with on-net prefix (6) and NY site code (333)  <br/> |^6333(\d{4})$  <br/> |+1202555$1  <br/> |63330100 is translated to +12025550100  <br/> |
|DallasSitePrefix  <br/> |Translates numbers with on-net prefix (6) and Dallas site code (444)  <br/> |^6444(\d{4})$  <br/> |+1972555$1  <br/> |64440100 is translated to +19725550100  <br/> |
   
The following table illustrates a sample dial plan for Redmond, Washington, United States, based on the normalization rules shown in the previous table.
  
**Table 2. Redmond Dial Plan Based on Normalization Rules Shown in Table 1**

|**Redmond.forestFQDN**|
|:-----|
|5digitExtension  <br/> |
|7digitcallingRedmond  <br/> |
|10digitcallingUS  <br/> |
|IntlCallingUS  <br/> |
|RedmondSitePrefix  <br/> |
|NYSitePrefix  <br/> |
|DallasSitePrefix  <br/> |
|RedmondOperator  <br/> |
   
> [!NOTE]
> The normalization rules names shown in the preceding table do not include spaces, but this is a matter of choice. The first name in the table, for example, could have been written "5 digit extension" or "5-digit Extension" and still be valid. 
  
## Voice policies

Skype for Business Server voice policies define the following for each user, site, or organization that is assigned the policy:
  
- A set of calling features that can be enabled or disabled to determine the Enterprise Voice functionality available to users.
    
- A set of public switched telephone network (PSTN) usage records that define what types of calls are authorized. 
    
The following steps will help you plan the voice policies that you will need for your Enterprise Voice deployment:
  
- Determine how you will configure your global voice policy (the default voice policy that is installed with the product). This policy will apply to all Enterprise Voice users who are not explicitly assigned a site-level or per-user policy.
    
- Identify any site-level voice policies that you might need.
    
- Identify any per-user voice policies that you might need.
    
- Decide which call features to enable for each voice policy.
    
- Determine what PSTN usage records to configure for each voice policy.
    
### Voice Policy Scope

Voice policy scope determines the hierarchical level at which the policy can be applied. In Skype for Business Server, you can configure voice policies with the following scope levels (listed from the most specific to the most general).
  
- **User voice policy** can be assigned to individual users, groups, or contact objects. This is the lowest level policy. User voice policies can be deployed to enable features for certain users or groups at a site, but not for others in the same site. For example, you may want to disable long distance dialing for some employees. For the purpose of assigning a voice policy, a contact object is treated as an individual user.
    
    > [!NOTE]
    > We recommend that you deploy a user voice policy for branch site Enterprise Voice users who are registered with the central site deployment, or users who are registered on a Survivable Branch Appliance. 
  
- **Site voice policy** applies to an entire site, except for any users, groups, or contact objects that are assigned a user voice policy. To define a site voice policy, you must specify the site to which the policy applies. If a user voice policy is not assigned, the site voice policy is used.
    
- **Global voice policy** is the default voice policy that is installed with the product. You can edit the global voice policy to meet the specific needs of your organization, but you cannot rename or delete it. This voice policy applies to all Enterprise Voice users, groups, and contact objects in your deployment unless you configure and assign a voice policy with more specific scope. If you want to disable this policy entirely, be sure that all sites and users have custom policies assigned to them.
    
### Call Features

You can enable or disable the following call features for each voice policy:
  
- **Call forwarding** enables users to forward calls to other phones and client devices. Enabled by default.
    
- **Delegation** enables users to specify other users to send and receive calls on their behalf. Enabled by default.
    
- **Call transfer** enables users to transfer calls to other users. Enabled by default.
    
- **Call park** enables users to park calls and then pick up the call from a different phone or client. Disabled by default.
    
- **Simultaneous ringing** enables incoming calls to ring on an additional phone (for example, a mobile phone) or other endpoint devices. Enabled by default.
    
- **Team call** enables users on a defined team to answer calls for other members of the team. Enabled by default.
    
- **PSTN reroute** enables calls made by users who are assigned this policy to other enterprise users to be rerouted on the public switched telephone network (PSTN) if the WAN is congested or unavailable. Enabled by default.
    
- **Bandwidth policy override** enables administrators to override call admission control policy decisions for a particular user. Disabled by default.
    
- **Malicious call tracing** enables users to report malicious calls by using the Skype for Business client, and then flags such calls in the call detail records. Disabled by default.
    
- **Voicemail escape** prevents calls from being immediately routed to the user's mobile phone voicemail system when simultaneous ringing is configured and the phone is turned off, out of battery, or out of range, and is based on a timer value. This setting enables and disables the timer and sets the value of the timer. It can be configured only by using the Skype for Business Server Management Shell. Disabled by default.
    
- **Call forwarding and simultaneous ringing PSTN usages** enables administrators to specify the same PSTN usage as the voice policy for call forwarding and simultaneous ringing, restrict call forwarding and simultaneous ringing to internal Skype for Business users only, or specify a custom PSTN usage that is different from the voice policy's PSTN usage. The default is to use the same PSTN usage as the voice policy for call forwarding and simultaneous ringing.
    
### PSTN Usage Records

Each voice policy should have one or more associated PSTN usage records. PSTN usages can be associated with a voice policy for the purpose of simultaneous ringing and call forwarding only. 
  
> [!NOTE]
> PSTN usage order is critical because in matching users to routes, the outbound routing functionality compares PSTN usages from top to bottom. If the first usage matches the call route, that route is used. If not, the outbound routing functionality looks at the next PSTN usage on the list and continues until a match is found. In effect, the subsequent PSTN usages provide backup if the first one on the list is unavailable. 
  
## PSTN usage records

Planning PSTN usage records consists mainly of listing all the call permissions that are currently in force in your organization, from the CEO to temporary workers, consultants, and contingent staff. This process also provides an opportunity to reexamine existing call permissions and revise them. You can create PSTN usage records only for those call permissions that apply to your anticipated Enterprise Voice users, but a better long-range solution might be to create PSTN usage records for all call permissions, regardless of whether some may not currently apply to the group of users to be enabled for Enterprise Voice. If call permissions change or new users with different call permissions are added, you will have already created the required PSTN usage records.
  
The following table shows a typical PSTN usage table.
  
**PSTN Usage Records**

|**Phone attribute**|**Description**|
|:-----|:-----|
|Local  <br/> |Local calls  <br/> |
|Long-Distance  <br/> |Long distance calls  <br/> |
|International  <br/> |International calls  <br/> |
|Delhi  <br/> |Delhi full-time employees  <br/> |
|Redmond  <br/> |Redmond full-time employees  <br/> |
|RedmondTemps  <br/> |Redmond temporary employees  <br/> |
|Zurich  <br/> |Zurich full-time employees  <br/> |
   
By themselves, PSTN usage records do not do anything. For them to work, you must associate them with the following:
  
- Voice policies, which are assigned to users.
    
- Routes, which are assigned to phone numbers.
    
## Voice routes

Call routes specify how Skype for Business Server handles outbound calls placed by Enterprise Voice users. When a user dials a number, the Front End Server normalizes the dial string to E.164 format, if necessary, and attempts to match it to a SIP URI. If the server cannot make the match, it applies outgoing call routing logic based on the number. The final step in defining that logic is to create a separate named call route for each set of destination phone numbers that are listed in each dial plan.
  
Before you define outbound call routes, you should complete the following steps:
  
- Deploy one or more trunks.
    
- Create dial plans as needed for sites, individuals, and Contact objects.
    
- Create public switched telephone network (PSTN) usage records.
    
Additionally, to enable outbound call routing, you must create and assign one or more voice policies. You can do this either before or after you define outbound call routes.
  
For each route, you must specify:
  
- A name by which the route can be easily identified.
    
- An optional description in cases where the name alone may not be sufficient to describe the route.
    
- The regular expression matching pattern that identifies the destination phone numbers to which the route is applied, along with exceptions to which the matching pattern is not to be applied.
    
- One or more trunks that you want to assign to the route.
    
- The PSTN usage records that users must have in order to call numbers matching the destination phone number regular expression.
    
You can specify call routes in the Skype for Business Server Control Panel. These call routes populate the server routing table, which Skype for Business Server uses to route calls that are destined for the PSTN.
  
### M:N Trunk Support

Skype for Business Server provides flexibility in how calls are routed to the PSTN. A voice route specifies a set of trunks to the PSTN that can be used for a particular voice call. A trunk associates a Mediation Server and a port number with a PSTN gateway and listening port number. This logical association enables a Mediation Server to be associated with multiple gateways and have multiple connections to the same gateway. When defining a call route, you specify the trunks associated with that route, but you do not specify which Mediation Servers are associated with the route. To create trunks by defining the relationships between Mediation Servers and PSTN gateways, IP-PBXs, and Session Border Controllers (SBCs), use the Topology Builder.
  
### Least-Cost Routing

The ability to specify the trunks to which various numbers are routed enables you to determine which routes incur the lowest costs and implement them accordingly. The general rule in selecting trunks is to choose the trunk with the closest gateway to the location of the destination number in order to minimize long-distance charges. For example, if you are in New York and calling a number in Rome, you would carry the call over the IP network to the trunk with the gateway in your Rome office, thereby incurring a charge only for a local call.
  
For an example of how least-cost routing might be used, consider the following: Fabrikam decides to enable German users to dial U.S. numbers by using the U.S. trunk. Fabrikam also wants to configure the system so that all calls from U.S. Skype for Business Server users to Germany and adjacent countries/regions terminate on the trunk with the gateway in Germany. This routing will save money, because a call from Germany to Austria, for example, is less expensive than a call from the U.S. to Austria.
  
### Translating Outbound Dial Strings

Skype for Business Server requires all dial strings to be normalized to E.164 format for the purpose of performing reverse number lookup (RNL). For trunks with gateways or private branch exchanges (PBXs) that require numbers translated in local dialing formats, Skype for Business Server enables you to create one or more rules that assist in manipulating the called number (i.e. Request URI) prior to routing it to the trunk. For example, you could write a rule to remove +44 from the head of a dial string and replace it with 0144.
  
With Skype for Business Server, it is possible to create one or more rules that assist in manipulating the calling number prior to routing it to the trunk.
  
In planning your trunks that associate gateway:port pairs with Mediation Server:port pairs, it may be useful to group trunks with similar local dialing requirements, and therefore reduce the number of required translation rules and the time it takes to write them.
  
### Configuring Caller ID

Skype for Business Server provides a way to manipulate the caller ID for outbound calls. For example, if an organization wants to mask employees' direct-dial extensions and replace them with the generic corporate or departmental number, an administrator can do that by using Skype for Business Server Control Panel to suppress the caller ID and replace it with a specified alternative caller ID. In planning your routing logic, consider which individuals, groups, sites you'll want this option for—perhaps, even, for all employees.
  
> [!NOTE]
> For calls that are rerouted over the PSTN, the generic caller ID will be presented instead of the original caller ID. This can cause the call to bypass Do Not Disturb or privacy settings that the callee may have configured. 
  
### Additional Routing Logic

In creating outbound call routes, you should be aware of the following factors that can affect routing logic:
  
- Where a call is established over a federated boundary, the domain portion of the URI is used to route the call over to the enterprise that is responsible for applying the outbound routing logic.
    
- If the domain portion of the request URI does not contain a supported domain for the enterprise, the outbound routing component on the server does not process the call.
    
- If a user is not enabled for Enterprise Voice, the server applies other routing logic, as appropriate.
    
- If a call is routed to a gateway that is fully occupied (all trunk lines are busy), the gateway rejects the call and the outbound routing logic redirects the call to the next-least-cost route. Give this careful consideration, because a gateway sized for a small office overseas (for example, Zurich) may actually carry a significant amount of nonlocal traffic for international calls to Switzerland. If the gateway is not correctly sized for this additional traffic, calls to Switzerland may be routed by way of a gateway in Germany, resulting in larger toll charges.
    

