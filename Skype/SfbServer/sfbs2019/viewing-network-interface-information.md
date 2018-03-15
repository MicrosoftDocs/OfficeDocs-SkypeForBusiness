---
title: "Viewing network interface information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e7dbb1ec-62b3-48be-a419-c493df5740e6
description: "You can view network interface information by using Windows PowerShell and the Get-CsNetworkInterface cmdlet. You can run this cmdlet from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog articleQuick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShellat https://go.microsoft.com/fwlink/p/?linkId=255876."
---

# Viewing network interface information in Lync Server 2013
[]
You can view network interface information by using Windows PowerShell and the **Get-CsNetworkInterface** cmdlet. You can run this cmdlet from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view network interface information

- To view network interface information, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsNetworkInterface
  ```

    This command returns information similar to the following for each network interface:
    
  ```
  Identity              : dc.vdomain.com/Primary/1
  ComputerFqdn          : dc.vdomain.com
  IPAddress             : 0.0.0.0
  IPv6Address           :
  Interface             : Primary
  InterfaceNumber       : 1
  ConfiguredFqdn        :
  ConfiguredIPAddress   :
  ConfiguredIPv6Address :
  ```

    For details, see [Get-CsNetworkInterface](get-csnetworkinterface.md).
    

