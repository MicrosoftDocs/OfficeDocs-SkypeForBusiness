---
title: 'Configuring a watcher node to use Trusted Server authentication'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring a watcher node to use Trusted Server authentication
ms:assetid: 42d879ac-aa90-4ed6-b5e2-1e208711672a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204852(v=OCS.15)
ms:contentKeyID: 48184017
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring a watcher node in Lync Server 2013 to use Trusted Server authentication

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

If your watcher node computer lies inside the perimeter network, using Trusted Server authentication can greatly reduce administration taxes to maintaining a single certificate rather than numerous user account passwords.

The first step in configuring Trusted Server authentication is to create a trusted application pool to host the watcher node computer. After the trusted application pool has been created, you must then configure synthetic transactions on that watcher node to run as a trusted application.

<div>


> [!NOTE]
> A trusted application is an application that is given trusted status to run as part of Lync Server 2013, but that is not a built-in part of the product. Trusted status means that the application will not be challenged for authentication each time it runs.



</div>

To create a trusted application pool, open the Lync Server 2013 Management Shell and run a command similar to this:

    New-CsTrustedApplicationPool -Identity atl-watcher-001.litwareinc.com -Registrar atl-cs-001.litwareinc.com -ThrottleAsServer $True -TreatAsAuthenticated $True -OutboundOnly $False -RequiresReplication $True -ComputerFqdn atl-watcher-001.litwareinc.com -Site Redmond

<div>


> [!NOTE]
> For details about the parameters used in the preceding command, type the following at the Lync Server Management Shell prompt:<BR>Get-Help New-CsTrustedApplicationPool -Full | more



</div>

After creating the trusted application pool, configure the watcher node computer to run synthetic transactions as a trusted application. This is done by using the **New-CsTrustedApplication** cmdlet and a command similar to this:

    New-CsTrustedApplication -ApplicationId STWatcherNode -TrustedApplicationPoolFqdn atl-watcher-001.litwareinc.com -Port 5061

When the preceding command completes and the trusted application has been created, run Enable-CsTopology to make sure that the changes take effect:

    Enable-CsTopology

After running Enable-CsTopology, we recommend that you restart the computer.

To verify that the new trusted application has been created, type the following at the Lync Server Management Shell prompt:

    Get-CsTrustedApplication -Identity "atl-watcher-001.litwareinc.com/urn:application:STWatcherNode"

<div>

## Configuring a Default Certificate on the Watcher Node

Each watcher node must have a Default certificate assigned by using the Lync Server Deployment Wizard.

**To assign a Default certificate**

1.  Click **Start**, click **All Programs**, click **Lync Server**, and then click **Lync Server Deployment Wizard**.

2.  In the Lync Server Deployment Wizard, click **Install or Update Lync Server System** and then click **Run** under the heading **Request, Install, or Assign Certificate**.
    
    <div>
    

    > [!NOTE]
    > If the <STRONG>Run</STRONG> button is disabled, you may need to first click <STRONG>Run</STRONG> under <STRONG>Install Local Configuration Store</STRONG>.

    
    </div>

3.  Do one of the following:
    
      - If you already have a certificate that can be used as the Default certificate, click **Default** in the Certificate wizard and then click **Assign**. Follow the steps in the Certificate Assignment wizard to assign that certificate.
    
      - If you need to request a certificate for use the Default certificate, click **Request** and then follow the steps in the Certificate Request wizard to request that certificate. If you use the default values for the Web Server certificate, you get a certificate that you can assign as the Default certificate.

</div>

<div>

## Installing and Configuring a Watcher Node

After you have restarted the watcher node computer and configured a certificate, you need to run the file Watchernode.msi. (You must run Watchernode.msi on a computer where both the Operations Manager agent files and the Lync Server 2013 core components are installed.)

**To install and configure a watcher node**

1.  Open the Lync Server Management Shell by clicking **Start**, clicking **All Programs**, clicking **Lync Server**, and then clicking **Lync Server Management Shell**.

2.  In the Lync Server Management Shell, type the following command and then press ENTER (specify the actual path to your copy of Watchernode.msi):
    
        C:\Tools\Watchernode.msi Authentication=TrustedServer
    
    <div>
    

    > [!NOTE]
    > You can also run Watchernode.msi from a command window. To open a command window, click <STRONG>Start</STRONG>, right-click <STRONG>Command Prompt</STRONG>, and then click <STRONG>Run as administrator</STRONG>. When the command window opens, type the same preceding command.

    
    </div>

Note that the name/value pair in the preceding command Authentication=TrustedServer is case-sensitive. You must type it exactly as shown. The following command fails because it does not use the correct letter casing:

C:\\Tools\\Watchernode.msi authentication=trustedserver

You can use TrustedServer mode only with computers that are located within the perimeter network. When a watcher node is running in TrustedServer mode, administrators do not have to maintain test user passwords on the computer.

</div>

</div>

<span> </span>

</div>

</div>

</div>

