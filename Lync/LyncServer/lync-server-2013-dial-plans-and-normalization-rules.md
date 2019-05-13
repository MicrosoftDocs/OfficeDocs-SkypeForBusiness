---
title: 'Lync Server 2013: Dial plans and normalization rules'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Dial plans and normalization rules
ms:assetid: fde45195-6eb4-403c-9094-57df7fc0bd2a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413082(v=OCS.15)
ms:contentKeyID: 48185960
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Dial plans and normalization rules in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

A dial plan is a named set of normalization rules that translates phone numbers for a named location, individual user, or contact object into a single standard (E.164) format for purposes of phone authorization and call routing.

Normalization rules define how phone numbers expressed in various formats are to be routed for each specified location, user, or contact object. The same dial string may be interpreted and translated differently, depending on the location from which it is dialed and the person or contact object making the call.

<div>

## Dial Plan Scope

A dial plan’s *scope* determines the hierarchical level at which the dial plan can be applied. In Lync Server, a user can be assigned a specific per-user dial plan. If a user dial plan is not assigned, the Registrar pool dial plan is applied. If there is no Registrar pool dial plan, the site dial plan is applied. Finally, if there is no other dial plan applicable to the user, the global dial plan is applied.

Clients obtain dial plan scope levels through in-band provisioning settings that are provided when users log on to Lync Server. As the administrator, you can manage and assign dial plan scope levels by using Lync Server Control Panel.

<div>


> [!NOTE]  
> The service level public switched telephone network (PSTN) gateway dial plan is applied to the incoming calls from a particular gateway.



</div>

Dial plan scope levels are defined as follows:

  - **User dial plan:** Can be assigned to individual users, groups, or contact objects. Voice applications can look up a per-user dial plan when a call is received with the phone-context set to user-default. For the purpose of assigning a dial plan, a contact object is treated as an individual user.

  - **Pool dial plan:** Can be created at the service level for any PSTN gateway or Registrar in your topology. To define a pool dial plan, you must specify the particular service (PSTN gateway or Registrar pool) to which the dial plan applies.

  - **Site dial plan:** Can be created for an entire site, except for any users, groups, or contact objects that are assigned a pool dial plan or user dial plan. To define a site dial plan, you must specify the site to which the dial plan applies.

  - **Global dial plan:** The default dial plan installed with the product. You can edit the global dial plan, but you cannot delete it. This dial plan applies to all Enterprise Voice users, groups, and contact objects in your deployment, unless you configure and assign a dial plan with a more specific scope.

</div>

<div>

## Planning for Dial Plans

To plan a dial plan, follow these steps:

  - List all the locales in which your organization has an office.
    
    The list must be up-to-date and complete. It will need to be revised as company organization evolves. In a large, multinational company with numerous small branch offices, this can be a time-consuming task.

  - Identify valid number patterns for each site.
    
    The most time-consuming part of planning your dial plans is identifying the valid number patterns for each site. In some cases, you may be able to copy normalization rules that you have written for one dial plan to other dial plans, especially if the corresponding sites are within the same country/region or even continent. In other cases, small changes to numbers in one dial plan may be enough to use them in other dial plans.

  - Develop an organization-wide scheme for naming dial plans.
    
    Adopting a standard naming scheme assures consistency across an organization and makes maintenance and updates easier.

  - Decide whether multiple dial plans are required for a single location.
    
    If your organization maintains a single dial plan across multiple locations, you may still need to create a separate dial plan for Enterprise Voice users who are migrating from a private branch exchange (PBX) and who need to have their existing extensions retained.

  - Decide whether per-user dial plans are required. For example, if you have users at a branch site who are registered with the central site or if you have users who are registered on a Survivable Branch Appliance, you can consider special dialing scenarios for such users using per-user dial plans and normalization rules. For details, see [Branch-site resiliency requirements for Lync Server 2013](lync-server-2013-branch-site-resiliency-requirements.md).

  - Determine dial plan scope (as previously described in this topic).

To create a dial plan, you specify values in the following fields, as required, by using Lync Server Control Panel or Lync Server Management Shell.

<div>

## Name and Simple Name

For user dial plans, you should specify a descriptive name that identifies the users, groups, or contact objects to which the dial plan will be assigned. For site dial plans, the Name field is prepopulated with the site name and cannot be changed. For pool dial plans, the Name field is prepopulated with the PSTN gateway or Front End pool fully qualified domain name (FQDN) and cannot be changed.

The dial plan *Simple Name* is prepopulated with a string that is derived from the dial plan name. The Simple Name field is editable, which enables you to create a more descriptive naming convention for your dial plans. The *Simple Name* value cannot be empty and must be unique. A best practice is to develop a naming convention for your entire organization and then use this convention consistently across all sites and users.

</div>

<div>

## Description

We recommend that you type the common, recognizable name of the geographic location to which the corresponding dial plan applies. For example, if the dial plan name is London.Contoso.com, the recommended description would be London.

</div>

<div>

## Dial-in Conferencing Region

If you are deploying dial-in conferencing, you will need to specify a dial-in conferencing region to associate dial-in conferencing access numbers with a dial plan.

</div>

<div>

## External Access Prefix

