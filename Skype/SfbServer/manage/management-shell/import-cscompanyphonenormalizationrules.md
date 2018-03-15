---
title: "Import-CsCompanyPhoneNormalizationRules"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: fe4c28d7-b6bf-4678-bfe9-11b9aed2c03d
description: "Use the Import-CsCompanyPhoneNormalizationRules cmdlet to import custom phone normalization rules defined in Company_Phone_Number_Normalization_Rules.txt used in previous server versions into Skype for Business Server 2015 environments."
---

# Import-CsCompanyPhoneNormalizationRules
 
Use the **Import-CsCompanyPhoneNormalizationRules** cmdlet to import custom phone normalization rules defined in Company_Phone_Number_Normalization_Rules.txt used in previous server versions into Skype for Business Server 2015 environments.
  
```
Import-CsCompanyPhoneNormalizationRules [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

This example reads the phone normalization rules at the specified path and applies them globally.
  
```
Import-CsCompanyPhoneNormalizationRules -Filename "C:\Data\Company_Phone_Number_Normalization_Rules.txt" -Identity Global
```

## Detailed Description
<a name="DetailedDescription"> </a>

Address Book phone normalization rule configurations have been migrated from the plain text file Company_Phone_Number_Normalization_Rules.txt to central management configuration in Skype for Business Server for easier and more convenient manageability. In order for the Skype for Business Server Address Book service to pick up custom normalization rules, normalization rule definitions must be in the central management configuration store. The **Import-CsCompanyPhoneNormalizationRules** cmdlet reads all custom normalization rules defined in the file specified by the _FileName_ parameter and ensures the same normalization rules exist in the central management configuration store. Company_Phone_Number_Normalization_Rules.txt and phone normalization rules defined in central management store must be kept in sync until the environment is fully migrated to Skype for Business Server 2015.
  
The **Import-CsCompanyPhoneNormalizationRules** cmdlet uses GUID names for the new normalization rules as name is required in the Skype for Business Server configuration schema, and does not exist in the legacy normalization file format. These GUID names can be replaced with more appropriate values by using **Set-CsAddressBookNormalizationConfiguration** cmdlet after the migration is completed.
  
Alternatively, the **New-CsAddressBookNormalizationConfiguration** and **Set-CsAddressBookNormalizationConfiguration** cmdlets can also be used to keep custom normalization rule definitions in sync.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |Specifies the full path to the input Company_Phone_Number_Normalization_Rules.txt file. For example:  <br/>  `-FileName "C:\Data\Company_Phone_Number_Normalization_Rules.txt"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the address book normalization configuration settings to be updated. To modify the global settings, use this syntax:  <br/>  `-Identity global` <br/> To modify settings configured at the site scope:  <br/>  `-Identity site:Redmond` <br/> To modify settings at the service level:  <br/>  `-Identity service:Registrar:atl-cs-001.litwareinc.com` <br/> Note that address book normalization configuration settings can only be applied to the Registrar service. An error will occur if you try to apply these settings to any other service.  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsAddressBookNormalizationConfiguration](set-csaddressbooknormalizationconfiguration.md)
  
[Remove-CsAddressBookNormalizationConfiguration](remove-csaddressbooknormalizationconfiguration.md)
  
[New-CsAddressBookNormalizationConfiguration](new-csaddressbooknormalizationconfiguration.md)
  
[Get-CsAddressBookNormalizationConfiguration](get-csaddressbooknormalizationconfiguration.md)

