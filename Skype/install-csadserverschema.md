---
title: Install-CsAdServerSchema
ms.prod: SKYPEFORBUSINESS
ms.assetid: 86e13601-7e80-4276-b176-77d9c6e7d55a
---


# Install-CsAdServerSchema
[]
Extends the Active Directory schema to allow for the installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Install-CsAdServerSchema [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Ldf <String>] [-Report <String>] [-SchemaMaster <Fqdn>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 determines the location of the .LDF file by reading information from the registry, then uses that file to update the Active Directory schema.
  
    
    

```

Install-CsAdServerSchema
```


### EXAMPLE 2

In Example 2, the Active Directory schema is updated with information taken from a schema update file located in the folder C:\\Schemas. This folder location is specified by using the Ldf parameter.
  
    
    

```
Install-CsAdServerSchema -Ldf "C:\\Schemas"
```


## Detailed Description

Although Skype for Business Server 2015 stores most of its configuration information in its own database, the software also relies on Active Directory Domain Services as a storage location; for example, user-related information is stored as part of the user's Active Directory account. In order to do this, Skype for Business Server 2015 must store these values in attributes that are not part of the typical Active Directory user account. In turn, that means you must "extend" your Active Directory schema: the schema must be modified to add custom attributes (and other items) required by Skype for Business Server 2015.
  
    
    
The easiest way to extend the Active Directory schema is to use the **Install-CsAdServerSchema** cmdlet. The **Install-CsAdServerSchema** cmdlet is typically run as part of the Skype for Business Server 2015 setup process but, if need be, administrators can run the cmdlet at any time. After the cmdlet finishes running, you can then use the **Get-CsAdServerSchema** cmdlet to verify that the schema has been updated and that Active Directory is ready for the next step in the installation process.
  
    
    
Note that, when the **Install-CsAdServerSchema** cmdlet runs, the cmdlet must have access to the schema master, the operations master role that manages Active Directory object and attribute definitions. If you are running the **Install-CsAdServerSchema** cmdlet on a computer other than the schema master, the computer that hosts the schema master must allow remote access to the registry. If it does not, then you must run the **Install-CsAdServerSchema** cmdlet on the schema master itself.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the **Install-CsAdServerSchema** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller in your domain. This parameter is not required if you are running the **Install-CsAdServerSchema** cmdlet on a computer with an account in your domain. <br/> |
| _Ldf_ <br/> |Optional  <br/> |System.String  <br/> |Path to the folder containing the .LDF file to be imported; the .LDF (LDAP Data Interchange Format) file contains the required updates for the Active Directory schema. If this parameter is not included, the **Install-CsAdServerSchema** cmdlet will look for the file in the Skype for Business Server 2015 installation path recorded in the registry. The installation path will typically be C:\\Program Files\\Skype for Business Server 2015\\Deployment\\Setup. <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\\Logs\\ServerSchema.html"  <br/> |
| _SchemaMaster_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the Active Directory schema master for your domain. This parameter is not required if you are running the Install-CsAdServerSchema cmdlet on a computer with an account in your domain.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

None. The **Install-CsAdServerSchema** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **Install-CsAdServerSchema** cmdlet does not return any values or objects.
  
    
    

## See also


#### 


  
    
    
 [Get-CsAdServerSchema](get-csadserverschema.md)
