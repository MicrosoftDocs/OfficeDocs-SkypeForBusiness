---
title: "Test-CsMcxPushNotification"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: db81339b-f79a-418a-b29d-8596dff7a210
description: "Verifies that the push notification service is working. The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices like iPhones and Windows Phones, even if the Skype for Business application on those devices is currently suspended or running in the background. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011."
---

# Test-CsMcxPushNotification
 
Verifies that the push notification service is working. The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) provides a way to send notifications about events such as new instant messages or new voice mail to mobile devices like iPhones and Windows Phones, even if the Skype for Business application on those devices is currently suspended or running in the background. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
Test-CsMcxPushNotification -AccessEdgeFqdn <String> [-Certificate <X509Certificate2>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 tests the push notification service accessed through the Edge server atl-edge-001.litwareinc.com. The AccessEdgeFqdn must point to the internal edge of the proxy server to which push notification traffic is directed.
  
```
Test-CsMcxPushNotification -AccessEdgeFqdn "atl-edge-001.litwareinc.com"
```

## Detailed Description

The Apple Push Notification Service and the Skype for Business Server 2015 Push Notification Service enable users running Skype for Business on their Apple iPhone or Windows Phone to receive notifications about Skype for Business events even when the application is suspended or running in the background. For example, users can receive notice for events such as these:
  
- Invitations to a new instant messaging session or conference
  
- New instant messages
  
- New voice mail
  
Without the push notification service, users would receive these notices only when Skype for Business was in the foreground and serving as the active application.
  
The Test-CsMcxPushNotification cmdlet provides a way for administrators to verify that the push notification service is working. When using this cmdlet, make sure that the AccessEdgeFqdn parameter points to the internal edge of the proxy server to which push notification traffic is directed.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AccessEdgeFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name of the Access Edge server used to connect to the push notification service.  <br/> |
| _Certificate_ <br/> |Optional  <br/> |System.Security.Cryptography.X509Certificates.X509Certificate2  <br/> |Enables you to specify an X509 certificate to use for authentication purposes  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types

None. The **Test-CsMcxPushNotification** cmdlet does not accept pipelined input.
  
## Return Types

The **Test-CsMcxPushNotification** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  

