---
title: Block inbound calls in Skype for Business Online
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 02/06/2018
ms.topic: article
ms.assetid: 
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
ms.reviewer: yinq
appliesto:
- Skype for Business 
localization_priority: Normal
ms.custom: "Use PowerShell to manage inbound call blocking in Skype for Business Online."
---

 # Block inbound calls

Skype for Business Online Calling Plans now supports blocking of inbound calls from the public switched telephone network (PSTN). This feature allows a tenant-global list of number patterns to be defined so that the caller ID of every incoming PSTN call to the tenant can be checked against the list for a match. If a match is made, an incoming call is rejected. 

This inbound call blocking feature only works on inbound calls that originate from the PSTN and only works on a tenant-global basis. It's not available on a per user basis.  

This feature isn't yet available for Direct Routing.

>[!NOTE]
> Blocked callers may experience slightly different behaviors when they have been blocked. The behavior is based on how the blocked caller’s carrier handles the notification that the call isn't allowed to be successfully completed. Examples may include a carrier message stating the call can't be completed as dialed, or simply dropping the call.

## Call blocking admin controls and information

Admin controls for blocking numbers are provided using PowerShell only. Number block patterns are defined as regular expression patterns. The order of the expressions is unimportant – the first pattern matched in the list results in the call being blocked. A new number or pattern that's added or removed in the blocked callers list may take up to 24 hours for the pattern to become active.

## Call blocking PowerShell commands

Number patterns are managed through the **CsInboundBlockedNumberPattern** commands **New**, **Get**, **Set**, and **Remove**. You can manage a given pattern by using these cmdlets, including the ability to toggle the activation of a given pattern.
- **Get-CsInboundBlockedNumberPattern**
Returns a list of all blocked number patterns added to the tenant list including Name, Description, Enabled (True/False), and Pattern for each.
- **New-CsInboundBlockedNumberPattern**
Adds a blocked number pattern to the tenant list.
- **Remove-CsInboundBlockedNumberPattern**
Removes a blocked number pattern from the tenant list.
- **Set-CsInboundBlockedNumberPattern**
Modifies one or more parameters of a blocked number pattern in the tenant list.

Viewing and activating the entire call blocking feature is managed through the **CsTenantBlockingCallingNumbers** commands **Get** and **Set**. 
- **Get-CsTenantBlockedCallingNumbers**
Returns the parameters for the global blocked number list including Enabled (True/False). There's a single global tenant policy that can't be modified manually other than to turn the feature on or off.
- **Set-CsTenantBlockedCallingNumbers**
Allows modifying the global tenant blocked calls to be turned on and off at the tenant level.

### Examples

#### Block a number

In this example, the -Enabled and -Description parameters are optional:

```
New-CsInboundBlockedNumberPattern -Name “<name>” -Enabled $True -Description “<description>” -Pattern “^[+]?13125550000”
```

Creating a new pattern will by default add the pattern as enabled. The description is an optional field to provide more information. 

We recommend that you provide a meaningful name to easily understand why the pattern was added. In the case of simply blocking spam numbers, consider naming the rule the same as the number pattern that's being matched and add additional information in the description as required.

Patterns are matched using Regular Expressions (Regex). 
Allow time for replication before you test and validate.

#### Allow a number

In this example, the -Identity parameter is required:

```
Remove-CsInboundBlockedNumberPattern -Identity “<identity>”
```
 
If the identity isn't known, use the **Get-CsInboundBlockedNumberPattern** cmdlet to first locate the proper pattern and note the identity. Then, run the **Remove-CsTenantBlockedNumberPattern** cmdlet and pass the appropriate identity value.

Allow time for replication before you test and validate.

#### View all number patterns
Running this cmdlet returns a list of all blocked numbers that are entered for a tenant: 

```
Get-CsInboundBlockedNumberPattern
```

Use built-in PowerShell filtering abilities to parse the returned values as required.

## Add number exceptions

You can add exceptions to blocked number patterns through the **CsTenantBlockNumberExceptionPattern** commands, **New**, **Get**, **Set**, and **Remove**. 
- **New-CsTenantBlockedNumberExceptionPattern** adds a number exception pattern to the tenant list. 
- **Get-CsTenantBlockedNumberExceptionPattern** returns a list of all number exception patterns added to the tenant list. 
- **Set-CsTenantBlockedNumberExceptionPattern** modifies one or more parameters to a number exception pattern in the tenant list. 
- **Remove-CsTenantBlockedNumberExceptionPattern** removes a number exception pattern from the tenant list.

