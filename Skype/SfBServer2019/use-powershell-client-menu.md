---
title: "Use PowerShell for tasks on Client menu"
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
description: "Summary: Skype for Business Server Control panel to Cmdlet mapping for Client menu."
---
# Client

This article describes how similar results as that of the **Client** menu item in the legacy Control Panel can be achieved using cmdlets.

This article describes the following sub-menus :

- [Client](#client)
  - [Client Version Policy](#client-version-policy)
  - [Client Version Configuration](#client-version-configuration)
  - [Device Update](#device-update)
  - [Test Device](#test-device)
  - [Device Log Configuration](#device-log-configuration)
  - [Device Configuration](#device-configuration)
  - [Mobility Policy](#mobility-policy)
  - [Push Notification Configuration](#push-notification-configuration)

## Client Version Policy

The **CLIENT VERSION POLICY** sub-menu item under **Client** menu returns information about the clients supported in Skype for Business Server environment. A client version policy enables you to specify those clients who can sign in to Skype for Business Server system.

Let us consider the various tasks a user can do on **CLIENT VERSION POLICY**, and the Skype for Business cmdlets those tasks map to.

---
> **Scenario 1**: List all the client version policies

   ![List Client Version Policy](./media/clientversionpolicy-1.png)

***Cmdlet***

[Get-CsClientVersionPolicy](/powershell/module/skype/get-csclientversionpolicy)

***Example***

```powershell
 Get-CsClientVersionPolicy
```

---

> **Scenario 2**: Create a new client version policy

   ![New Client Version Policy](./media/clientversionpolicy-2.png)

***Cmdlet***

[New-CsClientVersionPolicy](/powershell/module/skype/new-csclientversionpolicy)  

***Example***

```powershell
 New-CsClientVersionPolicy -Identity site:Redmond
```

---

> **Scenario 3**: Get details of a chosen client version policy

   ![Get Client Version Policy](./media/clientversionpolicy-3.png)

***Cmdlet***

[Get-CsClientVersionPolicy](/powershell/module/skype/get-csclientversionpolicy)

***Example***

```powershell
 Get-CsClientVersionPolicy -Identity site:Redmond
```

---

> **Scenario 4**: Delete chosen client version policies

   ![Delete Client Version Policy](./media/clientversionpolicy-4.png)

***Cmdlet***

[Remove-CsClientVersionPolicy](/powershell/module/skype/remove-csclientversionpolicy)

***Example***

```powershell
 Remove-CsClientVersionPolicy -Identity site:Redmond
```

---

> **Scenario 5**: Update a client version policy

   ![Update Client Version Policy](./media/clientversionpolicy-5.png)

- **Annotation 1 - Result**

    This annotation on the image indicates a result, that is, the data being retrieved and displayed.

    ***Cmdlet***

    [Get-CsClientVersionPolicyRule](/powershell/module/skype/get-csclientversionpolicyrule)

    ***Example***

    ```powershell
    Get-CsClientVersionPolicyRule -Filter "Global/*"
    ```

- **Annotation 2 - Option (for the user)**

    This annotation on the image indicates an option for the user to implement, that is, to get the details of the client version policy rules.

    ***Cmdlet***

    [Get-CsClientVersionPolicyRule](/powershell/module/skype/get-csclientversionpolicyrule)

    ***Example***

    ```powershell
    Get-CsClientVersionPolicyRule -Identity "Global/2336c611-a243-4c5d-994b-eea8a524d0e4"
    ```

- **Annotation 3 - Option (for the user)**

    This annotation on the image indicates an option for the user to implement, that is, to create a new client version policy rule.

    ***Cmdlet***

    [New-CsClientVersionPolicyRule](/powershell/module/skype/new-csclientversionpolicyrule)

    ***Example***

    ```powershell
    $x = \[guid\]::NewGuid()

    New-CsClientVersionPolicyRule -Parent "site:Redmond" -RuleId $x -MajorVersion 4 -UserAgent InHouse
    ```

- **Annotation 4 - Option (for the user)**

    This annotation on the image indicates an option for the user to implement, that is, to commit/save the newly created client version policy rule.

    ***Cmdlet***

    [Set-CsClientVersionPolicy](/powershell/module/skype/set-csclientversionpolicy)

    ***Example***

    ```powershell
    Set-CsClientVersionPolicy -Identity site:Redmond -Rules $Null

    $x = Get-CsClientVersionPolicy -Identity site:Dublin | Select-Object -ExpandProperty Rules

    Set-CsClientVersionPolicy -Identity site:Redmond -Rules $x
    ```

---

## Client Version Configuration

 The **CLIENT VERSION CONFIGURATION** sub-menu item returns information about the clients supported in Skype for Business Server environment.

Let us consider the various tasks a user can do on **CLIENT VERSION CONFIGURATION**, and the Skype for Business cmdlets those tasks map to.

---
> **Scenario 1**: List all the client version configurations

   ![List Client Version Configuration](./media/ClientVersionConfiguration-1.png)

***Cmdlet***

[Get-CsClientVersionConfiguration](/powershell/module/skype/get-csclientversionconfiguration)

***Example***

```powershell
 Get-CsClientVersionConfiguration
```

---

> **Scenario 2**: Create a new client version configuration

   ![Create Client Version Configuration](./media/ClientVersionConfiguration-2.png)

***Cmdlet***

[New-CsClientVersionConfiguration](/powershell/module/skype/new-csclientversionconfiguration)  

***Example***

```powershell
 New-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False
```

---

> **Scenario 3**: Get details of a chosen client version configuration

   ![Get Client Version Configuration](./media/ClientVersionConfiguration-3.png)

***Cmdlet***

[Get-CsClientVersionConfiguration](/powershell/module/skype/get-csclientversionconfiguration)

***Example***

```powershell
 Get-CsClientVersionConfiguration -Identity site:Redmond
```

---

> **Scenario 4**: Delete chosen client version configurations

   ![Delete Client Version Configuration](./media/ClientVersionConfiguration-4.png)

***Cmdlet***

[Remove-CsClientVersionConfiguration](/powershell/module/skype/remove-csclientversionconfiguration)

***Example***

```powershell
 Remove-CsClientVersionConfiguration -Identity site:Redmond
```

---

> **Scenario 5**: Update a client version configuration

   ![Update Client Version Configuration](./media/ClientVersionConfiguration-5.png)

***Cmdlet***

[Set-CsClientVersionConfiguration](/powershell/module/skype/set-csclientversionconfiguration)

***Example***

```powershell
Get-CsClientVersionConfiguration | Set-CsClientVersionConfiguration -DefaultURL "https://litwareinc.com/csclients"
```

---

> **Scenario 6**: Enable/disable client version configurations

![Enable Client Version Configuration](./media/ClientVersionConfiguration-6.png)

***Cmdlet***

[Set-CsClientVersionConfiguration](/powershell/module/skype/set-csclientversionconfiguration)

***Example***

```powershell
Set-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False
```

---

## Device Update

**DEVICE UPDATE** rules are used to associate firmware updates with devices that run Skype for Business Phone Edition.

Let us consider the various tasks a user can do on **DEVICE UPDATE**, and the Skype for Business cmdlets those tasks map to.

---
> **Scenario 1**: List all the device updates

   ![List Device Update](./media/device-update-1.png)

***Cmdlet***

[Get-CsDeviceUpdateRule](/powershell/module/skype/get-csdeviceupdaterule)

***Example***

```powershell
 Get-CsDeviceUpdateRule
```

---

> **Scenario 2**: Delete device updates

   ![Delete Device Update](./media/device-update-2.png)

***Cmdlet***

[Remove-CsDeviceUpdateRule](/powershell/module/skype/remove-csdeviceupdaterule)  

***Example***

```powershell
 Remove-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9
```

---

> **Scenario 3**: Cancel device updates

   ![Cancel Device Update](./media/device-update-3.png)

***Cmdlet***

[Clear-CsDeviceUpdateFile](/powershell/module/skype/clear-csdeviceupdatefile)

***Example***

```powershell
 Clear-CsDeviceUpdateFile -Identity "service:WebServer:atl-cs-001.litwareinc.com"
```

---

> **Scenario 4**: Approve device updates

   ![Approve Device Update](./media/device-update-4.png)

***Cmdlet***

[Approve-CsDeviceUpdateRule](/powershell/module/skype/approve-csdeviceupdaterule)

***Example***

```powershell
 Approve-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9
```

---

> **Scenario 5**: Restore device updates

   ![Restore Device Update](./media/device-update-5.png)

***Cmdlet***

[Restore-CsDeviceUpdateRule](/powershell/module/skype/restore-csdeviceupdaterule)

***Example***

```powershell
 Restore-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9
```

---

## Test Device

The **TEST DEVICE** sub-menu item provides a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization.

Let us consider the various tasks a user can do on **TEST DEVICE**, and the Skype for Business cmdlets those tasks map to.

---
> **Scenario 1**: List all the test devices

   ![List Test Device](./media/testdevice-1.png)

***Cmdlet***

[Get-CsTestDevice](/powershell/module/skype/get-cstestdevice)

***Example***

```powershell
 Get-CsTestDevice
```

---

> **Scenario 2**: Create a new test device

   ![Create Test Device](./media/testdevice-2.png)

***Cmdlet***

[New-CsTestDevice](/powershell/module/skype/new-cstestdevice)  

***Example***

```powershell
 New-CsTestDevice -Identity site:Redmond/UCPhone -IdentifierType SerialNumber -Identifier "07823-A345"
```

---

> **Scenario 3**: Get details of a chosen test device

   ![Get Test Device](./media/testdevice-3.png)

***Cmdlet***

[Get-CsTestDevice](/powershell/module/skype/get-cstestdevice)

***Example***

```powershell
 Get-CsTestDevice -Identity site:Redmond/UCPhone
```

---

> **Scenario 4**: Delete chosen test devices

   ![Delete Test Device](./media/testdevice-4.png)

***Cmdlet***

[Remove-CsTestDevice](/powershell/module/skype/remove-cstestdevice)

***Example***

```powershell
 Remove-CsTestDevice -Identity site:Redmond
```

---

> **Scenario 5**: Update a test device

   ![Update Test Device](./media/testdevice-5.png)

***Cmdlet***

[Set-CsTestDevice](/powershell/module/skype/set-cstestdevice)

***Example***

```powershell
Set-CsTestDevice -Identity site:Redmond/UCPhone -IdentifierType SerialNumber -Identifier "09768-ABDR-83295"
```

---

## Device Log Configuration

**DEVICE LOG CONFIGURATION** sub-menu item helps manage the Device Update Web service, a Skype for Business Server component that enables administrators to distribute firmware updates to telephones and other devices that run Skype for Business.

Let us consider the various tasks a user can do on **DEVICE LOG CONFIGURATION**, and the Skype for Business cmdlets those tasks map to.

---
> **Scenario 1**: List all the device log configurations

   ![List Device Log Configuration](./media/device-log-configuration-1.png)

***Cmdlet***

[Get-CsDeviceUpdateConfiguration](/powershell/module/skype/get-csdeviceupdateconfiguration)

***Example***

```powershell
 Get-CsDeviceUpdateConfiguration
```

---

> **Scenario 2**: Create a new device log configuration

   ![Create Device Log Configuration](./media/device-log-configuration-2.png)

***Cmdlet***

[New-CsDeviceUpdateConfiguration](/powershell/module/skype/new-csdeviceupdateconfiguration)  

***Example***

```powershell
 New-CsDeviceUpdateConfiguration -Identity site:Redmond "07823-A345"
```

---

> **Scenario 3**: Get details of a chosen device log configuration

   ![Get Device Log Configuration](./media/device-log-configuration-3.png)

***Cmdlet***

[Get-CsDeviceUpdateConfiguration](/powershell/module/skype/get-csdeviceupdateconfiguration)

***Example***

```powershell
 Get-CsDeviceUpdateConfiguration -Identity Global
```

---

> **Scenario 4**: Delete chosen device log configurations

   ![Delete Device Log Configuration](./media/device-log-configuration-4.png)

***Cmdlet***

[Remove-CsDeviceUpdateConfiguration](/powershell/module/skype/remove-csdeviceupdateconfiguration)

***Example***

```powershell
 Remove-CsDeviceUpdateConfiguration -Identity site:Redmond
```

---

> **Scenario 5**: Update a device log configuration

   ![Update Device Log Configuration](./media/device-log-configuration-5.png)

***Cmdlet***

[Set-CsDeviceUpdateConfiguration](/powershell/module/skype/set-csdeviceupdateconfiguration)

***Example***

```powershell
Set-CsDeviceUpdateConfiguration -Identity global -MaxLogFileSize 2048000 -MaxLogCacheLimit 1024000
```

---

## Device Configuration

**DEVICE CONFIGURATION** sub-menu item helps administer information regarding management options for UC phones. These options include the required security mode and whether or not the phone should automatically be locked after a specified period of inactivity.

Let us consider the various tasks a user can do on **DEVICE CONFIGURATION**, and the Skype for Business cmdlets those tasks map to.

---

> **Scenario 1**: List all the mobility policies

   ![List Device Configuration](./media/device-configuration-1.png)

***Cmdlet***

[Get-CsUCPhoneConfiguration](/powershell/module/skype/get-csucphoneconfiguration)

***Example***

```powershell
 Get-CsUCPhoneConfiguration
```

---

> **Scenario 2**: Create a new device configuration

   ![Create Device Configuration](./media/device-configuration-2.png)

***Cmdlet***

[New-CsUCPhoneConfiguration](/powershell/module/skype/new-csucphoneconfiguration)  

***Example***

```powershell
 New-CsUCPhoneConfiguration -Identity site:Redmond -CalendarPollInterval "00:10:00" -LoggingLevel "Medium"
```

---

> **Scenario 3**: Get details of a chosen device configuration

   ![Get Device Configuration](./media/device-configuration-3.png)

***Cmdlet***

[Get-CsUCPhoneConfiguration](/powershell/module/skype/get-csucphoneconfiguration)

***Example***

```powershell
 Get-CsUCPhoneConfiguration -Identity site:Redmond
```

---

> **Scenario 4**: Delete chosen device configurations

   ![Delete Device Configuration](./media/device-configuration-4.png)

***Cmdlet***

[Remove-CsUCPhoneConfiguration](/powershell/module/skype/remove-csucphoneconfiguration)

***Example***

```powershell
 Remove-CsUCPhoneConfiguration -Identity site:Redmond
```

---

> **Scenario 5**: Updates a device configuration

   ![Update Device Configuration](./media/device-configuration-5.png)

***Cmdlet***

[Set-CsUCPhoneConfiguration](/powershell/module/skype/set-csucphoneconfiguration)

***Example***

```powershell
 Set-CsUCPhoneConfiguration -Identity site:Redmond -PhoneLockTimeout "00:30:00"
```

---

## Mobility Policy

**MOBILITY POLICY** determines whether or not a user can use Skype for Business Mobile. These policies also manage a user's ability to employ Call via Work, a feature that enables users to make and receive phone calls on their mobile phone by using their work phone number instead of their mobile phone number. Mobility policies can also be used to make Wi-Fi connections a requirement when making or receiving calls.

Let us consider the various tasks a user can do on **MOBILITY POLICY**, and the Skype for Business cmdlets those tasks map to.

---

> **Scenario 1**: List all the mobility policies

   ![List Mobility Policy](media/mobility-policy-1.png)

***Cmdlet***

[Get-CsMobilityPolicy](/powershell/module/skype/get-csmobilitypolicy)

***Example***

```powershell
 Get-CsMobilityPolicy
```

---

> **Scenario 2**: Create a new mobility policy

   ![Create Mobility Policy](./media/mobility-policy-2.png)

***Cmdlet***

[New-CsMobilityPolicy](/powershell/module/skype/new-csmobilitypolicy)  

***Example***

```powershell
 New-CsMobilityPolicy -Identity site:Redmond -EnableOutsideVoice $False
```

---

> **Scenario 3**: Get details of a chosen mobility policy

   ![Get Mobility Policy](./media/mobility-policy-3.png)

***Cmdlet***

[Get-CsMobilityPolicy](/powershell/module/skype/get-csmobilitypolicy)

***Example***

```powershell
 Get-CsMobilityPolicy -Identity "site:Redmond"
```

---

> **Scenario 4**: Delete chosen mobility policies

   ![Delete Mobility Policy](./media/mobility-policy-4.png)

***Cmdlet***

[Remove-CsMobilityPolicy](/powershell/module/skype/remove-csmobilitypolicy)

***Example***

```powershell
 Remove-CsMobilityPolicy -Identity "site:Redmond"
```

---

> **Scenario 5**: Update a mobility policy

   ![Update Mobility Policy](./media/mobility-policy-5.png)

***Cmdlet***

[Set-CsMobilityPolicy](/powershell/module/skype/set-csmobilitypolicy)

***Example***

```powershell
Set-CsMobilityPolicy -Identity "site:Redmond" -EnableOutsideVoice $False
```

---

## Push Notification Configuration

The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices such as iPhones and Windows Phones. These notifications are configured to be sent even if the Skype for Business application on those devices is currently suspended or running in the background.

Let us consider the various tasks a user can do on **PUSH NOTIFICATION CONFIGURATION**, and the Skype for Business cmdlets those tasks map to.

---

> **Scenario 1**: List all the mobility policies

   ![List Push Notification Configuration](./media/push-notification-config-1.png)

***Cmdlet***

[Get-CsPushNotificationConfiguration](/powershell/module/skype/get-cspushnotificationconfiguration)

***Example***

```powershell
 Get-CsPushNotificationConfiguration
```

---

> **Scenario 2**: Create a new push notification configuration

   ![Create Push Notification Configuration](./media/push-notification-config-2.png)

***Cmdlet***

[New-CsPushNotificationConfiguration](/powershell/module/skype/new-cspushnotificationconfiguration)  

***Example***

```powershell
 New-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $True -EnableMicrosoftPushNotificationService -$True
```

---

> **Scenario 3**: Get details of a chosen push notification configuration

   ![Get Push Notification Configuration](./media/push-notification-config-3.png)

***Cmdlet***

[Get-CsPushNotificationConfiguration](/powershell/module/skype/get-cspushnotificationconfiguration)

***Example***

```powershell
 Get-CsPushNotificationConfiguration -Identity "site:Redmond"
```

---

> **Scenario 4**: Delete chosen push notification configurations

   ![Delete Push Notification Configuration](./media/push-notification-config-4.png)

***Cmdlet***

[Remove-CsPushNotificationConfiguration](/powershell/module/skype/remove-cspushnotificationconfiguration)

***Example***

```powershell
 Remove-CsPushNotificationConfiguration -Identity "site:Redmond"
```

---

> **Scenario 5**: Update a push notification configuration

   ![Update Push Notification Configuration](./media/push-notification-config-5.png)

***Cmdlet***

[Set-CsPushNotificationConfiguration](/powershell/module/skype/set-cspushnotificationconfiguration)

***Example***

```powershell
 Set-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $False
```

---
