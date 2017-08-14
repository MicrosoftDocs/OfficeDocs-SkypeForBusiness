---
title: Disable-CsPublicProvider
ms.prod: SKYPEFORBUSINESS
ms.assetid: df1338ea-fe6d-45da-a39c-86108bb54ef5
---


# Disable-CsPublicProvider
[]
Disables a public provider configured for use in your organization. A public provider is an organization that provides instant messaging, presence, and related services to the general public. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Disable-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

Example 1 disables the public provider with the Identity Skype. This command will return an error if MSN is already disabled.
  
    
    

```

Disable-CsPublicProvider -Identity "Skype"
```


### EXAMPLE 2

Example 2 disables all the public providers that are currently enabled. To do this, the command first uses the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers currently in use in the organization. This collection is piped to the **Where-Object** cmdlet, which picks out only those providers where the Enabled property is equal to True. In turn, this filtered collection is piped to the **Disable-CsPublicProvider** cmdlet, which disables each provider in the collection.
  
    
    

```
Get-CsPublicProvider | Where-Object {$_.Enabled -eq $True} | Disable-CsPublicProvider
```


### EXAMPLE 3

The command shown in Example 3 disables all the public providers that are current enabled and that have a verification level set to AlwaysVerifiable. To accomplish this task, the command first calls the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects the providers that meet two criteria: 1) the VerificationLevel property is equal to AlwaysVerifiable; and, 2) the Enabled property is equal to True. (The -and operator tells the **Where-Object** cmdlet that objects must meet all the specified criteria in order to be selected.) The filtered collection is then piped to the **Disable-CsPublicProvider** cmdlet, which disables each provider in that collection.
  
    
    

```
Get-CsPublicProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable" -and $_.Enabled -eq $True} | Disable-CsPublicProvider
```


## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Skype for Business. Skype for Business Server 2015 allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
    
    
A public provider is an organization that provides Session Initiation Protocol (SIP) communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider. For example, if you federate with Skype your users will be able to exchange instant messages and presence information with anyone who has a Skype instant messaging account.
  
    
    
In order to federate with a public provider you need to create and enable a new public provider. (In addition, the public provider will need to create a federation relationship with you.) When you create a public provider, you have the option of either enabling or disabling that federation relationship. If a public provider is enabled, then users in your organization will be able to exchange instant messages and presence information with people who have accounts with the public provider. If a public provider is disabled, then your ability to communicate with people who have accounts with the public provider will be suspended, and will remain suspended until the provider has been re-enabled. If you need to temporarily suspend a provider relationship you can do so by using the **Disable-CsPublicProvider** cmdlet. If you prefer to delete that provider altogether, use the **Remove-CsPublicProvider** cmdlet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the public provider to be disabled. The Identity is typically the name of the website providing the services.  <br/> |
| _Instance_ <br/> |Optional  <br/> |DisplayPublicProvider object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object. The **Disable-CsPublicProvider** cmdlet accepts pipelined instances of the public provider object.
  
    
    

## Return Types

None. Instead, the cmdlet disables instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object.
  
    
    

## See also


#### 


  
    
    
 [Enable-CsPublicProvider](enable-cspublicprovider.md)
  
    
    
 [Get-CsPublicProvider](get-cspublicprovider.md)
  
    
    
 [New-CsPublicProvider](new-cspublicprovider.md)
  
    
    
 [Remove-CsPublicProvider](remove-cspublicprovider.md)
  
    
    
 [Set-CsPublicProvider](set-cspublicprovider.md)
