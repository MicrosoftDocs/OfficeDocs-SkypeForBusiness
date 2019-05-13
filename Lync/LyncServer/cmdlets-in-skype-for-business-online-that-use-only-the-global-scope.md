---
title: Cmdlets in Skype for Business Online that use only the global scope
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Cmdlets that use only the global scope
ms:assetid: 0ffd3bc9-a6a1-4c2e-8d52-e599acc49d2d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362771(v=OCS.15)
ms:contentKeyID: 56558800
ms.date: 05/04/2015
manager: serdars
mtps_version: v=OCS.15
---

# Cmdlets in Skype for Business Online that use only the global scope

 


A number of Skype for Business Online settings are available only at the *global scope*. This means that there is a single collection of settings that applies to all the users who are assigned to that tenant. (Each tenant has its own unique collection of global settings.) When you are using cmdlets that are limited to the global scope, the Identity parameter is optional. For example, to retrieve meeting configuration settings, you can use this command:

    Get-CsMeetingConfiguration -Identity "global"

Alternatively, you can omit the Identity parameter and use this simpler command instead:

    Get-CsMeetingConfiguration

Because there is only one global collection of meeting configuration settings, the two commands return the exact same information. The Identity parameter can also be omitted when using one of the **Set-Cs** cmdlets. These two commands are identical:

    Set-CsMeetingConfiguration -Identity "global" -AdmitAnonymousUsersByDefault $False
    Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False

The two commands are identical because, by default, Windows PowerShell will modify the global collection if you do not include the Identity parameter.

The following cmdlets operate only at the global scope:

  - [Get-CsImFilterConfiguration](https://technet.microsoft.com/en-us/library/gg398980\(v=ocs.15\))

  - [Get-CsMeetingConfiguration](https://technet.microsoft.com/en-us/library/gg425875\(v=ocs.15\))

  - [Get-CsPrivacyConfiguration](https://technet.microsoft.com/en-us/library/gg413002\(v=ocs.15\))

  - [Get-CsTenantFederationConfiguration](https://technet.microsoft.com/en-us/library/jj994072\(v=ocs.15\))

  - [Get-CsTenantHybridConfiguration](https://technet.microsoft.com/en-us/library/jj994034\(v=ocs.15\))

  - [Get-CsTenantLicensingConfiguration](https://technet.microsoft.com/en-us/library/dn362770\(v=ocs.15\))

  - [Get-CsTenantPublicProvider](https://technet.microsoft.com/en-us/library/jj994016\(v=ocs.15\))

  - [Remove-CsVoicePolicy](https://technet.microsoft.com/en-us/library/gg398309\(v=ocs.15\))

  - [Set-CsMeetingConfiguration](https://technet.microsoft.com/en-us/library/gg398648\(v=ocs.15\))

  - [Set-CsPrivacyConfiguration](https://technet.microsoft.com/en-us/library/gg398484\(v=ocs.15\))

Note that the **Remove-CsVoicePolicy** cmdlet is something of an anomaly. First, this cmdlet does require you to include the Identity parameter:

    Remove-CsVoicePolicy -Identity "global"

Second, the **Remove-CsVoicePolicy** cmdlet does not actually delete the global voice policy; Skype for Business Online does not allow you to delete global policies or configuration settings. What the cmdlet does do is enable you to reset all the properties in the global voice policy to their default values. For example, by default, the AllowCallForwarding property is set to False. However, AllowCallForwarding may have been modified, with the value now set to True. When you run the **Remove-CsVoicePolicy** cmdlet, the AllowCallForwarding property will revert to its default value: False. The following table summarizes this scenario:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>AllowCallForwarding Value</th>
<th>Scenario</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>False</p></td>
<td><p>Default value</p></td>
</tr>
<tr class="even">
<td><p>True</p></td>
<td><p>After the global policy has been modified</p></td>
</tr>
<tr class="odd">
<td><p>False</p></td>
<td><p>After <strong>Remove-CsVoicePolicy</strong> cmdlet has been run</p></td>
</tr>
</tbody>
</table>


## See Also


[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[The Skype for Business Online cmdlets](https://technet.microsoft.com/en-us/library/dn362817\(v=ocs.15\))

