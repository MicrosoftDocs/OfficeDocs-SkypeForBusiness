---
title: "View information about individual SIP trunks in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: adfacb74-7ea5-4c53-934e-ba7ec59879eb
description: "Summary: Learn how to view information about SIP trunks in Skype for Business Server."
---

# View information about individual SIP trunks in Skype for Business Server
 
**Summary:** Learn how to view information about SIP trunks in Skype for Business Server.
  
SIP trunks are used to connect Skype for Business Server Voice over IP phone network with the Public Switched Telephone Network (PSTN). In previous version of the product, trunks were used to route outbound calls from a Mediation Server to a PSTN gateway and each gateway was limited to a single trunk. As a result, a PSTN gateway and a SIP trunk were essentially identical. For administrators, that meant they could view information about an individual SIP trunk simply by viewing information about the associated PSTN gateway.
  
In Skype for Business Server, however, multiple trunks can now be assigned to a single PSTN gateway; this means that gateways and trunks are no longer one and the same. In turn, that means that administrators must use the new [Get-CsTrunk](https://docs.microsoft.com/powershell/module/skype/get-cstrunk?view=skype-ps) cmdlet in order to view information about an individual SIP trunk.
  
### To view information for all your SIP trunks

- The following command returns information about all the SIP trunks in use in your organization:
    
  ```
  Get-CsTrunk
  ```

### To view information for a specific SIP trunk

- This command returns information only for the SIP trunk with the Identity PstnGateway:192.168.0.240:
    
  ```
  Get-CsTrunk -Identity "PstnGateway:192.168.0.240"
  ```

### View information for all the SIP trunks assigned to a pool

- In this example, information is returned for all the SIP trunks assigned to the pool atl-cs-001.litwareinc.com:
    
  ```
  Get-CsTrunk -PoolFqdn "atl-cs-001.litwareinc.com"
  ```
