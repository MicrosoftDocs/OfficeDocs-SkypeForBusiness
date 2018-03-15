---
title: "Create a Kerberos authentication account in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 63f0cef6-562a-4209-ae25-71f8dc7c7295
description: "To successfully complete this procedure, you should be logged on to the server or domain minimally as a member of the Domain Admins group."
---

# Create a Kerberos authentication account in Lync Server 2013
[]
To successfully complete this procedure, you should be logged on to the server or domain minimally as a member of the Domain Admins group. 
  
You can create Kerberos authentication accounts for each site or you can create a single Kerberos authentication account and use it for all sites. You use Windows PowerShell cmdlets to create and manage the accounts, including identifying the accounts assigned to each site. Topology Builder and the Lync Server 2013 Control Panel do not display Kerberos authentication accounts. Use the following procedure to create one or more user accounts to be used for Kerberos authentication.
  
### To create a Kerberos account

1. As a member of the Domain Admins group, log on to a computer in the domain running Lync Server 2013 or on to a computer where the administrative tools are installed.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. From the command line, run the following command:
    
  ```
  New-CsKerberosAccount -UserAccount "Domain\UserAccount" -ContainerDN "CN=Users,DC=DomainName,DC=DomainExtension"
  ```

    For example:
    
  ```
  New-CsKerberosAccount -UserAccount "Contoso\KerbAuth" -ContainerDN "CN=Users,DC=contoso,DC=com"
  ```

4. Confirm that the Computer object was created by opening Active Directory User and Computers, expand the **Users** container, and then confirm that the Computer object for the user account is in the container. 
    

