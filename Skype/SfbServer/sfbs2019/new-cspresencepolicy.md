---
title: "New-CsPresencePolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a0b54f25-db48-4797-8f0e-0e826830217c
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsPresencePolicy
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new presence policy at either the site scope or the per-user scope. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsPresencePolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxCategorySubscription <UInt16>] [-MaxPromptedSubscriber <UInt16>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 creates a new per-user presence policy with the Identity RedmondPresencePolicy. In this example, the value of the MaxPromptedSubscriber property is set to 400 and the value of the MaxCategorySubscription property is set to 500.
  
```
New-CsPresencePolicy -Identity "RedmondPresencePolicy" -MaxPromptedSubscriber 400 -MaxCategorySubscription 500
```

### EXAMPLE 2

In Example 2, a new per-user presence policy is initially created in memory, and only later converted to an actual presence policy. To do this, the first command in the example creates a presence policy with the Identity RedmondPresencePolicy and stores this policy in a variable named $x. The InMemory parameter ensures that the policy is created in memory only, and is not immediately added to Lync Server.
  
Commands 2 and 3 are next used to configure the MaxPromptedSubscriber and the MaxCategorySubscription properties of the virtual policy. After the policy values have been set, line 4 uses the **Set-CsPresencePolicy** cmdlet and the Instance parameter to create an actual presence policy based on the information stored in $x. This final step is crucial: if you do not call the **Set-CsPresencePolicy** cmdlet the policy will exist only in memory, and will disappear as soon as you end your Windows PowerShell session or delete the variable $x. 
  
```
$x = New-CsPresencePolicy -Identity "RedmondPresencePolicy" -InMemory
$x.MaxPromptedSubscriber = 400
$x.MaxCategorySubscription = 500
Set-CsPresencePolicy -Instance $x
```

## Detailed Description
<a name="sectionSection1"> </a>

Presence information (which, among other things, lets you know whether a contact is available to take part in an instant messaging conversation) is invaluable. At the same time, however, there is a cost associated with presence information: the more presence subscriptions you have the more network bandwidth must be devoted to updating presence information. If network bandwidth is a concern, you might want to limit the number of presence subscriptions any one user can have.
  
The **CsPresencePolicy** cmdlets enable you to manage two important aspects of presence subscriptions: prompted subscribers and category subscriptions. When you are added to another person's Lync Contacts list, the default behavior is for you to receive a pop-up notification informing you that you have been added to that list. Until you dismiss the pop-up, each notification counts as a prompted subscriber. The presence policy's MaxPromptedSubscriber property enables you to specify the maximum number of unresolved notification dialogs a user can have. (If a user reaches the maximum amount then he or she will not receive new contact notifications, at least not until some of those dialogs have been resolved.) 
  
Category subscriptions represent a request for a specific category of information; for example, an application that requests calendar data. The MaxCategorySubscription property enables administrators to place a limit on the number of category subscriptions a user can have.
  
Prior to the release of Lync Server, prompted subscriber and category subscriptions were managed on a global basis. With the **CsPresencePolicy** cmdlets you can manage these presence subscriptions at the global scope, the site scope, or the per-user scope. This enables you to control bandwidth use while, at the same time, ensuring that users have access to the presence information they need to do their jobs. 
  
The **New-CsPresencePolicy** cmdlet provides a way for you to create custom presence policies at either the site scope or the per-user scope. Policies created at the site scope are automatically applied to that site; policies created at the per-user scope must be assigned to users by running the **Grant-CsPresencePolicy** cmdlet. Note that you cannot create a new presence policy at the global scope, nor can you create a second presence policy at an individual site. (For example, the Redmond site can host only one presence policy.) 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsPresencePolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsPresencePolicy"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new presence policy. To create a new per-user policy, use syntax similar to this: -Identity "RedmondPresencePolicy". To create a new policy at the site scope, use syntax similar to this: -Identity "site:Redmond".  <br/> Note that you cannot create a new presence policy at the global scope. In addition, your command will fail if the site in question already hosts a presence policy, or if you try to use the Identity of a per-user policy that already exists.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide additional text to accompany a presence policy. For example, the Description might include information about the users the policy should be assigned to.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _MaxCategorySubscription_ <br/> |Optional  <br/> |System.UInt16  <br/> |The maximum number of category subscriptions allowed at any one time. A category subscription represents a request for a specific category of information; for example, an application that requests calendar data.  <br/> MaxCategorySubscription can be set to any integer value between 0 and 3000; the default value is 1000.  <br/> |
| _MaxPromptedSubscriber_ <br/> |Optional  <br/> |System.UInt16  <br/> |The maximum number of promoted subscribers a user can have at any one time. By default, any time you are added to another user's Contacts list a notification dialog appears on screen informing you of this fact, and giving you the chance to do such things as add the person to your own Contacts list or block the person from viewing your presence. Until you take action and dismiss the dialog box, each notification counts as a prompted subscriber.  <br/> MaxPromptedSubscriber can be set to any integer value between 0 and 600, inclusive; the default value is 200. If you set this value to 0, users will not receive any notifications when they are added to another user's Contacts list.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsPresencePolicy** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **New-CsPresencePolicy** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Presence.PresencePolicy object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsPresencePolicy](get-cspresencepolicy.md)
  
[Grant-CsPresencePolicy](grant-cspresencepolicy.md)
  
[Remove-CsPresencePolicy](remove-cspresencepolicy.md)
  
[Set-CsPresencePolicy](set-cspresencepolicy.md)

