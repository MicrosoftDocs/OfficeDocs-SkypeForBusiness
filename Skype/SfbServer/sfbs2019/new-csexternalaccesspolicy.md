---
title: "New-CsExternalAccessPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 624a878e-6bbf-4e8b-9a5e-e7b5521fa4c1
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsExternalAccessPolicy
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables you to create a new external access policy. External access policies determine whether or not your users can: 1) communicate with users who have Session Initiation Protocol (SIP) accounts with a federated organization; 2) communicate with users who have SIP accounts with a public instant messaging (IM) provider such as MSN; and, 3) access Lync Server over the Internet, without having to log on to your internal network. This cmdlet was introduced in Lync Server 2010. 
  
```
New-CsExternalAccessPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Description <String>] [-EnableFederationAccess <$true | $false>] [-EnableOutsideAccess <$true | $false>] [-EnablePublicCloudAccess <$true | $false>] [-EnablePublicCloudAudioVideoAccess <$true | $false>] [-EnableXmppAccess <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 creates a new external access policy that has the Identity site:Redmond; upon creation, this policy will automatically be assigned to the Redmond site. Note that this new policy sets both the EnableFederationAccess and the EnableOutsideAccess properties to True.
  
```
New-CsExternalAccessPolicy -Identity site:Redmond -EnableFederationAccess $True -EnableOutsideAccess $True
```

### EXAMPLE 2

Example 2 demonstrates the use of the InMemory parameter; this parameter enables you to create an in-memory-only instance of an external access policy. After it has been created, you can modify the in-memory-only instance, then use the **Set-CsExternalAccessPolicy** cmdlet to transform the virtual policy into a real external access policy. 
  
To do this, the first command in the example uses the **New-CsExternalAccessPolicy** cmdlet and the InMemory parameter to create a virtual policy with the Identity RedmondAccessPolicy; this virtual policy is stored in a variable named $x. The next three commands are used to modify three properties of the virtual policy: EnableFederationAccess, EnablePublicCloudAccess, and the EnableOutsideAccess. Finally, the last command uses the **Set-CsExternalAccessPolicy** cmdlet to create an actual per-user external access policy with the Identity RedmondAccessPolicy. If you do not call the **Set-CsExternalAccessPolicy** cmdlet, then the virtual policy will disappear as soon as you end your Windows PowerShell session or delete the variable $x. Should that happen, an external access policy with the Identity RedmondAccessPolicy will never be created. 
  
```
$x = New-CsExternalAccessPolicy -Identity RedmondAccessPolicy -InMemory
$x.EnableFederationAccess = $True
$x.EnablePublicCloudAccess = $True
$x.EnableOutsideAccess = $True
Set-CsExternalAccessPolicy -Instance $x  
```

## Detailed Description
<a name="sectionSection1"> </a>

When you install Lync Server your users are only allowed to exchange instant messages and presence information among themselves: by default, they can only communicate with other people who have SIP accounts in your Active Directory Domain Services. In addition, users are not allowed to access Lync Server over the Internet; instead, they must be logged on to your internal network before they will be able to log on to Lync Server.
  
That might be sufficient to meet your communication needs. If it doesn't meet your needs you can use external access policies to extend the ability of your users to communicate and collaborate. External access policies can grant (or revoke) the ability of your users to do any or all of the following:
  
1. Communicate with people who have SIP accounts with a federated organization. Note that enabling federation alone will not provide users with this capability. Instead, you must enable federation and then assign users an external access policy that gives them the right to communicate with federated users.
  
2. Communicate with people who have SIP accounts with a public instant messaging service such as MSN.
  
3. Access Lync Server over the Internet, without having to first log on to your internal network. This enables your users to use Lync Server and log on to Lync Server from an Internet café or other remote location.
  
When you install Lync Server, a global external access policy is automatically created for you. In addition to the global policy, you can also create custom external access policies at either the site or the per-user scope. If you create an external access policy at the site scope, that policy will automatically be assigned to the site upon creation. If you create an external access policy at the per-user scope, that policy will be created but will not be assigned to any users. To assign the policy to a user or group of users, use the **Grant-CsExternalAccessPolicy** cmdlet. 
  
New external access policies can be created by using the **New-CsExternalAccessPolicy** cmdlet. Note that these policies can only be created at the site or the per-user scope; you cannot create a new policy at the global scope. In addition, you can have only one external access policy per site: if the Redmond site already has been assigned an external access policy you cannot create a second policy for the site. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsExternalAccessPolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
```
Get-CsAdminRole | Where-Object  {$_.Cmdlets -match "New-CsExternalAccessPolicy"}
```

## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity to be assigned to the policy. New external access policies can be created at the site or per-user scope. To create a new site policy, use the prefix "site:" and the name of the site as your Identity. For example, use this syntax to create a new policy for the Redmond site: -Identity site:Redmond. To create a new per-user policy, use an Identity similar to this: -Identity SalesAccessPolicy.  <br/> Note that you cannot create a new global policy; if you want to make changes to the global policy, use the **Set-CsExternalAccessPolicy** cmdlet instead. Likewise, you cannot create a new site or per-user policy if a policy with that Identity already exists. If you need to make changes to an existing policy, use the **Set-CsExternalAccessPolicy** cmdlet.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide explanatory text to accompany the policy. For example, the Description might include information about the users the policy should be assigned to.  <br/> |
| _EnableFederationAccess_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the user is allowed to communicate with people who have SIP accounts with a federated organization. The default value is False.  <br/> |
| _EnableOutsideAccess_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the user is allowed to connect to Lync Server over the Internet, without logging on to the organization's internal network. The default value is False.  <br/> |
| _EnablePublicCloudAccess_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the user is allowed to communicate with people who have SIP accounts with a public Internet connectivity provider such as MSN. The default value is False.  <br/> |
| _EnablePublicCloudAudioVideoAccess_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the user is allowed to conduct audio/video conversations with people who have SIP accounts with a public Internet connectivity provider such as MSN. When set to False, audio and video options in Lync Server will be disabled any time a user is communicating with a public Internet connectivity contact.  <br/> |
| _EnableXmppAccess_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the user is allowed to communicate with users who have SIP accounts with a federated XMPP (Extensible Messaging and Presence Protocol ) partner. The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsExternalAccessPolicy** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

Creates new instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ExternalAccess.ExternalAccessPolicy object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)
  
[Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)
  
[Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)
  
[Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md)