### Examples

#### Add a number exception

In this example, a new number exception pattern is created and will by default add the pattern as enabled. The -Enabled and -Description parameters are optional.

```
New-CsTenantBlockedNumberExceptionPattern -Identity <XdsGlobalRelativeIdentity> -Tenant <GUID> -Pattern <String> -Enabled <bool> -Description <string>
```

```
New-CsTenantBlockedNumberExceptionPattern -Identity InternationalPrefix -Tenant daacb588-18ef-4f77-8c83-955af9615930 -Pattern "^011(\d*)$" -Description "Allow international prefix in US"  
```

#### View all number exceptions

In this example, the -Identity parameter is optional. If -Identity isn't specified, this cmdlet returns a list of all number exception patterns entered for a tenant. 
 
```
Get-CsTenantBlockedNumberExceptionPattern -Identity <XdsGlobalRelativeIdentity> -Tenant <GUID>
``` 
 
```
Get-CsTenantBlockedNumberExceptionPattern -Tenant daacb588-18ef-4f77-8c83-955af9615930
```

#### Modify a number exception

In this example, the -Identity parameter is mandatory. The **Set-CsTenantBlockedNumberExceptionPattern** cmdlet lets you modify one or more parameters for a given number pattern identity. 
 
```
Set-CsTenantBlockedNumberExceptionPattern -Identity <XdsGlobalRelativeIdentity> -Tenant <GUID> -Enabled <bool> -Description <string> -Pattern <string> 
```
```
Set-CsTenantBlockedNumberExceptionPattern -Identity InternationalPrefix -Tenant daacb588-18ef-4f77-8c83-955af9615930  -Pattern "^022(\d*)$" 
```

#### Remove a number exception

In this example, the -Identity parameter is required. This cmdlet will remove the given number pattern from the tenant list.  If the identity isn't known, use the **Get-CsInboundBlockedNumberPattern** cmdlet to first locate the proper pattern and note the identity. Then, run the **Remove-CsTenantBlockedNumberExceptionPattern** cmdlet and pass the appropriate Identity value.  
Allow time for replication before you test and validate.  

``` 
Remove-CsTenantBlockedNumberExceptionPattern -Identity <XdsGlobalRelativeIdentity> -Tenant <GUID>
```
```
Remove-CsTenantBlockedNumberExceptionPattern -Identity InternationalPrefix -Tenant daacb588-18ef-4f77-8c83-955af9615930
``` 

### Test whether a number is blocked

Use the **Test-CsInboundBlockedNumberPattern** cmdlet to verify whether a number is blocked in the tenant.
 
In this example, the -Phonenumber and -Tenant parameters are required. The -PhoneNumber parameter should be a numeric string without any additional characters such as + or -. In TRPS, the -Tenant parameter is optional. The resulting isNumberBlocked parameter returns a value of True if the number is blocked in the tenant and False if it's not blocked.
```
Test-CsInboundBlockedNumberPattern –Tenant <GUID> -PhoneNumber <String> 
```
```
Test-CsInboundBlockedNumberPattern -Tenant e09ad6bc-1d3c-4650-8cae-02f6c5a04b45 -PhoneNumber 4255550101 
```
|httpResponseCode  |isNumberBlocked   |errorMessage |
|---------|---------|---------|
|200    | True        |         |

```
Test-CsInboundBlockedNumberPattern -Tenant e09ad6bc-1d3c-4650-8cae-02f6c5a04b45 -PhoneNumber 6045550188
``` 

|httpResponseCode  |isNumberBlocked   |errorMessage |
|---------|---------|---------|
|200    | False        |         |

## A note about Regex
As stated earlier, the pattern matching for blocking callers is done by using Regex. Multiple tools are available online to help validate a Regex pattern match. If you aren't familiar with Regex patterns, we recommend that you take some time to familiarize yourself with the basics. To make sure you get expected results, use a tool for validating pattern matches before you add new blocked number matches to your tenant. 

## Related topics
- [Set up your computer to manage Skype for Business Online by using Windows PowerShell](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)

