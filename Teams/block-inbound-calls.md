---
title: Block inbound calls in Microsoft Teams
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection:
  - M365-voice
audience: Admin
ms.reviewer: roykuntz
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom: Learn how to use PowerShell to manage inbound call blocking.
---

# Block inbound calls

Microsoft Calling Plans, Direct Routing, and Operator Connect all support blocking inbound calls from the Public Switched Telephone Network (PSTN). This feature allows an administrator to define a  list of number patterns at the tenant global level so that the caller ID of every incoming PSTN call to the tenant can be checked against the list for a match. If a match is made, an incoming call is rejected.

This inbound call blocking feature only works on inbound calls that originate from the PSTN and only works on a tenant global level. Individual Teams users can't manipulate this list. The Teams client does allow individual users to block PSTN calls. For information about how your end users can implement call blocking, see [Manage call settings in Teams](https://support.microsoft.com/office/manage-your-call-settings-in-teams-456cb611-3477-496f-b31a-6ab752a7595f).

> [!NOTE]
> Blocked callers may experience slightly different behaviors when they've been blocked. The behavior is based on how the blocked caller's carrier handles the notification that the call isn't allowed to be successfully completed. Examples may include a carrier message stating the call can't be completed as dialed, or simply dropping the call.

## Call blocking admin controls and information

Admin controls for blocking numbers are provided using PowerShell only. Number block patterns are defined as regular expression patterns. The order of the expressions is unimportant – the first pattern matched in the list results in the call being blocked. A new number or pattern that's added or removed in the blocked callers list may take up to 24 hours for the pattern to become active.

## Call blocking PowerShell commands

You manage number patterns by using the **New-**, **Get-**, **Set-**, and **Remove-CsInboundBlockedNumberPattern** cmdlets. You can manage a given pattern by using these cmdlets, including the ability to toggle the activation of a given pattern.

- [Get-CsInboundBlockedNumberPattern](/powershell/module/skype/get-csinboundblockednumberpattern)
returns a list of all blocked number patterns added to the tenant list including Name, Description, Enabled (True/False), and Pattern for each.
- [New-CsInboundBlockedNumberPattern](/powershell/module/skype/new-csinboundblockednumberpattern)
adds a blocked number pattern to the tenant list.
- [Remove-CsInboundBlockedNumberPattern](/powershell/module/skype/remove-csinboundblockednumberpattern)
removes a blocked number pattern from the tenant list.
- [Set-CsInboundBlockedNumberPattern](/powershell/module/skype/set-csinboundblockednumberpattern)
modifies one or more parameters of a blocked number pattern in the tenant list.

Viewing and activating the entire call blocking feature is managed through the **Get-** and **Set-CsTenantBlockingCallingNumbers** cmdlets.

- [Get-CsTenantBlockedCallingNumbers](/powershell/module/skype/get-cstenantblockedcallingnumbers) returns the inbound block number patterns and the inbound exempt number patterns parameters for the global blocked number list. This cmdlet also returns whether blocking has been Enabled (True or False). There's a single global tenant policy that can't be modified manually other than to turn the feature on or off.
- [Set-CsTenantBlockedCallingNumbers](/powershell/module/skype/set-cstenantblockedcallingnumbers) allows modifying the global tenant blocked calls to be turned on and off at the tenant level.

### Examples

#### Block a number

In the following example, the tenant administrator wants to block all calls coming from the number range 1 (312) 555-0000 to 1 (312) 555-9999. The number pattern is created so that both numbers in range with + prefixed and numbers in the range without + prefixed are matched. You don't need to include the symbols – and () in the phone numbers because the system strips these symbols before matching.  To turn on the number pattern, the **Enabled** parameter is set to True. To disable this specific number pattern, set the parameter to False.

```PowerShell
New-CsInboundBlockedNumberPattern -Name "BlockRange1" -Enabled $True -Description "Block Contoso" -Pattern "^\+?1312555\d{4}$"
```

In the next example, the tenant administrator wants to block all calls coming from the number 1 (412) 555-1234. To turn on the number pattern, the **Enabled** parameter is set to True.

```PowerShell
New-CsInboundBlockedNumberPattern -Name "BlockNumber1" -Enabled $True -Description "Block Fabrikam" -Pattern "^\+?14125551234$"
```

Creating a new pattern adds the pattern as enabled by default. The description is an optional field to provide more information.

We recommend that you provide a meaningful name to easily understand why the pattern was added. In the case of simply blocking spam numbers, consider naming the rule the same as the number pattern that's being matched and add additional information in the description as required.

