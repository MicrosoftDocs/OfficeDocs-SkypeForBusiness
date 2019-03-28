---
title: 'Lync Server 2013: Report Kerberos account assignments'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Report Kerberos account assignments
ms:assetid: 523231f6-81b3-454b-996d-663d9bd5cf83
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398343(v=OCS.15)
ms:contentKeyID: 48184151
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Report Kerberos account assignments in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-01-16_

To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group.

You can use the **Get-CsKerberosAccountAssignment** cmdlet to query information about the Kerberos authentication account assignments and report information about the current assignments in your deployment.

<div>

## To query Kerberos authentication account assignments for a site

1.  As a member of the RTCUniversalServerAdmins group, log on to a computer in the domain running Lync Server 2013 or on to a computer where the administrative tools are installed.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  From the command line, run one of the following commands:
    
      - To query all Kerberos authentication account assignments in your organization and return assignment information about each of them, run the cmdlet without any parameters:
        
            Get-CsKerberosAccountAssignment
    
      - To query all Kerberos authentication account assignments in your deployment and return site assignment information about each of them, run the cmdlet with the Identity parameter:
        
            Get-CsKerberosAccountAssignment -Identity "site:SiteName"
        
        For example:
        
            Get-CsKerberosAccountAssignment -Identity "site:Redmond"
    
      - To query all Kerberos authentication account assignments in a single site and return assignment information about each of them, run the cmdlet with the Filter parameter:
        
            Get-CsKerberosAccountAssignment -Filter "SiteName"
        
        For example:
        
            Get-CsKerberosAccountAssignment -Filter "*Redmond"
        
        <div>
        

        > [!NOTE]  
        > Specifying *SiteName for the Filter parameter returns information about all sites that contain the specified site name anywhere in the site identifier (for example, all sites that contain the string Redmond in the site identifier).

        
        </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

