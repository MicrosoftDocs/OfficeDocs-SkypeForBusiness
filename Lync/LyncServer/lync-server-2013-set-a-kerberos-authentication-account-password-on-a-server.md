---
title: 'Lync Server 2013: Set a Kerberos authentication account password on a server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Set a Kerberos authentication account password on a server
ms:assetid: 902d3292-678d-4512-9248-586053cb638b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398734(v=OCS.15)
ms:contentKeyID: 48184787
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set a Kerberos authentication account password on a server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-01-16_

To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group.

You must set up a password on the Kerberos account for each site that has Front End Servers, Standard Edition servers, and Directors. You can set up the password by running the **Set-CsKerberosAccountPassword** Windows PowerShell cmdlet on one server in the site (for example, one Front End Server). For each site, you must run the **Set-CsKerberosAccountPassword** cmdlet. The cmdlet configures Internet Information Services (IIS) for the Web Services service, and then sets the password on the computer account in Active Directory Domain Services. An alternate method, based on which parameter is used with the cmdlet, configures IIS on one server while using another server that has been configured as the source of the Kerberos account password.

When you use the **Set-CsKerberosAccountPassword** cmdlet to set a password, Kerberos sets the password to a randomly generated string. This cmdlet contacts all IIS instances in all Lync Server 2013 central sites to which this account is assigned.

<div>

## To set a password for a Kerberos authentication account

1.  Log on to any domain computer with Lync Server Management Shell installed as a member of the RTCUniversalServerAdmins group.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  From the command line, run the following two commands:
    
        Set-CsKerberosAccountPassword -UserAccount "Domain\UserAccount"
    
    For example:
    
        Set-CsKerberosAccountPassword -UserAccount "contoso\KerbAuth"
    
    <div>
    

    > [!NOTE]  
    > You must specify the UserAccount parameter by using the Domain\User format. The User@Domain.extension format is not supported for referencing the computer objects created for Kerberos authentication purposes.

    
    </div>
    
    <div>
    

    > [!IMPORTANT]  
    > After making any changes to Kerberos authentication, such as adding an account or removing an account, you must run <STRONG>Enable-CsTopology</STRONG> from the Lync Server Management Shell command prompt.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

