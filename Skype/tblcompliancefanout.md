---
title: tblComplianceFanout
ms.prod: SKYPEFORBUSINESS
ms.assetid: f5d9f342-a7cb-4b54-baa6-e656256b75ad
---


# tblComplianceFanout
[]
tblComplianceFanout contains all servers that processed a compliance event.
  
    
    


**Columns**


|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|fanoutEventID  <br/> |int  <br/> |Event ID.  <br/> |
|fanoutServerID  <br/> |int  <br/> |Server identity (corresponding to tblServerIdentity.serverID table).  <br/> |
   

**Key**


|**Column**|**Description**|
|:-----|:-----|
|fanoutEventID  <br/> |Foreign key with lookup in tblComplianceData.cmplEventID table.  <br/> |
   

