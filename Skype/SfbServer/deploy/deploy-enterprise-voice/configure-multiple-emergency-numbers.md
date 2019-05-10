---
title: "Configure multiple emergency numbers in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Admin
ms.custom:
ms.assetid: 2e869df0-5fdb-4e70-bd81-cb012556eb1a
description: "Read this topic to learn how to configure multiple emergency numbers in Skype for Business Server."
---

# Configure multiple emergency numbers in Skype for Business

Read this topic to learn how to configure multiple emergency numbers in Skype for Business Server.

Skype for Business Server now supports multiple emergency numbers for a client. Multiple emergency numbers is a new feature introduced in the June 2016 Cumulative Update. Before you configure your environment to support multiple emergency numbers, be sure to read [Plan for multiple emergency numbers in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/multiple-emergency-numbers.md).

> [!NOTE]
> If you have not yet upgraded to the November 2016 Cumulative Update, see [Updates to Skype for Business Server 2015](https://support.microsoft.com/en-us/help/3061064/updates-for-skype-for-business-server-2015). With the November 2016 Cumulative Update, the number of support emergency numbers increases from 5 to 100. 

## Configure multiple emergency numbers

To configure multiple emergency numbers, you use the New-CsEmergencyNumber cmdlet, and then you specify the EmergencyNumbers parameter with the [New-CsLocationPolicy](https://docs.microsoft.com/powershell/module/skype/new-cslocationpolicy?view=skype-ps) and [Set-CsLocationPolicy](https://docs.microsoft.com/powershell/module/skype/set-cslocationpolicy?view=skype-ps) cmdlets. For a complete description of all the location policy parameters, such as PSTN usage and Location required, see [Set-CsLocationPolicy](https://docs.microsoft.com/powershell/module/skype/set-cslocationpolicy?view=skype-ps).

The following command creates a new emergency number with dial string 911 by using the New-CsEmergency cmdlet:

```
> $a = New-CsEmergencyNumber -DialString 911 
```

The next command associates the number with the specified location policy by specifying the EmergencyNumbers parameter in the Set-CsLocationPolicy cmdlet:

```
> Set-CsLocationPolicy -Identity <id> -EmergencyNumbers @{add=$a} 
```

In the next example, an emergency number is created with a single dial mask, 112:

```
> $a = New-CsEmergencyNumber -DialString 911 -DialMask 112 
```

The next command creates an emergency number with multiple dial masks:

```
> $a = New-CsEmergencyNumber -DialString 911 -DialMask 112;999 
```

The next example adds multiple emergency numbers with multiple dial masks, and then associates the emergency numbers with the specified location policy:

```
> $a = New-CsEmergencyNumber -DialString 911 -DialMask 112;999 
> $b = New-CsEmergencyNumber -DialString 500 -DialMask 501;502
> Set-CsLocationPolicy -Identity <id> -EmergencyNumbers @{add=$a,$b} 
```

The next example configures multiple emergency numbers for health care providers that use both 911 and 450: 

```
> $a = New-CsEmergencyNumber -DialString 911 
> $b = New-CsEmergencyNumber -DialString 450
> Set-CsLocationPolicy -Identity US-Hospital -EmergencyNumbers @{add=$a,$b}
```

The next example configures multiple emergency numbers for the city of London:

```
> $a = New-CsEmergencyNumber -DialString 999 -DialMask 144
> $b = New-CsEmergencyNumber -DialString 112 -DialMask 911;117;118
> Set-CsLocationPolicy -Identity London -EmergencyNumbers @{add=$a,$b}
```

The next example configures multiple emergency numbers for India:

```
> $a = New-CsEmergencyNumber -DialString 100 -DialMask 911
> $b = New-CsEmergencyNumber -DialString 101 
> $c = New-CsEmergencyNumber -DialString 102 
> Set-CsLocationPolicy -Identity India -EmergencyNumbers @{add=$a,$b,$c}
```

The next example removes an existing entry with Dial string 911 and Dial masks 112 and 999:

```
> $a = New-CsEmergencyNumber -DialString 911 -DialMask 112;999
> Set-CsLocationPolicy -Identity <id> -EmergencyNumbers @{remove=$a} 
```


