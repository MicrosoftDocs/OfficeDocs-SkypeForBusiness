---
title: "PSTN usage records in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b5f624aa-abe8-455b-a8e3-c228be230463
description: "Planning PSTN usage records consists mainly of listing all the call permissions that are currently in force in your organization, from the CEO to temporary workers, consultants, and contingent staff. This process also provides an opportunity to reexamine existing call permissions and revise them. You can create PSTN usage records only for those call permissions that apply to your anticipated Enterprise Voice users, but a better long-range solution might be to create PSTN usage records for all call permissions, regardless of whether some may not currently apply to the group of users to be enabled for Enterprise Voice. If call permissions change or new users with different call permissions are added, you will have already created the required PSTN usage records."
---

# PSTN usage records in Lync Server 2013
[]
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
    
For details about voice policies and routes, see [Voice policies in Lync Server 2013](voice-policies.md) and [Voice routes in Lync Server 2013](voice-routes.md). For details about how to create and configure them, see [Configuring voice routes for outbound calls in Lync Server 2013](configuring-voice-routes-for-outbound-calls.md).
  

