---
title: "Get-CsCallViaWorkPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9771da00-06ec-4f0b-bfe2-2c6d0e9a2e7b
description: "Use the Get-CsCallViaWorkPolicy cmdlet to return call via work policies. Call via work policies enable and manage the characteristics of outbound calls placed through the Skype for Business client."
---

# Get-CsCallViaWorkPolicy
 
Use the **Get-CsCallViaWorkPolicy** cmdlet to return call via work policies. Call via work policies enable and manage the characteristics of outbound calls placed through the Skype for Business client.
  
```
Get-CsCallViaWorkPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

This example returns the properties of the policy currently assigned to the Redmond site.
  
```
Get-CsCallViaWorkPolicy -Identity Site:Redmond
```

## Detailed Description
<a name="DetailedDescription"> </a>

To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters when indicating the policy (or policies) to be returned. For example, to return all the policies configured at the site scope use this syntax: `-Filter "site:*"`. To return a collection of all the per-user policies, use this syntax: `-Filter "tag:*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> | Specifies the identity of the policy to be returned. Call via work policies can be returned at the global, site, or per-user scope. <br/>  Global syntax: `-Identity Global` <br/>  Site syntax: `-Identity Site:Redmond` <br/>  Per-user syntax: `-Identity CallviaWorkStandard` <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the call via work policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |This parameter is reserved for internal Microsoft use.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsCallViaWorkPolicy** returns **[Microsoft.Rtc.Management.WritableConfig.Policy.CallViaWork.CallViaWorkPolicy]** instances.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Remove-CsCallViaWorkPolicy](remove-cscallviaworkpolicy.md)
  
[Set-CsCallViaWorkPolicy](set-cscallviaworkpolicy.md)
  
[New-CsCallViaWorkPolicy](new-cscallviaworkpolicy.md)
  
[Grant-CsCallViaWorkPolicy](grant-cscallviaworkpolicy.md)

