---
title: 'Lync Server 2013: Deploy the SEFAUtil tool'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deploy the SEFAUtil tool
ms:assetid: fb556e50-88dd-4404-a3d5-be36f5ba41e6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945659(v=OCS.15)
ms:contentKeyID: 51541534
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploy the SEFAUtil tool in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-30_

To deploy and manage Group Call Pickup, you need to use the SEFAUtil resource kit tool. The tool is part of the Lync Server 2013 resource kit tools. Before you can install SEFAUtil, you must have a trusted application pool in your topology, specify SEFAUtil as a trusted application, and enable the topology.

<div>


> [!IMPORTANT]  
> Microsoft Unified Communications Managed API (UCMA) 3.0 Core SDK must be installed on any computer where you plan to run the SEFAUtil tool.



</div>

You can run the SEFAUtil in any Front End pool in your deployment.

<div>


> [!NOTE]  
> For more details about running SEFAUtil, see the Technet blog article, "How to get SEFAutil running?" at <A href="http://go.microsoft.com/fwlink/?linkid=278940">http://go.microsoft.com/fwlink/?LinkId=278940</A>.



</div>

<div>

## To deploy SEFAUtil

1.  Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  The SEFAUtil tool can be run only on a computer that is part of a trusted application pool. If needed, define a trusted application pool for the Front End pool where you plan to run SEFAUtil. At the command line, run:
    
        New-CsTrustedApplicationPool -id <Pool FQDN> -Registrar <Pool Registrar FQDN> -site Site:<Pool Site>

4.  Define the SEFAUtil tool as a trusted application. At the command line, run:
    
        New-CsTrustedApplication -ApplicationId sefautil -TrustedApplicationPoolFqdn <Pool FQDN>  -Port 7489
    
    <div>
    

    > [!NOTE]  
    > You can use a different port if needed.

    
    </div>

5.  Enable the topology with your changes. At the command line, run:
    
        Enable-CsTopology

6.  Install the Lync Server 2013 resource kit tools on a Front End Server that is in the trusted application pool that you created in step 3.

7.  Verify that the SEFAUtil tool is running correctly, as follows:
    
    1.  Run the tool from the Windows command prompt with administrator privileges to display the call forwarding settings of a user in your deployment.
        
        <div>
        

        > [!NOTE]  
        > The tool is located at \Program Files\Microsoft Lync Server 2013\Reskit.

        
        </div>
    
    2.  Display the call forwarding settings of a user. At the command line, run:
        
            SEFAUtil.exe <user SIP address> /server:<Lync Server/Pool FQDN>
        
        The call forwarding settings for the user will be displayed.

</div>

</div>

<span> </span>

</div>

</div>

</div>

