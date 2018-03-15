---
title: "Report Kerberos account assignments in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 523231f6-81b3-454b-996d-663d9bd5cf83
description: "To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group."
---

# Report Kerberos account assignments in Lync Server 2013
[]
To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group.
  
You can use the **Get-CsKerberosAccountAssignment** cmdlet to query information about the Kerberos authentication account assignments and report information about the current assignments in your deployment. 
  
### To query Kerberos authentication account assignments for a site

1. As a member of the RTCUniversalServerAdmins group, log on to a computer in the domain running Lync Server 2013 or on to a computer where the administrative tools are installed.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. From the command line, run one of the following commands:
    
  - To query all Kerberos authentication account assignments in your organization and return assignment information about each of them, run the cmdlet without any parameters:
    
  ```
  Get-CsKerberosAccountAssignment
  ```

  - To query all Kerberos authentication account assignments in your deployment and return site assignment information about each of them, run the cmdlet with the Identity parameter:
    
  ```
  Get-CsKerberosAccountAssignment -Identity "site:SiteName"
  ```

    For example:
    
  ```
  Get-CsKerberosAccountAssignment -Identity "site:Redmond"
  ```

  - To query all Kerberos authentication account assignments in a single site and return assignment information about each of them, run the cmdlet with the Filter parameter:
    
  ```
  Get-CsKerberosAccountAssignment -Filter "SiteName"
  ```

    For example:
    
  ```
  Get-CsKerberosAccountAssignment -Filter "*Redmond"
  ```

    > [!NOTE]
    > Specifying \*SiteName for the Filter parameter returns information about all sites that contain the specified site name anywhere in the site identifier (for example, all sites that contain the string Redmond in the site identifier). 
  

