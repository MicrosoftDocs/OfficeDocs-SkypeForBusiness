---
title: "Merge using Topology Builder Merge wizard [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c3f3c425-dab6-4dcd-bf0e-d7fde05f2ebf
description: ""
---

# Merge using Topology Builder Merge wizard [OCS 2007 R2 to W15]
[]
1. Download the existing deployment using Topology Builder.
    
2. From the **Action** menu, select **Merge Office Communications Server 2007 R2**.
    
3. Click **Next**.
    
4. In **Specify Edge Setup**, click **Add**.
    
     ![Merge Topology Wizard, Specify Edge Setup page](media/Migration_LyncServer_TopoBuilder_OCS2007R2_SpecifyEdgeServer.JPG)
  
5. In **Specify Edge Type**, enter the type of Edge Server configuration, and then click **Next**. This example uses the **Single Edge Server** option. 
    
    > [!IMPORTANT]
    > **Expanded Edge deployment** is not a supported configuration. An **Expanded Edge Server** must first be converted to a **Single Edge Server** or a **Load-balanced consolidated Edge** Server. 
  
6. In **Specify Internal Edge Settings**, enter the relevant information for your Edge pool's internal FQDN and ports as needed, and then click **Next**.
    
     ![Specify Internal Edge Settings dialog](media/Migration_LyncServer_TopoBuilder_OCS2007R2_SpecifyIntEdgeSettings.jpg)
  
7. In **Specify External Edge**, enter the web conferencing FQDN information for your Edge Server. 
    
    > [!IMPORTANT]
    > Before you click **Next**, do the next step in this procedure. It is very important that you do not miss this step. 
  
8. Check the **This Edge pool is used for federation and public IM connectivity** check box if you plan to use the legacy Office Communications Server 2007 R2 Edge Server for federation. If you have multiple Edge Servers deployed, only one of them will be enabled for federation. If you do not check this box and you decide later that you want to enable federation, you must run the Topology Builder Merge wizard and publish your topology again. 
    
     ![Edge Server dialog, Specify External Edge page](media/migration_lyncserver_w15_specifyedgetype_postmerge.JPG)
  
9. In **Specify Next Hop**, enter the fully qualified domain name (FQDN) of the next hop location in your environment. Click **Finish**.
    
     ![Edge Server dialog, Specify Next Hop page](media/Migration_LyncServer_TopoBuilder_OCS2007R2_SpecifyNextHopSettings.jpg)
  
10. In **Specify Edge Setup**, if all your Office Communications Server 2007 R2 Edge Servers have been added, click **Next**. If you have more Office Communications Server 2007 R2 Edge Servers to add, repeat this procedure starting at step 4. 
    
11. In **Specify Internal SIP port**, select the default setting (that is, if you did not modify the default SIP port). Change as appropriate if you are not using a default port of 5061, and then click **Next**.
    
12. In **Summary**, click **Next** to begin merging the topologies. 
    
13. The wizard page verifies that the merging of the topologies was successful.
    
14. In the **Status** column, verify that the value is **Success**, and then click **Finish**.
    
15. In the left pane of Topology Builder, you should now see the **BackCompatSite**, which indicates that your Office Communications Server 2007 R2 environment has been merged with Lync Server 2013.
    
     ![Topology Builder showing a merged topology](media/Migration_LyncServer_TopoBuilder_OCS2007R2_FinalPage.JPG)
  
16. From the **Action** menu, click **Publish Topology**, and then click **Next**.
    
17. When the **Publishing wizard** completes, click **Finish**.
    
    > [!NOTE]
    > It's important that you complete the next topic, [Import policies and settings [OCS 2007 R2 to W15]](import-policies-and-settings-ocs-2007-r2-to-w15.md), to ensure that the legacy policy settings are imported into Lync Server 2013. 
  

