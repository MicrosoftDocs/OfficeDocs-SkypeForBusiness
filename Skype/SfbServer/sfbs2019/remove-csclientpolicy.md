---
title: "Remove-CsClientPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2beb1557-8397-493e-be87-910ce01ba8f5
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsClientPolicy
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes an existing client policy. Among other things, client policies help determine the features of Lync that are available to users; for example, you might give some users the right to transfer files while denying this right to other users. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsClientPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In Example 1, the **Remove-CsClientPolicy** cmdlet is used to delete the client policy that has the Identity SalesPolicy. 
  
```
Remove-CsClientPolicy -Identity SalesPolicy
```

### EXAMPLE 2

In Example 2, the **Get-CsClientPolicy** cmdlet and the **Remove-CsClientPolicy** cmdlet are used to delete all the client policies that have been configured at the per-user scope. The command uses the **Get-CsClientPolicy** cmdlet and the Filter parameter to return a collection of all the client policies configured at the per-user scope; the filter value "tag:*" tells the **Get-CsClientPolicy** cmdlet to limit the retrieved data to client policies that have an Identity that begins with the string value "tag:". The filtered collection is then piped to the **Remove-CsClientPolicy** cmdlet, which removes each policy in the collection. 
  
```
Get-CsClientPolicy -Filter "tag:*" | Remove-CsClientPolicy
```

### EXAMPLE 3

Example 3 deletes all the client policies where the EnableAppearOffline property is set to True. To do this, the **Get-CsClientPolicy** cmdlet is first called without any additional parameters; that returns a collection of all the client policies configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where the EnableAppearOffline property is equal to True. In turn, this filtered collection is piped to the **Remove-CsClientPolicy** cmdlet, which deletes each policy in the collection. 
  
```
Get-CsClientPolicy | Where-Object {$_.EnableAppearOffline -eq $True} | Remove-CsClientPolicy
```

## Detailed Description
<a name="sectionSection1"> </a>

In Lync Server, client policies replace the Group Policy settings used in previous versions of the product. In Microsoft Office Communicator 2007 and Microsoft Office Communicator 2007 R2, Group Policy helped determine what users could do with Communicator and other clients; for example, there were Group Policy settings that determined whether or not users could save a transcript of their instant messaging sessions; whether information from Microsoft Outlook was incorporated into their presence information; and whether or not users could include emoticons or formatted text in instant messages.
  
As useful as Group Policy is, however, the technology does have some limitations when applied to Lync Server. For one thing, Group Policy is designed to be applied on a per-domain or per-organizational unit (OU) basis, which makes it difficult to target policies toward a more select group of users (for example, all the users who work in a particular department, or all the users who have a particular job title). For another, Group Policy is only applied to users who log on to the domain and who log on using a computer; Group Policy is not applied to users who access Lync Server over the Internet or who access the system by using a mobile phone. This means that the same user can have a different experience depending on the device he or she uses to log on, and where he or she logs on from.
  
To help address these inconsistencies Lync Server uses client policies instead of Group Policy. Client policies are applied each time a user accesses the system, regardless of where the user logs on from and regardless of the type of device the user logs on with. In addition, client policies, like other Lync Server policies, can readily be targeted toward selected groups of users. You can even create a custom policy that gets assigned to a single user.
  
Client policies can be configured at the global, site, and per-user scopes. Policies that have been configured at the site or per-user scope, can later be deleted by using the **Remove-CsClientPolicy** cmdlet. You can also run the **Remove-CsClientPolicy** cmdlet against the global policy. In that case, the global policy will not be removed; that's because global policies cannot be deleted. However, all the properties in the global policy will be reset to their default values. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsClientPolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsClientPolicy"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the client policy to be removed. To "remove" the global policy, use the following syntax: -Identity global. (Note that the global policy cannot actually be removed. Instead, all the properties in that policy will be reset to their default values.) To remove a site policy, use syntax similar to this: -Identity "site:Redmond". To remove a per-user policy, use syntax similar to this: -Identity "SalesDepartmentPolicy". You cannot use wildcards when specifying a policy Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If this parameter is present, the policy will automatically be removed even if it is currently assigned to at least one user. If this parameter is not present, then the **Remove-CsClientPolicy** cmdlet will not automatically remove a per-user policy that is assigned to at least one user. Instead, a confirmation prompt will appear asking if you are sure that you want to remove the policy. You must answer yes (by pressing the Y key) before the command will continue and the policy will be removed.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Policy.Client.ClientPolicy object. The **Remove-CsClientPolicy** cmdlet accepts pipelined instances of the client policy object. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Remove-CsClientPolicy** cmdlet does not return a value. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Client.ClientPolicy object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsClientPolicy](get-csclientpolicy.md)
  
[Grant-CsClientPolicy](grant-csclientpolicy.md)
  
[New-CsClientPolicy](new-csclientpolicy.md)
  
[Set-CsClientPolicy](set-csclientpolicy.md)

