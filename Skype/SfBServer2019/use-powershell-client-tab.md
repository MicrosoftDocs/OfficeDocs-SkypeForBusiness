---
title: "Use PowerShell for tasks on Client tab"
ms.reviewer: 
ms.author: v-smandalika
author: v-smandalika
manager: dansimp
ms.date: 10/12/2021
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
description: "Summary: Skype for Business Server Control panel to Cmdlet mapping."
---

# Client Version Policy

 The **Client Version Policy** component of the **Client** tab, and it returns information about the clients supported in your Skype for Business Server environment. A client version policy enable you to specify those clients who will be able to log on to your Skype for Business Server system.

Let us consider the various tasks a user can do on the **Client Version Policy** component, and the Skype for Business cmdlets those tasks map to.

---
> **Task 1**: List all the client version policies

![Client Version Policy](./media/ClientVersionPolicy-1.png)

***Cmdlet***

[Get-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicy?view=skype-ps)

***Example***

```powershell
 Get-CsClientVersionPolicy
```

---

> **Task 2**: Create a new client version policy

![Client Version Policy](./media/ClientVersionPolicy-2.png)

***Cmdlet***

[New-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/new-csclientversionpolicy?view=skype-ps)  

***Example***

```powershell
 New-CsClientVersionPolicy -Identity site:Redmond
```

---

> **Task 3**: Get details of a chosen client version policy

![Client Version Policy](./media/ClientVersionPolicy-3.png)

***Cmdlet***

[Get-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicy?view=skype-ps)

***Example***

```powershell
 Get-CsClientVersionPolicy -Identity site:Redmond
```

---

> **Task 4**: Delete chosen client version policies

![Client Version Policy](./media/ClientVersionPolicy-4.png)

***Cmdlet***

[Remove-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csclientversionpolicy?view=skype-ps)

***Example***

```powershell
 Remove-CsClientVersionPolicy -Identity site:Redmond
```

---

> **Task 5**: Update a client version policy

![Client Version Policy](./media/ClientVersionPolicy-5678.png)

- **Step 1**

    ***Cmdlet***

    [Get-CsClientVersionPolicyRule](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicyrule?view=skype-ps)

    ***Example***

    ```powershell
    Get-CsClientVersionPolicyRule -Filter "Global/*"
    ```

- **Step 2**

    ***Cmdlet***

    [Get-CsClientVersionPolicyRule](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicyrule?view=skype-ps)

    ***Example***

    ```powershell
    Get-CsClientVersionPolicyRule -Identity "Global/2336c611-a243-4c5d-994b-eea8a524d0e4"
    ```

