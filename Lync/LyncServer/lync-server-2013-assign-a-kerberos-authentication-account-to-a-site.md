---
title: 'Lync Server 2013: Assign a Kerberos authentication account to a site'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Assign a Kerberos authentication account to a site
ms:assetid: 3d9c587c-c8b8-4f81-8ed9-1458a31fc292
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425901(v=OCS.15)
ms:contentKeyID: 48183929
ms.date: 04/18/2017
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Assign a Kerberos authentication account to a site in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2017-04-18_

To successfully complete this procedure you should be logged on as a user who is a member of the RTCUniversalServerAdmins group.

After creating the Kerberos account, you must assign it to a site. This is a Lync Server 2013 site, not an Active Directory site. You can create multiple Kerberos authentication accounts per deployment, but you can assign only one account to a site. Use the following procedure to assign a previously created Kerberos authentication account to a site. For details about creating the Kerberos account, see [Create a Kerberos authentication account in Lync Server 2013](lync-server-2013-create-a-kerberos-authentication-account.md).

<div>

## To assign a Kerberos authentication account to a site

1.  As a member of the RTCUniversalServerAdmins group, log on to a computer in the domain running Lync Server 2013 or on to a computer where the administrative tools are installed.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  From the command line, run the following two commands:
    
       ```
        New-CsKerberosAccountAssignment -UserAccount "Domain\UserAccount"
                  -Identity "site:SiteName"
       ```          
    
       ```
        Enable-CsTopology
       ```
    
    For example:
    
       ```
        New-CsKerberosAccountAssignment -UserAccount "contoso\kerbauth"
                  -Identity "site:redmond"
       ```
    
       ```
        Enable-CsTopology
       ```
    
    <div class="">
    

    > [!NOTE]  
    > You must specify the UserAccount parameter by using the Domain\User format. The User@Domain.extension format is not supported for referring to the computer objects created for Kerberos authentication purposes.

    
    </div>

4.  **OPTIONAL**: You may have configured an override FQDN (fully qualified domain name) for your WebServices, as per [Change the Web Services URL in Lync Server 2013](lync-server-2013-change-the-web-services-url.md). If that's the case, you'll need to add a SPN for this FQDN as well. For example, if the FQDN was webservices.contoso.local, you would run:
    
        setspn -S http/webservices.contoso.local kerbauth

5.     
    <div class="">
    

    > [!IMPORTANT]  
    > After making any changes to Kerberos authentication, such as adding an account or removing an account, you must run <STRONG>Enable-CsTopology</STRONG> from the Lync Server Management Shell command prompt.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

