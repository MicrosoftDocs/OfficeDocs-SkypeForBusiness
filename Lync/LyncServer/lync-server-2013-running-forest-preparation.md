---
title: 'Lync Server 2013: Running forest preparation'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Running forest preparation
ms:assetid: 9d62f7be-bcfe-421d-8d8a-225567102a35
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412732(v=OCS.15)
ms:contentKeyID: 48184991
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Running forest preparation for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-29_

You can use Setup or Lync Server Management Shell cmdlets to prepare the forest. The cmdlet that prepares the forest is **Enable-CsAdForest**.

After you prepare the forest, you must verify that global settings have been replicated before running domain preparation.

<div>

## To use Setup to prepare the forest

1.  Log on to a computer that is joined to a domain as a member of the Enterprise Admins group for the forest root domain.

2.  From the Lync Server 2013 installation folder or media, run Setup.exe to start the Deployment Wizard.

3.  Click **Prepare Active Directory**, and then wait for the deployment state to be determined.

4.  At **Step 3: Prepare Current Forest**, click **Run**.

5.  On the **Prepare Forest** page, click **Next**.
    
    <div>
    

    > [!NOTE]  
    > Forest Preparation allows you to choose where to place the Universal Groups for Lync Server 2013. Choose a location that is consistent with the requirements of your organization.

    
    </div>

6.  On the **Executing Commands** page, look for **Task status: Completed**, and then click **View Log**.

7.  Under the **Action** column, expand **Forest Prep**, look for a **\<Success\>** Execution Result at the end of each task to verify that forest preparation completed successfully, close the log, and then click **Finish**.

8.  Wait for Active Directory replication to complete, or force replication to all domain controllers listed in the **Active Directory Sites and Services** snap-in for the forest root domain controller, before running domain preparation. Force replication between the domain controllers in all Active Directory sites to cause replication within the sites to occur within minutes.

</div>

<div>

## To use cmdlets to prepare the forest

1.  Log on to a computer that is joined to a domain as a member of the Domain Admins group in the forest root domain.

2.  Install Lync Server Core components as follows:
    
    1.  From the Lync Server 2013 installation folder or media, run Setup.exe to start the Lync Server Deployment Wizard.
    
    2.  If you are prompted to install the Microsoft Visual C++ Redistributable, click **Yes**.
    
    3.  The Lync Server 2013 Setup dialog box prompts you for a location to install the Lync Server files. Choose the default location or **Browse** to a location of your choice, and then click **Install**.
    
    4.  On the License Agreement page, check **I accept the terms in the license agreement**, and then click **OK**. The installer installs the Lync Server 2013 Core Components.

3.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

4.  Run:
    
        Enable-CsAdForest [-GroupDomain <FQDN of the domain in which to create the universal groups>]
    
    For example:
    
        Enable-CsAdForest -GroupDomain domain1.contoso.com 
    
    If you do not specify the GroupDomain parameter, the default value is the local domain. If universal groups were created previously in a domain that is not the default domain, you must specify the GroupDomain parameter explicitly.

5.  Wait for Active Directory replication to complete, or force replication to all domain controllers listed in the **Active Directory Sites and Services** snap-in for the forest root domain controller, before running domain preparation.

6.  Verify that forest preparation was successful. Run:
    
        Get-CsAdForest 
    
    This cmdlet returns a value of **LC\_FORESTSETTINGS\_STATE\_READY** if forest preparation was successful.

</div>

<div>

## See Also


[Using cmdlets to reverse forest preparation for Lync Server 2013](lync-server-2013-using-cmdlets-to-reverse-forest-preparation.md)  


[Preparing the forest for Lync Server 2013](lync-server-2013-preparing-the-forest.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

