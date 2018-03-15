---
title: "Validate addresses in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aae557c9-e6f5-4d23-8af1-1d4cd7968c54
description: "Before publishing the location database, you must validate new locations against the Master Street Address Guide (MSAG) that is maintained by your SIP trunk or public switched telephone network (PSTN) E9-1-1 service provider."
---

# Validate addresses in Lync Server 2013
[]
Before publishing the location database, you must validate new locations against the Master Street Address Guide (MSAG) that is maintained by your SIP trunk or public switched telephone network (PSTN) E9-1-1 service provider. 
  
For details about SIP trunk E9-1-1 service providers, see [Choosing an E9-1-1 service provider for Lync Server 2013](choosing-an-e9-1-1-service-provider.md).
  
For details about validating addresses, see the Lync Server Management Shell documentation for the following cmdlets:
  
- **Get-CsLisServiceProvider**
    
- **Set-CsLisServiceProvider**
    
- **Remove-CsLisServiceProvider**
    
- **Get-CsLisCivicAddress**
    
- **Test-CsLisCivicAddress**
    
### To validate addresses located in the location database

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the following cmdlets to configure the emergency service provider connection.
    
  ```
  $pwd = Read-Host -AsSecureString <password>
  Set-CsLisServiceProvider -ServiceProviderName Provider1 -ValidationServiceUrl <URL provided by provider> -CertFileName <location of certificate provided by provider> -Password $pwd
  
  ```

3. Run the following cmdlet to validate the addresses in the location database.
    
  ```
  Get-CsLisCivicAddress | Test-CsLisCivicAddress -UpdateValidationStatus
  ```

    You can also use the **Test-CsLisCivicAddress** cmdlet to validate individual addresses. 
    

