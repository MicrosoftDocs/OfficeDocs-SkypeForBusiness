---
title: "Response group experience in Lync Server 2013 during pool failure"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4e00fb38-64b1-4fd9-903d-7639177bc303
description: "In this articleUser Experience When Outage OccursUser Experience During FailoverUser Experience During Failback"
---

# Response group experience in Lync Server 2013 during pool failure
[]
 **In this article**
  
[User Experience When Outage Occurs](#sectionSection0)
  
[User Experience During Failover](#sectionSection1)
  
[User Experience During Failback](#sectionSection2)
  
This section describes in detail how response group activity is affected in the following stages:
  
- An outage occurs in the primary pool, but failover is not yet initiated.
    
- Service is failed over to the backup pool.
    
- Service is failed back to the primary pool.
    
## User Experience When Outage Occurs
<a name="sectionSection0"> </a>

When a pool or site outage occurs, but the administrator has not yet initiated failover, response group activity is handled as described in the following table.
  
> [!NOTE]
> During disaster recovery, calls behave differently depending on whether the primary pool response groups were imported to the backup pool during recovery. In the following table, references to imported response groups mean that primary pool response groups were imported to the backup pool during disaster recovery mode. 
  
**Outage Occurs**

|**Type of call or user action**|**During outage**|
|:-----|:-----|
|Calls connected to an agent  <br/> | Regular calls remain connected.  <br/>  Anonymous calls are disconnected.  <br/> |
|In progress calls not yet connected to an agent  <br/> |Calls are disconnected.  <br/> |
|New calls  <br/> | Calls are disconnected.  <br/>  If response groups were imported, calls connect to backup pool, but agents homed in primary pool are unreachable.  <br/> |
|Agent calls on behalf of response group  <br/> |Feature is disabled during this stage.  <br/> |
|Agent sign-in and agent information  <br/> | Agent groups owned by the primary pool can be viewed on agent console but agents cannot sign in.  <br/>  Agent groups owned by the backup pool can be viewed on agent console and agents can sign in.  <br/>  Imported agent groups are not displayed on agent console.  <br/> |
|Response group configuration  <br/> | Response groups owned by the primary pool can be viewed, depending on the availability of the primary pool's back-end database, but cannot be modified.  <br/>  Response groups owned by the backup pool can be viewed and modified.  <br/>  Imported response groups cannot be viewed with Lync Server Control Panel or the Response Group Configuration Tool, but can be configured by using Lync Server Management Shell cmdlets.  <br/> |
   
## User Experience During Failover
<a name="sectionSection1"> </a>

When an administrator invokes failover to a backup pool, response group activity is handled during and after the failover as described in the following table. The first column describes the type of activity that might be taking place. The middle column describes how each activity is handled during the brief time that it takes to fail over to the backup pool. The last column describes how the activity is handled for the duration, after the failover process is complete and the backup pool is standing in for the primary pool.
  
> [!NOTE]
> During disaster recovery, calls behave differently depending on whether the primary pool response groups were imported to the backup pool during recovery. In the following table, references to imported response groups mean that primary pool response groups were imported to the backup pool during disaster recovery mode. 
  
**Failover Is Initiated**

|**Type of call or user action**|**During Failover**|**After Failover Completes**|
|:-----|:-----|:-----|
|Calls connected to an agent  <br/> | Regular calls remain connected.  <br/>  Anonymous calls are disconnected.  <br/> | Regular calls remain connected.  <br/>  For imported response groups, anonymous calls that have reached the backup pool remain connected.  <br/> |
|In progress calls not yet connected to an agent  <br/> |Calls are disconnected.  <br/> | If response groups were not imported, no calls are in this status.  <br/>  For imported response groups, calls that have reached the backup pool remain connected.  <br/> |
|New calls  <br/> | Calls are disconnected.  <br/>  For imported response groups, calls connect to the backup pool, but agents homed in the primary pool are unreachable.  <br/> | If response groups were not imported, calls are disconnected.  <br/>  For imported response groups, calls connect to the backup pool.  <br/> |
|Agent calls on behalf of response group  <br/> |Feature is disabled during this stage  <br/> | If response groups were not imported, calls fail.  <br/>  For imported response groups, calls succeed.  <br/> |
|Agent sign-in and agent information  <br/> | Agent groups owned by the primary pool can be viewed on agent console but agents cannot sign in.  <br/>  Agent groups owned by the backup pool can be viewed on agent console and agents can sign in.  <br/>  Imported agent groups are displayed on agent console and agents can sign in.  <br/> | Agent groups owned by the primary pool can be viewed on agent console but agents cannot sign in.  <br/>  Agent groups owned by the backup pool can be viewed on agent console and agents can sign in.  <br/>  Imported agent groups are displayed on agent console and agents can sign in.  <br/> |
|Response group configuration  <br/> | Response groups owned by the primary pool can be viewed, depending on the availability of the primary pool's back-end database, but cannot be modified.  <br/>  Response groups owned by the backup pool can be viewed and modified.  <br/>  Imported response groups cannot be viewed with Lync Server Control Panel or the Response Group Configuration Tool, but can be configured by using Lync Server Management Shell cmdlets.  <br/> | Response groups owned by the primary pool can be viewed, depending on the availability of the back end database, but cannot be modified.  <br/>  Response groups owned by the backup pool can be viewed and modified.  <br/>  Imported response groups cannot be viewed with Lync Server Control Panel or the Response Group Configuration Tool, but can be configured by using Lync Server Management Shell cmdlets.  <br/> |
   
## User Experience During Failback
<a name="sectionSection2"> </a>

When an administrator invokes failback to the primary pool, response group activity is handled during and after the failback as described in the following table. 
  
> [!NOTE]
> During disaster recovery, calls behave differently depending on whether the primary pool response groups were imported to the backup pool during recovery. In the following table, references to imported response groups mean that primary pool response groups were imported to the backup pool during disaster recovery mode. 
  
**Call Handling in Failback**

|**Type of call or user action**|**During Failback**|**After Failback Completes**|
|:-----|:-----|:-----|
|Calls connected to an agent  <br/> | Regular calls remain connected.  <br/>  If response groups were not imported, no anonymous calls are in this status.  <br/>  For imported response groups, anonymous calls remain connected.  <br/> | Regular calls remain connected.  <br/>  If response groups were not imported, no anonymous calls are in this status.  <br/>  For imported response groups, anonymous calls remain connected.  <br/> |
|In progress calls not yet connected to an agent  <br/> | If response groups were not imported, no calls are in this status.  <br/>  For imported response groups, calls will be disconnected.  <br/> | If response groups were not imported, no calls are in this status.  <br/>  For imported response groups, calls will be disconnected.  <br/> |
|New calls  <br/> |Calls connect to the primary pool, but agents homed in the primary pool are unreachable.  <br/> |Calls connect to the primary pool.  <br/> |
|Agent calls on behalf of response group  <br/> |Feature is disabled during this stage.  <br/> |Calls succeed.  <br/> |
|Agent sign-in and agent information  <br/> | Agent groups owned by the primary pool can be viewed on agent console but agents cannot sign in.  <br/>  Agent groups owned by the backup pool can be viewed on agent console and agents can sign in.  <br/>  Imported agent groups are displayed on agent console and agents can sign in.  <br/> | Agent groups owned by the primary pool can be viewed on agent console and agents can sign in.  <br/>  Agent groups owned by the backup pool can be viewed on agent console and agents can sign in.  <br/>  Imported agent groups are not displayed on agent console.  <br/> |
|Response group configuration  <br/> | Response groups owned by the primary pool can be viewed, depending on the availability of the primary pool's back-end database, but cannot be modified.  <br/>  Response groups owned by the backup pool can be viewed and modified.  <br/>  Imported response groups cannot be viewed with Lync Server Control Panel or the Response Group Configuration Tool, but can be configured by using Lync Server Management Shell cmdlets.  <br/> | Response groups owned by the primary pool can be viewed and modified.  <br/>  Response groups owned by the backup pool can be viewed and modified.  <br/>  Imported response groups cannot be viewed with Lync Server Control Panel or the Response Group Configuration Tool, but can be configured by using Lync Server Management Shell cmdlets.  <br/> |
   

