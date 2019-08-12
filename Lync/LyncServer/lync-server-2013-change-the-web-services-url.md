---
title: 'Lync Server 2013: Change the Web Services URL'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Change the Web Services URL
ms:assetid: 4cee37c0-3b99-4207-997f-bf4229d760c0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520992(v=OCS.15)
ms:contentKeyID: 48184063
ms.date: 11/16/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Change the Web Services URL in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-11-16_

When you set up your Front End pools and Standard Edition servers, you have the option to configure an external Web farm fully qualified domain name (FQDN) and associated ports. If you did not configure this URL when you ran the Lync Server Deployment Wizard, you need to manually configure these settings. An administrator typically does not need to modify these settings, as these are the recommended and default ports.

<div>


> [!NOTE]  
> The following screen shot was taken while configuring a Standard Edition server, so the Override FQDN option is disabled. That option is enabled when configuring an Enterprise Edition server in a Front End pool.



</div>

![Edit Web Services Pool Settings](images/Gg520992.fbdf5cc9-479a-463f-bb1d-53575ecdfc9d(OCS.15).jpg "Edit Web Services Pool Settings")

<div>

## To configure web services

1.  Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.

2.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

3.  In Topology Builder, in the console tree under **Standard Edition Front End Servers**, **Enterprise Edition Front End pools**, and **Directory pools**, select the pool name. Right-click the name, click **Edit Properties**, and then click **Web Services**.

4.  Add or edit the **External Web Services FQDN**, and then click **OK**.
    
    <div>
    

    > [!WARNING]  
    > If you have more than one Front End pool or Front End Server the external Web services FQDN must be unique. For example, if you define the external Web services FQDN of a Front End Server as <STRONG>pool01.contoso.com</STRONG>, you cannot use <STRONG>pool01.contoso.com</STRONG> for another Front End pool or Front End Server. If you are also deploying Directors, the external Web services FQDN defined for any Director or Director pool must be unique from any other Director or Director pool as well as any Front End pool or Front End Server.

    
    </div>

5.  Verify the listening and published ports are configured correctly for your environment.

6.  Repeat these steps for all Standard Edition servers, Front End Pools, and Director pools in your environment.

7.  In the console tree, click **Lync Server 2013**, and then, in the **Actions** pane, click **Publish Topology**.

There are a few requirements you should be aware of when configuring the Listening and Publishing ports:

  - The listening ports shown are the ports that are configured for Internet Information Server (IIS) on each Front End Server.

  - The internal and external listening ports must be different for IIS. For the external listening ports, these are typically the same because one represents the hardware load balancer for internal web traffic and one represents the reverse proxy server for external web traffic.

  - You can override the Internal web services on a Front End pool, Director or a Director pool and define your own FQDN.
    
    <div>
    

    > [!WARNING]  
    > If you decide to override the Internal web services with a self-defined FQDN, each FQDN must be unique from any other Front End pool, Director or a Director pool.

    
    </div>

  - The published ports must be configured on the reverse proxy or hardware load balancer as listening ports.

  - For an Front End pool (not shown in the example), the internal SIP pool FQDN must be different from the internal web services FQDN, because web traffic comes through the hardware load balancer and the internal SIP pool traffic travels comes through the DNS load balancer. This requirement must be met.

  - A Lync Server Standard Edition deployment does not need or allow an internal web services FQDN to be overridden because this server cannot be load balanced.

  - If you have a hardware load balancer in your environment that you use for both internal SIP and web traffic, the Topology Builder cannot make the distinction.
    
    Web service FQDNs should be easily-differentiated from one another; that helps to ensure that URL redirection points clients towards the appropriate server. For example, if you have two FQDNs you might consider naming one meeting.contoso.com and the other conferencing.contoso.com. You could potentially run into redirection issues if you have FQDNs with more similar names, such as meet1.contoso.com and meet2.contoso.com.

The external web services works in conjunction with a reverse proxy in the perimeter network. It provides clients external access to by using these web services. The FQDNs configured here are sent to clients when they log on, and are used to make an HTTPS connection back to the reverse proxy when connecting remotely. The reverse-proxy server forwards the external web service FQDN to an internal hardware load balancer, or directly to the pool. The reverse proxy must be able to resolve the external web services FQDN to the IP address of the internal Web server. The external web services FDQN must be resolvable in the public Internet.

If your internal server is a Standard Edition server, the internal FQDN is the Standard Edition server FQDN. If your internal server is a Front End pool, the FQDN is a hardware load balancer virtual IP (VIP) that load balances the internal web farm servers. A hardware load balancer is required in a Front End pool with more than one Enterprise Edition server. A load balancer is not required for a Standard Edition server or a single Enterprise Edition Front End Server.

</div>

</div>

<span> </span>

</div>

</div>

</div>

