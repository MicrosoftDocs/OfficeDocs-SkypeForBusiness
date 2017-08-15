---
title: Manage Skype for Business Online organizations using the Skype for Business Online Connector
ms.prod: SKYPEFORBUSINESS
ms.assetid: c71f0d4d-5b6b-40ac-bc4a-6b97c05a121a
---


# Manage Skype for Business Online organizations using the Skype for Business Online Connector

You can find information about your Skype for Business Online tenant by using the **Get-CsTenant** and **Get-CsTenantLicensingConfiguration** cmdlets.
  
    
    


## Manage Skype for Business Online tenants

To return information about your Skype for Business Online tenant, call the  [Get-CsTenant](https://go.microsoft.com/fwlink/p/?linkid=849599) cmdlet without any additional parameters.
  
    
    

```

Get-CsTenant
```


  
    
    
To return just the tenant name and ID, use this command.
  
    
    



```
Get-CsTenant | Select-Object Name, TenantID
```

The value of the  _TenantID_ parameter is required when running cmdlets such as [Set-CsTenantPublicProvider](https://go.microsoft.com/fwlink/p/?linkid=849602) and [Set-CsTenantFederationConfiguration](https://go.microsoft.com/fwlink/p/?linkid=849602).
  
    
    
To find information about whether licensing information for the specified tenant is available in the Skype for Business Online admin center, use the  [Get-CsTenantLicensingConfiguration](https://go.microsoft.com/fwlink/p/?linkid=849606) cmdlet.
  
    
    

