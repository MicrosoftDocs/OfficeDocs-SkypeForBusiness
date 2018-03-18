---
title: "Remove-CsPartnerApplication"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 3918a2eb-d464-4729-888b-fafebe2227ce
description: "Removes an existing partner application. A partner application is any application that Skype for Business Server 2015 can directly exchange security tokens with, without having to go through a third-party security token server. This cmdlet was introduced in Lync Server 2013."
---

# Remove-CsPartnerApplication
 
Removes an existing partner application. A partner application is any application that Skype for Business Server 2015 can directly exchange security tokens with, without having to go through a third-party security token server. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsPartnerApplication -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 deletes the partner application with the Identity "MicrosoftExchange".
  
```
Remove-CsPartnerApplication -Identity "MicrosoftExchange"
```

### Example 2

In Example 2, all the partner applications configured for use in the organization are deleted. To do this, the command first uses the **Get-CsPartnerApplication** cmdlet in order to return a collection of all the partner applications. This collection is then piped to the **Remove-CsPartnerApplication** cmdlet, which deletes each application in the collection.
  
```
Get-CsPartnerApplication | Remove-CsPartnerApplication
```

### Example 3

In Example 3, all the partner applications where the trust level is set to anything other than Full are deleted. To carry out this task, the command first calls the **Get-CsPartnerApplication** cmdlet without any parameters in order to return a collection of all the partner applications configured for use in the organization. This collection is then piped to the Where-Object cmdlet, which selects only those applications where the ApplicationTrustLevel property is not equal to (-ne) "Full". The applications that meet that criterion are then piped to, and removed by, the **Remove-CsPartnerApplication** cmdlet.
  
```
Get-CsPartnerApplication | Where-Object {$_.ApplicationTrustLevel -ne "Full"} | Remove-CsPartnerApplication
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, server-to-server authentication (for example, the authentication that enables Skype for Business Server 2015 and Exchange to share information) is carried out using the OAuth security protocol. This type of authentication typically requires three servers: the two servers that need to communicate with one another (Server A and B) and a third-party security token server. If Servers A and B need to communicate with one another, the two servers contact the token server (also known as an OAuth server) and obtain mutually-trusted security tokens that the two servers can exchange in order to prove their identities.
  
If you are using an on-premises version of Skype for Business Server 2015 and you need to communicate with another server product that fully supports the OAuth protocol (for example, Exchange or SharePoint) then you typically do not need to use a token server; that's because these server products are able to issue their own security tokens. However, you will need to configure the other server product (e.g., Exchange) as a partner application. (You will also need to configure Skype for Business Server 2015 as a partner application for the other server product.) In Skype for Business Server 2015, partner applications are managed by using the **CsPartnerApplication** cmdlets.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsPartnerApplication** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier of the partner application to be removed. For example:  <br/>  `-Identity "MicrosoftExchange"` <br/> Note that you cannot use wildcard characters when specifying an Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the partner application being deleted. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsPartnerApplication** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.PartnerApplication#Decorated object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsPartnerApplication** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.PartnerApplication#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPartnerApplication](get-cspartnerapplication.md)
  
[New-CsPartnerApplication](new-cspartnerapplication.md)
  
[Set-CsPartnerApplication](set-cspartnerapplication.md)

