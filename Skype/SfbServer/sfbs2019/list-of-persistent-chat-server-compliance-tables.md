---
title: "List of Persistent Chat Server compliance tables in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8563446e-90cc-47cc-8a8e-4883decfe195
description: "The Persistent Chat compliance database schema consists of the following tables."
---

# List of Persistent Chat Server compliance tables in Lync Server 2013
[]
The Persistent Chat compliance database schema consists of the following tables.
  
## List of Persistent Chat Server Compliance Tables

|**Table**|**Description**|
|:-----|:-----|
|[tblComplianceData in Lync Server 2013](tblcompliancedata.md) <br/> |Contains the compliance events that have not yet been processed by the configured adapter.  <br/> This table includes Persistent Chat-related events, such as chat messages and file downloads. (Participant events are tracked by the tblComplianceParticipant table.)  <br/> (The servers that processed the events in this table are listed in the tblComplianceFanout table.)  <br/> |
|[tblComplianceFanout in Lync Server 2013](tblcompliancefanout.md) <br/> |Contains the servers that processed a compliance event. This table is tightly coupled with the tblComplianceData table.  <br/> |
|[tblComplianceParticipant in Lync Server 2013](tblcomplianceparticipant.md) <br/> |Contains current participants per chat service and per server. It is maintained based on join and part compliance events received from the Persistent Chat service.  <br/> |
|[tblComplianceState in Lync Server 2013](tblcompliancestate.md) <br/> |Contains pool-wide compliance state information.  <br/> |
   

