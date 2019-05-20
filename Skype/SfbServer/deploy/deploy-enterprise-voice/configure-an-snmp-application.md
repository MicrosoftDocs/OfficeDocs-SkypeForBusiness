---
title: "Configure an SNMP application in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: c4b4a736-3b2e-45b9-a965-19d22161ad57
description: "Configure an SNMP application to work with E9-1-1 in Skype for Business Server Enterprise Voice."
---

# Configure an SNMP application in Skype for Business Server
 
Configure an SNMP application to work with E9-1-1 in Skype for Business Server Enterprise Voice. 
  
Skype for Business Server includes a standard web service interface that you can use to connect the Location Information service to Simple Network Management Protocol (SNMP) applications that match MAC addresses with port and switch information. 
  
If an SNMP application is installed and the Location Information service fails to find a match in the location database, the Location Information service automatically queries the application by using the MAC address provided by the client. The Location Information service then uses the port and switch information returned by the SNMP application to query the location database again.
  
> [!NOTE]
> MAC addresses are not available on computers running Windows 8. 
  
### To configure the SNMP application URL

1.  Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. Run the following cmdlet to configure the URL for the SNMP application. 
    
   ```
   Set-CsWebServiceConfiguration -MACResolverUrl "<SNMP application url>" 
   ```

## See also

[Set-CsWebServiceConfiguration](https://docs.microsoft.com/powershell/module/skype/set-cswebserviceconfiguration?view=skype-ps)

