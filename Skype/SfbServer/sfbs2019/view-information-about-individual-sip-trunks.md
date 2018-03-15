---
title: "View information about individual SIP trunks in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: adfacb74-7ea5-4c53-934e-ba7ec59879eb
description: "SIP trunks are used to connect Lync Server 2013 Voice over IP phone network with the Public Switched Telephone Network. In previous version of the product, trunks were used to route outbound calls from a Mediation Server to a PSTN gateway and each gateway was limited to a single trunk. As a result, a PSTN gateway and a SIP trunk were essentially identical. For administrators, that meant they could view information about an individual SIP trunk simply by viewing information about the associated PSTN gateway."
---

# View information about individual SIP trunks in Lync Server 2013
[]
SIP trunks are used to connect Lync Server 2013 Voice over IP phone network with the Public Switched Telephone Network. In previous version of the product, trunks were used to route outbound calls from a Mediation Server to a PSTN gateway and each gateway was limited to a single trunk. As a result, a PSTN gateway and a SIP trunk were essentially identical. For administrators, that meant they could view information about an individual SIP trunk simply by viewing information about the associated PSTN gateway.
  
In Lync Server 2013, however, multiple trunks can now be assigned to a single PSTN gateway; this means that gateways and trunks are no longer one and the same. In turn, that means that administrators must use the new [Get-CsTrunk](get-cstrunk.md) cmdlet in order to view information about an individual SIP trunk. 
  
The Get-CsTrunk cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
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

### Viewing Information for All the SIP Trunks Assigned to a Pool

- In this example, information is returned for all the SIP trunks assigned to the pool atl-cs-001.litwareinc.com:
    
  ```
  Get-CsTrunk -PoolFqdn "atl-cs-001.litwareinc.com"
  ```


