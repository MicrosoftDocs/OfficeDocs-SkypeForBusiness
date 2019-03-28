---
title: 'Lync Server 2013: Installing the Lync Room System Administrative Web Portal'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Installing the Lync Room System Administrative Web Portal
ms:assetid: dd19e368-c338-4e21-a40d-6439d46a9748
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn436326(v=OCS.15)
ms:contentKeyID: 56737622
ms.date: 04/09/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Installing the Lync Room System Administrative Web Portal in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-04-09_

You can download the Microsoft Lync Room System Administrative Web Portal from the Microsoft Download Center at [http://go.microsoft.com/fwlink/p/?LinkId=324044](http://go.microsoft.com/fwlink/p/?linkid=324044).

To install the Lync Room System Administrative Web Portal, use the following steps.

1.  Configure the Trusted Application Port by running the following cmdlet in Lync Server Management Shell:
    
        Set-CsWebServer -Identity POOLFQDN -MeetingRoomAdminPortalInternalListeningPort 4456 -MeetingRoomAdminPortalExternalListeningPort 4457

2.  To install the Meeting Room Portal, download **LyncRoomAdminPortal.exe** and then run it as an administrator.

3.  Open the Web.config file from the following location:
    
    %Program Files%\\Microsoft Lync Server 2013\\Web Components\\Meeting Room Portal\\Int\\Handler\\

4.  In the Web.Config file, change the PortalUserName to the username created in Step 2 under the section “Configuring Prerequisites for Lync Room System Admin Portal” (the recommended name in the step is LRSApp):
    
        <add key="PortalUserName" value="sip:LRSApp@domain.com" />

5.  Because the LRS Admin Portal is a trusted application, you do not need to provide the password in the portal configuration. If this user is using a different registrar than local registrar, you need to specify the registrar for it by adding the following line in the Web.Config file:
    
        <add key="PortalUserRegistrarFQDN" value="pool-xxxx.domain.com" />

6.  If the port used is other than 5061, add the following line in the Web.Config file:
    
        <add key="PortalUserRegistrarPort" value="5061" />

<div>

## Verifying Installation of the Lync Room System Administrative Web Portal

To verify installation of the Lync Room System Administrative Web Portal, do the following:


1.  On a Front End server, browse to the following URL:
    
    https://\<fe-server\>/lrs
    
    You should not see any errors, as shown in the following image:
    
    ![Lync Room System Admin Portal Sign In screen](images/Dn436326.050bcf70-2f3b-46b2-9b96-ebd12679b713(OCS.15).png "Lync Room System Admin Portal Sign In screen")

2.  If you do not see any errors, try accessing the following URL from any other computer in the topology:
    
    https://\<fe-server\>/lrs
    
    To access the page, you will need to add the DNS records as described in “Required DNS Records for Automatic Client Sign-In” at [http://go.microsoft.com/fwlink/p/?LinkId=318056](http://go.microsoft.com/fwlink/p/?linkid=318056).

</div>

</div>

<span> </span>

</div>

</div>

</div>

