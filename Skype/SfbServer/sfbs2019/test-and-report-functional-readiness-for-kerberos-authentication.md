---
title: "Test and report functional readiness for Kerberos authentication in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d52c39e5-747d-4f29-88aa-30fd6f26b99c
description: "To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group."
---

# Test and report functional readiness for Kerberos authentication in Lync Server 2013
[]
To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group.
  
You can use the **Test-CsKerberosAccountAssignment** Windows PowerShell cmdlet to test and report the functional readiness of a site assignment for Kerberos authentication. This command queries the site specified in the required Identity parameter. The optional Report parameter causes the cmdlet to write an HTML report to C:\Logs on the computer on which the command is run. The optional Verbose parameter reports activity information to the screen. 
  
### To test and report functional readiness for Kerberos authentication for a site

1. As a member of the RTCUniversalServerAdmins group, log on to a computer in the domain running Lync Server 2013 or on to the computer where the administrative tools are installed.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. From the command line, run the following command:
    
  ```
  Test-CsKerberosAccountAssignment -Identity "site:SiteName" -Report "c:\logs\FileName.htm" -Verbose
  ```

    For example:
    
  ```
  Test-CsKerberosAccountAssignment -Identity "site:Redmond" -Report "c:\logs\KerberosReport.htm" -Verbose
  ```


