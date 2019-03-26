---
title: 'Lync Server 2013: Running schema preparation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Running schema preparation
ms:assetid: 9d02bdb1-ff29-417a-bcce-b068b31207d8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412729(v=OCS.15)
ms:contentKeyID: 48184911
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Running Active Directory schema preparation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-29_

You can use Setup or Lync Server Management Shell cmdlets to prepare the Active Directory schema. The cmdlet that extends the Active Directory schema is **Install-CsAdServerSchema**.

<div>


> [!NOTE]  
> The schema preparation cmdlet (<STRONG>Install-CsAdServerSchema</STRONG>) must access the schema master, which requires that the remote registry service is running and that the remote registry key is enabled. If the remote registry service cannot be enabled on the schema master, you can run the cmdlet locally on the schema master. For details about registry remote access, see Microsoft Knowledge Base article 314837, "How to Manage Remote Access to the Registry," at <A href="http://go.microsoft.com/fwlink/p/?linkid=125769">http://go.microsoft.com/fwlink/p/?linkId=125769</A>.



</div>

After you complete schema preparation, manually verify that the schema partition has been replicated before proceeding to forest preparation. For details, see [Verifying Active Directory schema replication in Lync Server 2013](lync-server-2013-verifying-schema-replication.md).

<div>

## To use Setup to prepare the schema of the current forest

1.  Log on to a server in your forest as a member of the Schema Admins group and with administrator rights on the schema master.

2.  From the Lync Server 2013 installation folder or media, run Setup.exe to start the Deployment Wizard.

3.  If you are prompted to install the Microsoft Visual C++ Redistributable, click **Yes**.

4.  The Lync Server 2013 Setup dialog box prompts you for a location to install the Lync Server files. Choose the default location or **Browse** to a location of your choice, and then click **Install**.

5.  On the License Agreement page, check **I accept the terms in the license agreement**, and then click **OK**.

6.  The installer installs the Lync Server Core Components.

7.  When the Deployment Wizard is ready, click **Prepare Active Directory**, and then wait for the deployment state to be determined.

8.  At **Step 1: Prepare Schema**, click **Run**.

9.  On the **Prepare Schema** page, click **Next**.

10. On the **Executing Commands** page, look for **Task status: Completed**, and then click **View Log**.

11. Under the **Action** column, expand **Schema Prep**, look for the **\<Success\>** Execution Result at the end of each task to verify that schema preparation completed successfully, close the log, and then click **Finish**.

12. Wait for Active Directory replication to complete or force replication.

13. Manually verify that the schema changes replicated to all other domain controllers. For details, see [Verifying Active Directory schema replication in Lync Server 2013](lync-server-2013-verifying-schema-replication.md).

</div>

<div>

## To use cmdlets to prepare the schema of the current forest

1.  Log on to a computer in the forest as a member of the Schema Admins group and with administrator rights on the schema master.

2.  Install Lync Server Core components as follows:
    
    1.  From the Lync Server 2013 installation folder or media, run Setup.exe to start the Lync Server Deployment Wizard.
    
    2.  If you are prompted to install the Microsoft Visual C++ Redistributable, click **Yes**.
    
    3.  The Lync Server 2013 Setup dialog box prompts you for a location to install the Lync Server files. Choose the default location or **Browse** to a location of your choice, and then click **Install**.
    
    4.  On the License Agreement page, check **I accept the terms in the license agreement**, and then click **OK**. The installer installs the Lync Server 2013 Core Components.

3.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

4.  Run:
    
        Install-CsAdServerSchema [-Ldf <directory where the .ldf file is located>] 
    
    If you do not specify the Ldf parameter, the default value is the Lync Server 2013 installation path that is read from the registry.
    
    For example:
    
        Install-CsAdServerSchema -Ldf "C:\Program Files\Microsoft Lync Server 2013\Deployment\Setup"

5.  Use the following cmdlet to verify that schema preparation ran to completion.
    
        Get-CsAdServerSchema 
    
    This cmdlet returns a value of **SCHEMA\_VERSION\_STATE\_CURRENT** if schema preparation was successful.

6.  Wait for Active Directory replication to complete or force replication.

7.  Manually verify that the schema changes replicated to all other domain controllers. For details, see [Verifying Active Directory schema replication in Lync Server 2013](lync-server-2013-verifying-schema-replication.md).

</div>

<div>

## See Also


[Verifying Active Directory schema replication in Lync Server 2013](lync-server-2013-verifying-schema-replication.md)  


[Preparing the Active Directory schema in Lync Server 2013](lync-server-2013-preparing-the-active-directory-schema.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