You can specify an external access prefix of up to four characters (\#, \*, and 0-9) if users need to dial one or more additional leading digits (for example, 9) to get an external line.

<div>


> [!NOTE]  
> If you specify an external access prefix, you do not need to create an additional normalization rule to accommodate the prefix.



</div>

</div>

</div>

<div>

## Normalization Rules

Normalization rules define how phone numbers expressed in various formats are to be routed for the named location. The same number string may be interpreted and translated differently, depending on the locale from which it is dialed. Normalization rules are necessary for call routing because users can, and do, use various formats when entering phone numbers in their Contacts lists.

Normalizing user-supplied phone numbers provides a consistent format that facilitates the following tasks:

  - Match a dialed number to the intended recipient’s SIP-URI.

  - Apply dialing authorization rules to the calling party.

The following number fields are among those that your normalization rules may need to account for:

  - Dial plan

  - Country code

  - Area code

  - Length of extension

  - Site prefix

<div>

## Creating Normalization Rules

Normalization rules use .NET Framework regular expressions to specify numeric match patterns that the server uses to translate dial strings to E.164 format for the purpose of performing reverse number lookup. You create normalization rules in the Lync Server Control Panel either by entering the expressions manually, or by entering the starting digits and the length of the dial strings to be matched and letting the Lync Server Control Panel generate the corresponding regular expression for you. Either way, when you finish, you can enter a test number to verify that the normalization rule works as expected.

For details about using .NET Framework regular expressions, see ".NET Framework Regular Expressions" at [http://go.microsoft.com/fwlink/p/?linkId=140927](http://go.microsoft.com/fwlink/p/?linkid=140927).

</div>

<span id="BKMK_SampleNormalizationRules"></span>

<div>

## Sample Normalization Rules

The following table shows sample normalization rules that are written as .NET Framework regular expressions. The samples are examples only and are not meant to be a prescriptive reference for creating your own normalization rules.

### Table 1.Normalization Rules Using .NET Framework Regular Expressions

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
<td><p>4digitExtension</p></td>
<td><p>Translates 4-digit extensions</p></td>
<td><p>^(\d{4})$</p></td>
<td><p>+1425555$1</p></td>
<td><p>0100 is translated to +14255550100</p></td>
</tr>
<tr class="even">
<td><p>5digitExtension</p></td>
<td><p>Translates 5-digit extensions</p></td>
<td><p>^5(\d{4})$</p></td>
<td><p>+1425555$1</p></td>
<td><p>50100 is translated to +14255550100</p></td>
</tr>
<tr class="odd">
<td><p>7digitcallingRedmond</p></td>
<td><p>Translates 7-digit numbers to Redmond local numbers</p></td>
<td><p>^(\d{7})$</p></td>
<td><p>+1425$1</p></td>
<td><p>5550100 is translated to +14255550100</p></td>
</tr>
<tr class="even">
<td><p>7digitcallingDallas</p></td>
<td><p>Translates 7-digit numbers to Dallas local numbers</p></td>
<td><p>^(\d{7})$</p></td>
<td><p>+1972$1</p></td>
<td><p>5550100 is translated to +19725550100</p></td>
</tr>
<tr class="odd">
<td><p>10digitcallingUS</p></td>
<td><p>Translates 10-digit numbers in the United States</p></td>
<td><p>^(\d{10})$</p></td>
<td><p>+1$1</p></td>
<td><p>2065550100 is translated to +12065550100</p></td>
</tr>
<tr class="even">
<td><p>LDCallingUS</p></td>
<td><p>Translates numbers with long distance prefixes in the United States</p></td>
<td><p>^1(\d{10})$</p></td>
<td><p>+$1</p></td>
<td><p>12145550100 is translated to +2145550100</p></td>
</tr>
<tr class="odd">
<td><p>IntlCallingUS</p></td>
<td><p>Translates numbers with international prefixes in the United States</p></td>
<td><p>^011(\d*)$</p></td>
<td><p>+$1</p></td>
<td><p>01191445550100 is translated to +91445550100</p></td>
</tr>
<tr class="even">
<td><p>RedmondOperator</p></td>
<td><p>Translates 0 to Redmond Operator</p></td>
<td><p>^0$</p></td>
<td><p>+14255550100</p></td>
<td><p>0 is translated to +14255550100</p></td>
</tr>
<tr class="odd">
<td><p>RedmondSitePrefix</p></td>
<td><p>Translates numbers with on-net prefix (6) and Redmond site code (222)</p></td>
<td><p>^6222(\d{4})$</p></td>
<td><p>+1425555$1</p></td>
<td><p>62220100 is translated to +14255550100</p></td>
</tr>
<tr class="even">
<td><p>NYSitePrefix</p></td>
<td><p>Translates numbers with on-net prefix (6) and NY site code (333)</p></td>
<td><p>^6333(\d{4})$</p></td>
<td><p>+1202555$1</p></td>
<td><p>63330100 is translated to +12025550100</p></td>
</tr>
<tr class="odd">
<td><p>DallasSitePrefix</p></td>
<td><p>Translates numbers with on-net prefix (6) and Dallas site code (444)</p></td>
<td><p>^6444(\d{4})$</p></td>
<td><p>+1972555$1</p></td>
<td><p>64440100 is translated to +19725550100</p></td>
</tr>
</tbody>
</table>


The following table illustrates a sample dial plan for Redmond, Washington, United States, based on the normalization rules shown in the previous table.

### Table 2. Redmond Dial Plan Based on Normalization Rules Shown in Table 1

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>Redmond.forestFQDN</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5digitExtension</p></td>
</tr>
<tr class="even">
<td><p>7digitcallingRedmond</p></td>
</tr>
<tr class="odd">
<td><p>10digitcallingUS</p></td>
</tr>
<tr class="even">
<td><p>IntlCallingUS</p></td>
</tr>
<tr class="odd">
<td><p>RedmondSitePrefix</p></td>
</tr>
<tr class="even">
<td><p>NYSitePrefix</p></td>
</tr>
<tr class="odd">
<td><p>DallasSitePrefix</p></td>
</tr>
<tr class="even">
<td><p>RedmondOperator</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> The normalization rules names shown in the preceding table do not include spaces, but this is a matter of choice. The first name in the table, for example, could have been written "5 digit extension" or "5-digit Extension" and still be valid.



</div>

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

