---
title: "Skype for Business Server Control panel to Cmdlet mapping"
ms.reviewer: 
ms.author: ankum
author: ankum
manager: ravrao
ms.date: 5/10/21
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
description: "Summary: Skype for Business Server Control panel to Cmdlet mapping."
---

## Client Version Policy

 Returns information about the clients that are supported in your Skype for Business Server environment. Client version policies enable you to specify those clients who will be able to log on to your Skype for Business Server system.

Let us consider various scenarios and how do they map to Skype for Business cmdlets.

---
> **Scenario 1 :** List all the client version policies

![Client Version Policy](../media/ClientVersionPolicy-1.png)

***Cmdlet***

[Get-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicy?view=skype-ps)

***Example***

```powershell
 Get-CsClientVersionPolicy
```

---

> **Scenario 2 :** Create a new client version policy

![Client Version Policy](../media/ClientVersionPolicy-2.png)

***Cmdlet***

[New-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/new-csclientversionpolicy?view=skype-ps)  

***Example***

```powershell
 New-CsClientVersionPolicy -Identity site:Redmond
```

---

> **Scenario 3 :** Get details of a selected client version policy

![Client Version Policy](../media/ClientVersionPolicy-3.png)

***Cmdlet***

[Get-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicy?view=skype-ps)

***Example***

```powershell
 Get-CsClientVersionPolicy -Identity site:Redmond
```

---

> **Scenario 4 :** Delete selected client version policies

![Client Version Policy](../media/ClientVersionPolicy-4.png)

***Cmdlet***

[Remove-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csclientversionpolicy?view=skype-ps)

***Example***

```powershell
 Remove-CsClientVersionPolicy -Identity site:Redmond
```

> **Scenario 5 :** Update client version policy

![Client Version Policy](../media/ClientVersionPolicy-5678.png)

- **annotation 5**

    ***Cmdlet***

    [Get-CsClientVersionPolicyRule](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicyrule?view=skype-ps)

    ***Example***

    ```powershell
    Get-CsClientVersionPolicyRule -Filter "Global/*"
    ```

- **annotation 6**

    ***Cmdlet***

    [Get-CsClientVersionPolicyRule](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicyrule?view=skype-ps)

    ***Example***

    ```powershell
    Get-CsClientVersionPolicyRule -Identity "Global/2336c611-a243-4c5d-994b-eea8a524d0e4"
    ```

