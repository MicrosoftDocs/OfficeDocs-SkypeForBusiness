---
title: Remove-CsCertificate
ms.prod: SKYPEFORBUSINESS
ms.assetid: b7a83a58-9d3f-458a-867e-44466c9817dc
---


# Remove-CsCertificate
[]
Removes a certificate previously marked as being available for use by Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsCertificate -Type <CertType[]> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Identity <XdsIdentity>] [-Previous <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 deletes all the WebServicesExternal certificates available to Skype for Business Server 2015. If any of these certificates are currently being used, the **Remove-CsCertificate** cmdlet will ask you if you are sure you want to remove the certificate; you must respond to that prompt before the command can complete. To bypass the confirmation prompt, use the Force parameter:
  
    
    

```

Remove-CsCertificate -Type WebServicesExternal -Force

```


```

Remove-CsCertificate -Type WebServicesExternal
```


## Detailed Description

Skype for Business Server 2015 uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server, and vice versa. In order to fully implement Skype for Business Server 2015, you will need to have the appropriate certificates assigned to the appropriate server roles.
  
    
    
The **Remove-CsCertificate** cmdlet provides a way for you to remove certificates currently in use by Skype for Business Server 2015. The **Remove-CsCertificate** cmdlet does not actually delete the certificate itself; instead, it marks the certificate as no longer being available for use by Skype for Business Server 2015, removes any certificate bindings, and revokes access permissions to the certificate (assuming no other service is using the certificate). Among other things, this means that the certificate will no longer appear when you run the **Get-CsCertificate** cmdlet.
  
    
    
To again use the certificate with Skype for Business Server 2015 you will need to reassign the certificate to Skype for Business Server 2015 by using the **Set-CsCertificate** cmdlet.
  
    
    
If you try to remove a certificate that is currently in use, the **Remove-CsCertificate** cmdlet will be ask if you are sure that you want to remove the certificate; the certificate cannot be removed until you respond to that prompt. To bypass the prompt, and silently delete a certificate even if it is currently in use, add the Force parameter to your command:
  
    
    



```

Remove-CsCertificate -Type WebServicesExternal -Force

```


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Type_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.CertType[]  <br/> |Type of certificate to be deleted. Certificate types include (but are not limited to):  <br/> AccessEdgeExternal  <br/> AudioVideoAuthentication  <br/> DataEdgeExternal  <br/> Default  <br/> External  <br/> Internal  <br/> PICWebService (Skype for Business Online only)  <br/> ProvisionService (Skype for Business Online only)  <br/> WebServicesExternal  <br/> WebServicesInternal  <br/> WsFedTokenTransfer  <br/> For example, this syntax deletes the Default certificate:  `-Type Default`.  <br/> You can delete multiple types in a single command by separating the certificate types with commas:  <br/>  `-Type Internal,External,Default` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Bypasses the confirmation prompt that typically occurs if you attempt to delete a certificate that is currently in use.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |When set to Global, removes the certificate from the global scope. When not specified, certificates are removed from the local computer.  <br/> |
| _Previous_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, removes the previously-assigned certificate instead of the currently-assigned certificate.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to record detailed information about the procedures carried out by the **Remove-CsCertificate** cmdlet. The parameter value should be the full path to the HTML file to be generated; for example: `-Report C:\\Logs\\Certificates.html`. If the specified file already exists it will automatically be overwritten with the new information.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

None. The Remove-CsCertificate cmdlet does not accept pipelined input.
  
    
    

## Return Types

None. Instead, the **Remove-CsCertificate** cmdlet deletes instances of the Microsoft.Rtc.Management.Deployment.CertificateReference object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsCertificate](get-cscertificate.md)
  
    
    
 [Import-CsCertificate](import-cscertificate.md)
  
    
    
 [Request-CsCertificate](request-cscertificate.md)
  
    
    
 [Set-CsCertificate](set-cscertificate.md)
