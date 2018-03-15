---
title: "Installing the Operation Manager agent files in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e2246c44-0c75-43fc-8b04-26e53c5dd572
description: "To install the Operations Manager agent files on the computer, complete the following steps."
---

# Installing the Operation Manager agent files in Lync Server 2013
[]
To install the Operations Manager agent files on the computer, complete the following steps. 
  
1. On your System Center setup media, double-click **SetupOM.exe**.
    
2. In System Center Operation Manager setup, click **Install Operations Manager Agent**.
    
3. In System Center Setup wizard, on the **Welcome to the System Center Operations Manager Setup** wizard page, click **Next**.
    
4. On the **Destination Folder** page, select the folder where the Operations Manager Agent files will be installed, and then click **Next**.
    
5. On the **Management Group Configuration** page, select **Specify Management Group information**, and then click **Next**.
    
6. On the **Management Group Configuration** page, type the name of your Operations Manager Management Group in the **Management Group Name** box, and then type the host name of your Operations Manager server (for example, atl-scom-001) in the **Management Server** box. If you have changed the port number used by Operations Manager, then type the new port number in the Management Server Port box. Otherwise, leave the port at the default value of 5723 and click **Next**.
    
7. On the **Agent Action Account** page, select **Local System**, and then click **Next**.
    
8. On the **Microsoft Update** page, select **I don't want to use Microsoft Update**, and then click **Next**.
    
9. On the **Ready to Install** page, click **Install**.
    
10. On the **Completing the System Center Operations Manager Setup wizard** page, click **Finish**.
    
11. Click **Exit**.
    
If you are using System Center 2007 R2, you can verify that the agent has been created by clicking **Start**, clicking **All Programs**, clicking **System Center Operations Manager 2007 R2**, and then clicking **Operations Manager Shell**. In the Operations Manager Shell, type the following Windows PowerShell command, and then press ENTER:
  
```
Get-Agent 
```

A list of all your Operations Manager agents will appear onscreen.
  
If you are using System Center 2012, run this command from the Operations 2012 Manager Shell:
  
```
Get-SCOMAgent
```