- **annotation 7**

    ***Cmdlet***

    [New-CsClientVersionPolicyRule](https://docs.microsoft.com/en-us/powershell/module/skype/new-csclientversionpolicyrule?view=skype-ps)

    ***Example***

    ```powershell
    $x = \[guid\]::NewGuid()

    New-CsClientVersionPolicyRule -Parent "site:Redmond" -RuleId $x -MajorVersion 4 -UserAgent InHouse
    ```

- **annotation 8**

    ***Cmdlet***

    [Set-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/set-csclientversionpolicy?view=skype-ps)

    ***Example***

    ```powershell
    Set-CsClientVersionPolicy -Identity site:Redmond -Rules $Null

    $x = Get-CsClientVersionPolicy -Identity site:Dublin | Select-Object -ExpandProperty Rules

    Set-CsClientVersionPolicy -Identity site:Redmond -Rules $x
    ```

---
## Client Version Configuration

 Returns information about the clients that are supported in your Skype for Business Server environment. Client version policies enable you to specify those clients who will be able to log on to your Skype for Business Server system.

Let us consider various  scenarios and how do they map to Skype for Business cmdlets.

---
> **Scenario 1 :** List all the client version configurations

![Client Version Configuration](../media/ClientVersionConfiguration-1.png)

***Cmdlet***

[Get-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionconfiguration?view=skype-ps)

***Example***

```powershell
 Get-CsClientVersionConfiguration
```

---

> **Scenario 2 :** Create a new client version configuration

![Client Version Configuration](../media/ClientVersionConfiguration-2.png)

***Cmdlet***

[New-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/new-csclientversionconfiguration?view=skype-ps)  

***Example***

```powershell
 New-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False
```

---

> **Scenario 3 :** Get details of a selected client version configuration

![Client Version Configuration](../media/ClientVersionConfiguration-3.png)

***Cmdlet***

[Get-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionconfiguration?view=skype-ps)

***Example***

```powershell
 Get-CsClientVersionConfiguration -Identity site:Redmond
```

---

> **Scenario 4 :** Delete selected client version policies

![Client Version Configuration](../media/ClientVersionConfiguration-4.png)

***Cmdlet***

[Remove-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csclientversionconfiguration?view=skype-ps)

***Example***

```powershell
 Remove-CsClientVersionConfiguration -Identity site:Redmond
```

> **Scenario 5 :** Update client version configurations

![Client Version Configuration](../media/ClientVersionConfiguration-5.png)

***Cmdlet***

[Set-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/set-csclientversionconfiguration?view=skype-ps)

***Example***

```powershell
Get-CsClientVersionConfiguration | Set-CsClientVersionConfiguration -DefaultURL "https://litwareinc.com/csclients"
```

---

> **Scenario 6 :** Enable/disable client version configurations

[Set-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/set-csclientversionconfiguration?view=skype-ps)

***Example***

```powershell
Set-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False
```

## Test Device

Test devices provide a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization

Let us consider various  scenarios and how do they map to Skype for Business cmdlets.

---
> **Scenario 1 :** Lists all the test devices

![Client Version Configuration](../media/TestDevice-1.png)

***Cmdlet***

[Get-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/get-cstestdevice?view=skype-ps)

***Example***

```powershell
 Get-CsTestDevice
```

---

> **Scenario 2 :** Create a new test device

![Client Version Configuration](../media/TestDevice-2.png)

***Cmdlet***

[New-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/new-cstestdevice?view=skype-ps)  

***Example***

```powershell
 New-CsTestDevice -Identity site:Redmond/UCPhone -IdentifierType SerialNumber -Identifier "07823-A345"
```

---

> **Scenario 3 :** Get details of a selected test device

![Test Device](../media/TestDevice-3.png)

***Cmdlet***

[Get-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/get-cstestdevice?view=skype-ps)

***Example***

```powershell
 Get-CsTestDevice -Identity site:Redmond/UCPhone
```

---

> **Scenario 4 :** Delete a selected test device

![Test Device](../media/TestDevice-4.png)
***Cmdlet***

[Remove-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/remove-cstestdevice?view=skype-ps)

***Example***

```powershell
 Remove-CsTestDevice -Identity site:Redmond
```

> **Scenario 5 :** Update a test device

![Test Device](../media/TestDevice-5.png)

***Cmdlet***

[Set-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/set-cstestdevice?view=skype-ps)

***Example***

```powershell
Set-CsTestDevice -Identity site:Redmond/UCPhone -IdentifierType SerialNumber -Identifier "09768-ABDR-83295"
```

---

## Device Log Configuration

These settings help manage the Device Update Web service, a Skype for Business Server component that enables administrators to distribute firmware updates to telephones and other devices running Skype for Business.

Let us consider various  scenarios and how do they map to Skype for Business cmdlets.

---
> **Scenario 1 :** List all the device log configurations

![Device Log Configuration](../media/Device-Log-Configuration-1.png)

***Cmdlet***

[Get-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/get-csdeviceupdateconfiguration?view=skype-ps)

***Example***

```powershell
 Get-CsDeviceUpdateConfiguration
```

---

> **Scenario 2 :** Create a new device log configuration

![Device Log Configuration](../media/Device-Log-Configuration-2.png)

***Cmdlet***

[New-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/new-csdeviceupdateconfiguration?view=skype-ps)  

***Example***

```powershell
 New-CsDeviceUpdateConfiguration -Identity site:Redmond "07823-A345"
```

---

> **Scenario 3 :** Get details of a selected device log configuration

![Device Log Configuration](../media/Device-Log-Configuration-3.png)

***Cmdlet***

[Get-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/get-csdeviceupdateconfiguration?view=skype-ps)

***Example***

```powershell
 Get-CsDeviceUpdateConfiguration -Identity Global
```

---

> **Scenario 4 :** Delete selected device log configurations

![Device Log Configuration](../media/Device-Log-Configuration-4.png)

***Cmdlet***

[Remove-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csdeviceupdateconfiguration?view=skype-ps)

***Example***

```powershell
 Remove-CsTestDevice -Identity site:Redmond
```

> **Scenario 5 :** Update device log configurations

![Device Log Configuration](../media/Device-Log-Configuration-5.png)

***Cmdlet***

[Set-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/set-csdeviceupdateconfiguration?view=skype-ps)

***Example***

```powershell
Set-CsDeviceUpdateConfiguration -Identity global -MaxLogFileSize 2048000 -MaxLogCacheLimit 1024000
```

---
