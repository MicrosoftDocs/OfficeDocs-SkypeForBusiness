---
title: "Prepare Current Domain"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.dep.DeployMainDomainPrep
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bfcb37ca-34eb-4d0d-9694-6edd2e7fe0f3
description: "To prepare a domain to host servers running Lync Server 2013 or Lync Server users, you must complete Step 5: Prepare Current Domain, as described in the topic Running domain preparation for Lync Server 2013. To complete the step, you must be logged in as a member of the Domain Admins group in the domain that you are preparing, or as a member of the Enterprise Admins group of the forest that the domain belongs to. To prepare the domain:"
---

# Prepare Current Domain
[]
To prepare a domain to host servers running Lync Server 2013 or Lync Server users, you must complete **Step 5: Prepare Current Domain**, as described in the topic [Running domain preparation for Lync Server 2013](running-domain-preparation.md). To complete the step, you must be logged in as a member of the Domain Admins group in the domain that you are preparing, or as a member of the Enterprise Admins group of the forest that the domain belongs to. To prepare the domain:
  
1. From the Lync Server 2013 installation folder or media, run Setup.exe to start the Lync Server Deployment Wizard.
    
2. Click **Prepare Active Directory**, and then wait for the deployment state to be determined.
    
3. At **Step 5: Prepare Current Domain**, click **Run**.
    
4. On the **Executing Commands** page, look for **Task status: Completed**, and then click **View Log**.
    
5. Under the **Action** column, expand **Domain Prep**, look for a **\<Success\>** Execution Result at the end of each task to verify that domain preparation completed successfully, close the log, and then click **Finish**.
    
> [!TIP]
> If you need to review the log files that are created by the Lync Server Deployment Wizard, you can find them on the computer where the Deployment Wizard was run in the Users directory of the Active Directory Domain Services user who ran the step. For example, if the user logged in as the domain administrator in the domain Contoso.net, the log files are located in: > C:\Users\Administrator.Contoso\AppData\Local\Temp. 
  

