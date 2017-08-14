---
title: New-CsWebTrustedCACertificate
ms.prod: SKYPEFORBUSINESS
ms.assetid: a0a94971-372a-401a-8ae0-9ff649a9c301
---


# New-CsWebTrustedCACertificate
[]
Creates a new certificate ID object based on an existing certification authority (CA) certificate. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsWebTrustedCACertificate -CAStore <TrustedRootCA | IntermediateCA | ThirdPartyRootCA> -Thumbprint <String>

```


## Examples


  
    
    

### EXAMPLE 1

The commands shown in Example 1 create a new trusted CA certificate and then add that certificate to the TrustedCACerts property of the Web Services configuration settings for the Redmond site. To carry out this task, the first command in the example uses the **New-CsWebTrustedCACertificate** cmdlet to create a new trusted CA certificate; that certificate can be found in the Trusted Root certificate store and has the Thumbprint D543DFF74FEEA425162FD25F342786F1AB453BB3. The resulting certificate object is stored in a variable named $x.
  
    
    
After the certificate object has been created, the second command in the example adds that certificate to the TrustedCACerts property. To do this, the command uses the **Set-CsWebServiceConfiguration** cmdlet and the TrustedCACerts parameter. The parameter value ${Add=$x} tells the cmdlet to add the certificate stored in the variable $x to the collection of trusted CA certificates.
  
    
    



```

$x = New-CsWebTrustedCACertificate -Thumbprint "D543DFF74FEEA425162FD25F342786F1AB453BB3" -CAStore TrustedRootCA

Set-CsWebServiceConfiguration -Identity site:Redmond -TrustedCACerts @{Add=$x}
```


## Detailed Description

Web Services configuration settings are used to help manage Skype for Business Server 2015 Web servers and Web Services. Among the property values that can be managed using these settings is the TrustedCACerts property, which represents a collection of certification authorities trusted by Skype for Business Phone Edition. Certificates obtained from trusted CAs allow these clients to enhance the security of connections with servers running Skype for Business Server 2015. To add a new CA to the collection of trusted certification authorities, you must add the certificate chain for that CA in the local computer's certificate store. After you have verified that the certificate chain has been installed, you can then use the **New-CsWebTrustedCACertificate** cmdlet to create a certificate ID object that can be added to a collection of Web Services configuration settings.
  
    
    
Note that the certification authority that signs the default server certificate used when installing Skype for Business Server 2015 is automatically trusted and does not need to be added to the TrustedCACerts property of a collection of Web Services configuration settings. TrustedCACerts should only contain the identities of CAs that need to be trusted in addition to the CA that issued the default certificate. In most cases, the CA that issued the default certificate will be the only certification authority that needs to be trusted.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CAStore_ <br/> |Required  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Web.CAStore  <br/> |Indicates the name of the certificate store (on the local computer) where the certificate is stored. Valid values are:  <br/> TrustedRootCA  <br/> IntermediateCA  <br/> ThirdPartyRootCA  <br/> |
| _Thumbprint_ <br/> |Required  <br/> |System.String  <br/> |Thumbprint of the certificate which should be trusted by Lync Phone Edition. You can retrieve certificate issuer and thumbprint values by running this command:  <br/>  `Get-CsCertificate | Select-Object Issuer, Thumbprint` <br/> |
   

## Input Types

None. The **New-CsWebTrustedCACertificate** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **New-CsWebTrustedCACertificate** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Web.CACertID object.
  
    
    

## See also


#### 


  
    
    
 [New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)
  
    
    
 [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)
