---
title: View information about individual SIP trunks in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: adfacb74-7ea5-4c53-934e-ba7ec59879eb
---


# View information about individual SIP trunks in Skype for Business Server 2015
[] **Summary:** Learn how to view information about SIP trunks in Skype for Business Server 2015.
SIP trunks are used to connect Skype for Business Server Voice over IP phone network with the Public Switched Telephone Network (PSTN). In previous version of the product, trunks were used to route outbound calls from a Mediation Server to a PSTN gateway and each gateway was limited to a single trunk. As a result, a PSTN gateway and a SIP trunk were essentially identical. For administrators, that meant they could view information about an individual SIP trunk simply by viewing information about the associated PSTN gateway.
  
    
    

In Skype for Business Server, however, multiple trunks can now be assigned to a single PSTN gateway; this means that gateways and trunks are no longer one and the same. In turn, that means that administrators must use the new  [Get-CsTrunk](get-cstrunk.md) cmdlet in order to view information about an individual SIP trunk.
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


