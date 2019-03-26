---
title: 'Lync Server 2013: Running domain preparation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Running domain preparation
ms:assetid: 95dab800-1f2c-4506-b36c-99986643b149
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398761(v=OCS.15)
ms:contentKeyID: 48184847
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Running domain preparation for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-04-16_

You can use Setup or Lync Server Management Shell cmdlets to prepare domains. The cmdlet that prepares a domain is **Enable-CsAdDomain**.

Domain preparation is the final step in preparing Active Directory Domain Services for Lync Server 2013.

<div>

## To use Setup to prepare domains

1.  Log on to any server in the domain as a member of the Domain Admins group.

2.  From the Lync Server 2013 installation folder or media, run Setup.exe to start the Lync Server Deployment Wizard.

3.  Click **Prepare Active Directory**, and then wait for the deployment state to be determined.

4.  At **Step 5: Prepare Current Domain**, click **Run**.

5.  On the **Prepare Domain** page, click **Next**.

6.  On the **Executing Commands** page, look for **Task status: Completed**, and then click **View Log**.

7.  Under the **Action** column, expand **Domain Prep**, look for a **\<Success\>** Execution Result at the end of each task to verify that domain preparation completed successfully, close the log, and then click **Finish**.

8.  Wait for Active Directory replication to complete or force replication to all the domain controllers listed in the Active Directory Sites and Services snap-in for the forest root domain controller.

</div>

<div>

## To use cmdlets to prepare the domain

1.  Log on to any server in the domain as a member of the Domain Admins group.

2.  Install Lync Server Core components as follows:
    
    1.  From the Lync Server 2013 installation folder or media, run Setup.exe to start the Lync Server Deployment Wizard.
    
    2.  If you are prompted to install the Microsoft Visual C++ Redistributable, click **Yes**.
    
    3.  The Lync Server 2013 Setup dialog box prompts you for a location to install the Lync Server files. Choose the default location or **Browse** to a location of your choice, and then click **Install**.
    
    4.  On the License Agreement page, check **I accept the terms in the license agreement**, and then click **OK**. The installer installs the Lync Server 2013 Core Components.

3.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

4.  Run:
    
        Enable-CsAdDomain [-Domain <DomainFQDN>] 
    
    For example:
    
        Enable-CsAdDomain -Domain domain1.contoso.net 
    
    If you do not specify the Domain parameter, the default is the local domain.

5.  Verify that domain preparation was successful. Run:
    
        Get-CsAdDomain [-Domain <Domain FQDN>] [-DomainController <Domain controller FQDN>] [-GlobalCatalog <Global catalog server FQDN>] [-GlobalSettingsDomainController <Domain controller FQDN where global settings are stored>] 
    
    For example:
    
        Get-CsAdDomain -Domain domain1.contoso.net -GlobalSettingsDomainController dc01.domain1.contoso.com
    
    <div>
    

    > [!NOTE]  
    > The parameter GlobalSettingsDomainController allows you to indicate where global settings are stored. If your settings are stored in the System container (which is typical with upgrade deployments that have not had the global settings migrated to the Configuration container), you define a domain controller in the root of your Active Directory forest. If the global settings are in the Configuration container (which is typical with new deployments or upgrade deployments where the settings have been migrated to the Configuration container), you define any domain controller in the forest. If you do not specify this parameter, the cmdlet assumes that the settings are stored in the Configuration container and refers to any domain controller in AD&nbsp;DS.

    
    </div>
    
    If you do not specify the **Domain** parameter, the default is the local domain.
    
    This cmdlet returns a value of **LC\_DOMAINSETTINGS\_STATE\_READY** if domain preparation was successful.

</div>

<div>

## See Also


[Using cmdlets to reverse domain preparation for Lync Server 2013](lync-server-2013-using-cmdlets-to-reverse-domain-preparation.md)  


[Preparing domains for Lync Server 2013](lync-server-2013-preparing-domains.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

