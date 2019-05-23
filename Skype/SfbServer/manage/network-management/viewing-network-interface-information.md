---
title: 'Viewing network interface information'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You can view network interface information by using Windows PowerShell and the Get-CsNetworkInterface cmdlet. You can run this cmdlet from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell."
---

# Viewing network interface information in Skype for Business Server

You can view network interface information by using Windows PowerShell and the **Get-CsNetworkInterface** cmdlet. You can run this cmdlet from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 

## To view network interface information

  - To view network interface information, type the following command in the Skype for Business Server Management Shell, and then press ENTER:
    
        Get-CsNetworkInterface
    
    This command returns information similar to the following for each network interface:
    
        Identity              : dc.vdomain.com/Primary/1
        ComputerFqdn          : dc.vdomain.com
        IPAddress             : 0.0.0.0
        IPv6Address           :
        Interface             : Primary
        InterfaceNumber       : 1
        ConfiguredFqdn        :
        ConfiguredIPAddress   :
        ConfiguredIPv6Address :
    
    For details, see [Get-CsNetworkInterface](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkInterface).