Patterns are matched using Regular Expressions (Regex). For more information, see [Using Regex](#using-regex).

Allow time for replication before you test and validate.

#### Allow a number

You can allow a number to call by removing the blocked number pattern. In the following example, the tenant administrator wants to allow 1 (412) 555-1234 to make calls again.

```PowerShell
Remove-CsInboundBlockedNumberPattern -Identity "BlockNumber1"
```

If the identity isn't known, use the **Get-CsInboundBlockedNumberPattern** cmdlet to first locate the proper pattern and note the identity. Then, run the **Remove-CsInboundBlockedNumberPattern** cmdlet and pass the appropriate identity value.

Allow time for replication before you test and validate.

#### View all number patterns

Running this cmdlet returns a list of all blocked numbers that are entered for a tenant:

```powershell
Get-CsInboundBlockedNumberPattern
```

Use built-in PowerShell filtering abilities to parse the returned values as required.

## Add number exceptions

You can add exceptions to blocked number patterns by using the **New-**, **Get-**, **Set-**, and **Remove-CsInboundExemptNumberPattern** cmdlets.

- [New-CsInboundExemptNumberPattern](/powershell/module/skype/New-CsInboundExemptNumberPattern) adds a number exception pattern to the tenant list.
- [Get-CsInboundExemptNumberPattern](/powershell/module/skype/Get-CsInboundExemptNumberPattern) returns a list of all number exception patterns added to the tenant list.
- [Set-CsInboundExemptNumberPattern](/powershell/module/skype/Set-CsInboundExemptNumberPattern) modifies one or more parameters to a number exception pattern in the tenant list.
- [Remove-CsInboundExemptNumberPattern](/powershell/module/skype/Remove-CsInboundExemptNumberPattern) removes a number exception pattern from the tenant list.

### Examples

#### Add a number exception

In the following example, the tenant administrator wants to allow the phone numbers 1 (312) 555-8882 and 1 (312) 555-8883 to make calls to the tenant, even if these two phone numbers are in the range that has been blocked in the example above. To enable this, a new number exception pattern is created as follows:

```PowerShell
New-CsInboundExemptNumberPattern  -Identity "AllowContoso1" -Pattern "^\+?1312555888[2|3]$" -Description "Allow Contoso helpdesk" -Enabled $True
```

To turn on the number pattern, the **Enabled** parameter is set to True. To disable this specific number pattern, set the parameter to False.

#### View all number exceptions

In this example, the **Identity** parameter is optional. If the **Identity** parameter isn't specified, this cmdlet returns a list of all number exception patterns entered for a tenant.

```powershell
Get-CsInboundExemptNumberPattern -Identity <String>
```

```powershell
Get-CsInboundExemptNumberPattern
```

#### Modify a number exception

The **Set-CsInboundExemptNumberPattern** cmdlet lets you modify one or more parameters for a given number pattern identity. In this example, the **Identity** parameter is required.

```powershell
Set-CsInboundExemptNumberPattern -Identity <String> -Enabled <bool> -Description <string> -Pattern <string>
```

```powershell
Set-CsInboundExemptNumberPattern -Identity "AllowContoso1" -Enabled $False
```

#### Remove a number exception

The **Remove-CsInboundExemptNumberPattern** cmdlet will remove the given number pattern from the tenant list. In this example, the **Identity** parameter is required.

If the identity isn't known, use the **Get-CsInboundExemptNumberPattern** cmdlet to first locate the proper pattern and note the identity. Then, run the **Remove-CsInboundExemptNumberPattern** cmdlet and pass the appropriate identity value. Allow time for replication before you test and validate.

```powershell
Remove-CsInboundExemptNumberPattern -Identity <String>
```

```powershell
Remove-CsInboundExemptNumberPattern -Identity "AllowContoso1"
```

## Test whether a number is blocked

Use the **Test-CsInboundBlockedNumberPattern** cmdlet to verify whether a number is blocked in the tenant.

The **PhoneNumber** parameter is required, and should be a numeric string without any additional characters, such as +, - or (). The resulting **IsNumberBlocked** parameter returns a value of True if the number is blocked in the tenant; the parameter returns False if it's not blocked.

```powershell
Test-CsInboundBlockedNumberPattern –Tenant <GUID> -PhoneNumber <String>
```

### Examples

In these examples you can see that the phone number 1 (312) 555-8884 is blocked as it should be due to it being in the blocked range above, while the phone number 1 (312) 555-8883 is allowed to call as it should be based on the exemption created above.

```PowerShell
Test-CsInboundBlockedNumberPattern -PhoneNumber 13125558884

RunspaceId      : 09537e45-6f0c-4001-8b85-a79002707b0c
httpStatusCode  : NoContent
IsNumberBlocked : True
errorMessage    :

Test-CsInboundBlockedNumberPattern -PhoneNumber 13125558883

RunspaceId      : 09537e45-6f0c-4001-8b85-a79002707b0c
httpStatusCode  : NoContent
IsNumberBlocked : False
errorMessage    :
```

## Using Regex

The pattern matching for blocking callers is done by using Regex. Multiple tools are available online to help validate a Regex pattern match. If you aren't familiar with Regex patterns, we recommend that you take some time to familiarize yourself with the basics. To make sure you get expected results, use a tool for validating pattern matches before you add new blocked number matches to your tenant.