- **Step 3**

    ***Cmdlet***

    [New-CsClientVersionPolicyRule](https://docs.microsoft.com/en-us/powershell/module/skype/new-csclientversionpolicyrule?view=skype-ps)

    ***Example***

    ```powershell
    $x = \[guid\]::NewGuid()

    New-CsClientVersionPolicyRule -Parent "site:Redmond" -RuleId $x -MajorVersion 4 -UserAgent InHouse
    ```

- **Step 4**

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

 The **Client Version Configuration** component returns information about the clients supported in your Skype for Business Server environment.

Let us consider the various tasks a user can do on the **Client Version Configuration** component, and the Skype for Business cmdlets those tasks map to.

---
> **Task 1**: List all the client version configurations

![Client Version Configuration](./media/ClientVersionConfiguration-1.png)

***Cmdlet***

[Get-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionconfiguration?view=skype-ps)

***Example***

```powershell
 Get-CsClientVersionConfiguration
```

---

> **Task 2**: Create a new client version configuration

![Client Version Configuration](./media/ClientVersionConfiguration-2.png)

***Cmdlet***

[New-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/new-csclientversionconfiguration?view=skype-ps)  

***Example***

```powershell
 New-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False
```

---

> **Task 3**: Get details of a chosen client version configuration

![Client Version Configuration](../media/ClientVersionConfiguration-3.png)

***Cmdlet***

[Get-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionconfiguration?view=skype-ps)

***Example***

```powershell
 Get-CsClientVersionConfiguration -Identity site:Redmond
```

---

> **Task 4**: Delete chosen client version configurations

![Client Version Configuration](../media/ClientVersionConfiguration-4.png)

***Cmdlet***

[Remove-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csclientversionconfiguration?view=skype-ps)

***Example***

```powershell
 Remove-CsClientVersionConfiguration -Identity site:Redmond
```

---

> **Task 5**: Update client version configurations

![Client Version Configuration](../media/ClientVersionConfiguration-5.png)

***Cmdlet***

[Set-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/set-csclientversionconfiguration?view=skype-ps)

***Example***

```powershell
Get-CsClientVersionConfiguration | Set-CsClientVersionConfiguration -DefaultURL "https://litwareinc.com/csclients"
```

---

> **Task 6**: Enable/disable client version configurations

***Cmdlet***

[Set-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/set-csclientversionconfiguration?view=skype-ps)

***Example***

```powershell
Set-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False
```

---

## Test Device

The **Test Device** component provides a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization.

Let us consider the various tasks a user can do on the **Test Device** component, and the Skype for Business cmdlets those tasks map to.

---
> **Task 1**: List all the test devices

![Test Device](./media/TestDevice-1.png)

***Cmdlet***

[Get-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/get-cstestdevice?view=skype-ps)

***Example***

```powershell
 Get-CsTestDevice
```

---

> **Task 2**: Create a new test device

![Test Device](./media/TestDevice-2.png)

***Cmdlet***

[New-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/new-cstestdevice?view=skype-ps)  

***Example***

```powershell
 New-CsTestDevice -Identity site:Redmond/UCPhone -IdentifierType SerialNumber -Identifier "07823-A345"
```

---

> **Task 3**: Get details of a chosen test device

![Test Device](./media/TestDevice-3.png)

***Cmdlet***

[Get-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/get-cstestdevice?view=skype-ps)

***Example***

```powershell
 Get-CsTestDevice -Identity site:Redmond/UCPhone
```

---

> **Task 4**: Delete a chosen test device

![Test Device](./media/TestDevice-4.png)

***Cmdlet***

[Remove-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/remove-cstestdevice?view=skype-ps)

***Example***

```powershell
 Remove-CsTestDevice -Identity site:Redmond
```
---

> **Task 5**: Update a test device

![Test Device](./media/TestDevice-5.png)

***Cmdlet***

[Set-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/set-cstestdevice?view=skype-ps)

***Example***

```powershell
Set-CsTestDevice -Identity site:Redmond/UCPhone -IdentifierType SerialNumber -Identifier "09768-ABDR-83295"
```

---

## Device Log Configuration

**Device Log Configuration** component's settings help manage the Device Update Web service, a Skype for Business Server component that enables administrators to distribute firmware updates to telephones and other devices that run Skype for Business.

Let us consider the various tasks a user can do on the **Device Log Configuration** component, and the Skype for Business cmdlets those tasks map to.

---
> **Task 1**: List all the device log configurations

![Device Log Configuration](./media/Device-Log-Configuration-1.png)

***Cmdlet***

[Get-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/get-csdeviceupdateconfiguration?view=skype-ps)

***Example***

```powershell
 Get-CsDeviceUpdateConfiguration
```

---

> **Task 2**: Create a new device log configuration

![Device Log Configuration](./media/Device-Log-Configuration-2.png)

***Cmdlet***

[New-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/new-csdeviceupdateconfiguration?view=skype-ps)  

***Example***

```powershell
 New-CsDeviceUpdateConfiguration -Identity site:Redmond "07823-A345"
```

---

> **Task 3**: Get details of a chosen device log configuration

![Device Log Configuration](./media/Device-Log-Configuration-3.png)

***Cmdlet***

[Get-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/get-csdeviceupdateconfiguration?view=skype-ps)

***Example***

```powershell
 Get-CsDeviceUpdateConfiguration -Identity Global
```

---

> **Task 4**: Delete chosen device log configurations

![Device Log Configuration](./media/Device-Log-Configuration-4.png)

***Cmdlet***

[Remove-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csdeviceupdateconfiguration?view=skype-ps)

***Example***

```powershell
 Remove-CsTestDevice -Identity site:Redmond
```

---

> **Task 5**: Update device log configurations

![Device Log Configuration](./media/Device-Log-Configuration-5.png)

***Cmdlet***

[Set-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/set-csdeviceupdateconfiguration?view=skype-ps)

***Example***

```powershell
Set-CsDeviceUpdateConfiguration -Identity global -MaxLogFileSize 2048000 -MaxLogCacheLimit 1024000
```

---
