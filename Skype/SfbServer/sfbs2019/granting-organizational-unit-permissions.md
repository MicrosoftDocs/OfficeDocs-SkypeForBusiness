---
title: "Granting organizational unit permissions in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 95ee5ffa-39b1-4d80-87a2-27bb364f7396
description: "You can use the Grant-CsOuPermission cmdlet to grant permissions to objects in specified organizational units (OUs) so that members of the RTC universal groups created by forest preparation can access them without being members of the Domain Admins group. The permissions added to the specified OU are the same permissions that the Enable-CsAdDomain cmdlet adds to the computers and users containers during domain preparation."
---

# Granting organizational unit permissions in Lync Server 2013
[]
You can use the **Grant-CsOuPermission** cmdlet to grant permissions to objects in specified organizational units (OUs) so that members of the RTC universal groups created by forest preparation can access them without being members of the Domain Admins group. The permissions added to the specified OU are the same permissions that the **Enable-CsAdDomain** cmdlet adds to the computers and users containers during domain preparation. 
  
Use the **Test-CsOuPermission** cmdlet to verify the permissions you set up by using the **Grant-CsOuPermission** cmdlet. 
  
You can use the **Revoke-CsOuPermission** cmdlet to remove permissions that you granted by using the **Grant-CsOuPermission** cmdlet. 
  
### To grant OU permissions

1. Log on to a computer running Lync Server 2013 in the domain where you want to grant OU permissions. Use an account that is a member of the Domain Admins group or the Enterprise Admins group if the OU is in a different child domain.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run:
    
  ```
  Grant-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU> [-Domain <Domain FQDN>]
  ```

    If you do not specify the Domain parameter, the default value is the local domain.
    
### To verify OU permissions

1. Log on to a computer running Lync Server 2013 in the domain where you want to verify OU permissions that you granted by using the **Grant-CsOuPermission** cmdlet. Use an account that is a member of the Domain Admins group or the Enterprise Admins group if the OU is in a different child domain. 
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run:
    
  ```
  Test-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU> [-Domain <Domain FQDN>]
  ```

    If you do not specify the Domain parameter, the default value is the local domain.
    
### To revoke OU permissions

1. Log on to a computer running Lync Server 2013 in the domain where you want to revoke OU permissions that were granted by the **Grant-CsOuPermission** cmdlet. Use an account that is a member of the Domain Admins group or the Enterprise Admins group if the OU is in a different child domain. 
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run:
    
  ```
  Revoke-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU> [-Domain <Domain FQDN>]
  ```

    If you do not specify the Domain parameter, the default value is the local domain.
    

