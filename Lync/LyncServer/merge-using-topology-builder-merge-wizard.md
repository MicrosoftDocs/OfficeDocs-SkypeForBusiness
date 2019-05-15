---
title: Merge using Topology Builder Merge wizard
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Merge using Topology Builder Merge wizard
ms:assetid: c3f3c425-dab6-4dcd-bf0e-d7fde05f2ebf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205243(v=OCS.15)
ms:contentKeyID: 48185343
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Merge using Topology Builder Merge wizard

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-02_

1.  Download the existing deployment using Topology Builder.

2.  From the **Action** menu, select **Merge Office Communications Server 2007 R2**.

3.  Click **Next**.

4.  In **Specify Edge Setup**, click **Add**.
    
    ![Merge Topology Wizard, Specify Edge Setup page](images/JJ205243.cdca609d-d4d5-47d9-9ff8-8b1daa4106e1(OCS.15).jpg "Merge Topology Wizard, Specify Edge Setup page")  

5.  In **Specify Edge Type**, enter the type of Edge Server configuration, and then click **Next**. This example uses the **Single Edge Server** option.
    
    <div>
    

    > [!IMPORTANT]  
    > <STRONG>Expanded Edge deployment</STRONG> is not a supported configuration. An <STRONG>Expanded Edge Server</STRONG> must first be converted to a <STRONG>Single Edge Server</STRONG> or a <STRONG>Load-balanced consolidated Edge</STRONG> Server.

    
    </div>

6.  In **Specify Internal Edge Settings** , enter the relevant information for your Edge pool’s internal FQDN and ports as needed, and then click **Next**.
    
    ![Specify Internal Edge Settings dialog](images/JJ205243.dd664761-839c-4ac8-bd1a-5525589dfbb0(OCS.15).jpg "Specify Internal Edge Settings dialog")  

7.  In **Specify External Edge**, enter the web conferencing FQDN information for your Edge Server.
    
    <div>
    

    > [!IMPORTANT]  
    > Before you click <STRONG>Next</STRONG>, do the next step in this procedure. It is very important that you do not miss this step.

    
    </div>

8.  Check the **This Edge pool is used for federation and public IM connectivity** check box if you plan to use the legacy Office Communications Server 2007 R2 Edge Server for federation. If you have multiple Edge Servers deployed, only one of them will be enabled for federation. If you do not check this box and you decide later that you want to enable federation, you must run the Topology Builder Merge wizard and publish your topology again.
    
    ![Edge Server dialog, Specify External Edge page](images/JJ205243.32e97ce5-92f0-477e-8125-5d2ece237b13(OCS.15).jpg "Edge Server dialog, Specify External Edge page")  

9.  In **Specify Next Hop**, enter the fully qualified domain name (FQDN) of the next hop location in your environment. Click **Finish**.
    
    ![Edge Server dialog, Specify Next Hop page](images/JJ205243.e734ee0d-f91c-4f3f-8ae6-248ecabcf678(OCS.15).jpg "Edge Server dialog, Specify Next Hop page")  

10. In **Specify Edge Setup**, if all your Office Communications Server 2007 R2 Edge Servers have been added, click **Next**. If you have more Office Communications Server 2007 R2 Edge Servers to add, repeat this procedure starting at step 4.

11. In **Specify Internal SIP port** , select the default setting (that is, if you did not modify the default SIP port). Change as appropriate if you are not using a default port of 5061, and then click **Next**.

12. In **Summary**, click **Next** to begin merging the topologies.

13. The wizard page verifies that the merging of the topologies was successful.

14. In the **Status** column, verify that the value is **Success**, and then click **Finish**.

15. In the left pane of Topology Builder, you should now see the **BackCompatSite**, which indicates that your Office Communications Server 2007 R2 environment has been merged with Lync Server 2013.
    
    ![Topology Builder showing a merged topology](images/JJ205243.62751c76-f018-4c6d-bb48-c61ef8974d31(OCS.15).jpg "Topology Builder showing a merged topology")  

16. From the **Action** menu, click **Publish Topology**, and then click **Next**.

17. When the **Publishing wizard** completes, click **Finish**.
    
    <div>
    

    > [!NOTE]  
    > It’s important that you complete the next topic, <A href="import-policies-and-settings.md">Import policies and settings</A>, to ensure that the legacy policy settings are imported into Lync Server 2013.

    
    </div>

</div>

<span> </span>

</div>

</div>

</div>

