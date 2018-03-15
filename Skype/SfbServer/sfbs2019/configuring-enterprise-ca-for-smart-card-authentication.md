---
title: "Configuring Enterprise CA for smart card authentication in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c24e0891-e108-4cb6-9902-c6a4c8e68455
description: "The following section describes how to configure an Enterprise Root Certification Authority (CA) to support smart card authentication. For information on how to install an Enterprise Root CA, see Install an Enterprise Root Certification Authority at https://go.microsoft.com/fwlink/p/?LinkID=313364."
---

# Configuring Enterprise CA for smart card authentication in Lync Server 2013
[]
The following section describes how to configure an Enterprise Root Certification Authority (CA) to support smart card authentication. For information on how to install an Enterprise Root CA, see Install an Enterprise Root Certification Authority at [https://go.microsoft.com/fwlink/p/?LinkID=313364](https://go.microsoft.com/fwlink/p/?LinkID=313364).
  
## Configuring an Enterprise Root Certificate Authority to Support Smart Card Authentication

The following steps describe how to configure an Enterprise Root CA to support Smart Card Authentication:
  
1. Log in to the Enterprise CA computer using a Domain Admin account.
    
2. Launch System Manager, and verify that the Certificate Authority Web Enrollment role is installed.
    
3. From the **Administrative Tools** menu, open the **Certification Authority** management console. 
    
4. In the Navigation pane, expand **Certification Authority**.
    
5. Right click on **Certificate Templates**, select **New**, then select **Certificate Template to Issue**.
    
6. Select **Enrollment Agent**, **Smartcard User**, and **Smartcard Logon**.
    
7. Click **OK**.
    
8. Right click on **Certificate Templates**.
    
9. Select **Manage**.
    
10. Open the properties of the Smartcard User template.
    
11. Click on the **Security** tab. 
    
12. Change the permissions as follows:
    
  - Add individual user AD accounts with Read/Enroll (Allow) permissions, or
    
  - Add a security group containing smart card users with Read/Enroll (Allow) permissions, or
    
  - Add the Domain Users group with Read/Enroll (Allow) permissions
    

