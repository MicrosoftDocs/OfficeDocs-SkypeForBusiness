---
title: "View information about individual SIP trunks in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "In Skype for Business Server, multiple trunks can be assigned to a single PSTN gateway; this means that gateways and trunks are not one and the same, and administrators must use the Get-CsTrunk cmdlet to view information about an individual SIP trunk."
---

# View information about individual SIP trunks in Skype for Business Server

In Skype for Business Server, multiple trunks can be assigned to a single PSTN gateway; this means that gateways and trunks are not one and the same, and that administrators must use the [Get-CsTrunk](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTrunk) cmdlet to view information about an individual SIP trunk.

The Get-CsTrunk cmdlet can be run either from the  Skype for Business Server Management Shell or from a remote session of Windows PowerShell.

**To view information for all your SIP trunks**

The following command returns information about all the SIP trunks in use in your organization:

`Get-CsTrunk`

**To view information for a specific SIP trunk**

This command returns information only for the SIP trunk with the Identity PstnGateway:192.168.0.240:

`Get-CsTrunk -Identity "PstnGateway:192.168.0.240"`

**Viewing Information for All the SIP Trunks Assigned to a Pool**

In this example, information is returned for all the SIP trunks assigned to the pool atl-cs-001.litwareinc.com:

`Get-CsTrunk -PoolFqdn "atl-cs-001.litwareinc.com"`
