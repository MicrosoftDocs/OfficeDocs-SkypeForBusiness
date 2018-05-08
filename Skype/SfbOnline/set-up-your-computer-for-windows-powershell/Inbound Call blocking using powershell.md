---
title: "Inboound Call blocking Using Powershell for Skype for Business Onlin"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.date: 05/07/2018
ms.topic: article
ms.assetid: 
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1keywords: None
ms.custom:
- PowerShell
description: "Use PowerShell to manage inbound call blocking in Skype for Business Online."
---

 
# Inbound PSTN Call Blocking for Calling Plans

Skype for Business Online Calling Plans now supports blocking of inbound calls from the PSTN. This feature allows a tenant global list of number patterns to be defined, the caller ID of every incoming PSTN call to the tenant will then be checked against the list for a match. If a match is made, an incoming call will be rejected. The feature only works on inbound calls originating from the PSTN and only works on a tenant global basis and is not available on a per user basis.

This is not yet available for Direct Routing.

>[Note]
 Blocked callers may experience slightly different behaviors when they have been blocked. The behavior will be based on how the blocked caller’s carrier handles the notification that the call is not allowed to be successfully completed. Examples may include a carrier message stating the call cannot be completed as dialed, or simply dropping the call.

## Call Blocking Admin Controls and Information

Admin controls for blocking numbers are provided using PowerShell only. Number block patterns are defined as regular expression patterns. It does not matter what order the expressions are listed – the first pattern matched in the list will result in the call being blocked. When a new number or pattern is added/removed in the blocked callers list it may take up to 24 hours to for the pattern to become active.

## Call Blocking PowerShell Commands

*InboundBlockedNumberPattern*
Number patterns are managed via the *CsInboundBlockedNumberPattern* commands **New**, **Get**, **Set**, and **Remove**.  A given pattern can be managed via these commandlet’s including the ability to toggle the activation of a given pattern.
•	Get-CsInboundBlockedNumberPattern
Returns a list of all blocked number patterns added to the tenant list including Name, Description, Enabled (True/False), and Pattern for each.
•	New-CsInboundBlockedNumberPattern
Adds a blocked number pattern to the tenant list.
•	Remove-CsInboundBlockedNumberPattern
Removes a blocked number pattern from the tenant list.
•	Set-CsInboundBlockedNumberPattern
Modifies one or more parameters of a blocked number pattern in the tenant list.
TenantBlockedCallingNumbers
The viewing and activation of the entire call blocking feature is managed via the CsTenantBlockingCallingNumbers commands Get and Set. 
•	Get-CsTenantBlockedCallingNumbers
Returns the parameters for the global blocked number list including Enabled (True/False). There is a single global tenant policy that cannot be modified manually other than to turn the feature completely on/off.
•	Set-CsTenantBlockedCallingNumbers
Allows modifying the global tenant blocked calls to be turned on/off at the tenant level.
Examples
Blocking a Number
New-CsInboundBlockedNumberPattern -Name “<name>” -Enabled $True -Description “<description>” -Pattern “^[+]?13125550000”
In the above example, the -Enabled and -Description parameters are optional. Creating a new pattern will by default add the pattern as enabled, and the description is always and optional field to provide more information. 
It is recommended to provide a meaningful name to easily understand why the pattern was added. In the case of simply blocking spam numbers, considered naming the rule the same as the number pattern being matched, and add additional information in the description as required.
Patterns are matched using Regular Expressions (regex). 
Allow for replication time before testing and validating.
Allowing a Number
Remove-CsInboundBlockedNumberPattern -Identity “<identity>”
In the above example, the identity parameter if required. If the Identity is not known, use the Get-CsInboundBlockedNumberPattern cmdlet to first locate the proper pattern and note the Identity. Then run the Remove cmdlet and pass the appropriate Identity value.
Allow for replication time before testing and validating.
View all Number Patterns
Get-CsInboundBlockedNumberPattern
Running the above cmdlet will return a list of all entered blocked numbers for a tenant. Use built-in PowerShell filtering abilities to parse the returned values as required.
A Note on Regex
As stated earlier, the pattern matching for blocking callers is done by using Regular Expressions (regex). There are multiple tools available online to help validate a regex pattern match. If you are not familiar with regex patterns, it is recommended you take some time to familiarize yourself with the basics and use a tool for validating pattern matches prior to adding new blocked number matches to your tenant to make sure you get expected results. 


## Related topics
[Set up your computer for skype for business online management using Windows PowerShell](set-up-your-computer-for-windows-powershell.md)