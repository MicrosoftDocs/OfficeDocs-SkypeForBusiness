---
title: "Prepare Current Domain"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployMainDomainPrep
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: bfcb37ca-34eb-4d0d-9694-6edd2e7fe0f3
ROBOTS: NOINDEX, NOFOLLOW
description: "To prepare a domain to host servers running Skype for Business Server or Skype for Business Server users, you must complete Step 5: Prepare Current Domain, as described in the topic Using Setup to Run Domain Preparation. To complete the step, you must be logged in as a member of the Domain Admins group in the domain that you are preparing, or as a member of the Enterprise Admins group of the forest that the domain belongs to. To prepare the domain:"
---

# Prepare Current Domain

To prepare a domain to host servers running Skype for Business Server or Skype for Business Server users, you must complete **Step 5: Prepare Current Domain**, as described in the topic [Using Setup to Run Domain Preparation](https://technet.microsoft.com/library/95dab800-1f2c-4506-b36c-99986643b149.aspx). To complete the step, you must be logged in as a member of the Domain Admins group in the domain that you are preparing, or as a member of the Enterprise Admins group of the forest that the domain belongs to. To prepare the domain:

1. From the Skype for Business Server installation folder or media, run Setup.exe to start the Skype for Business Server Deployment Wizard.

2. Click **Prepare Active Directory**, and then wait for the deployment state to be determined.

3. At **Step 5: Prepare Current Domain**, click **Run**.

4. On the **Executing Commands** page, look for **Task status: Completed**, and then click **View Log**.

5. Under the **Action** column, expand **Domain Prep**, look for a **\<Success\>** Execution Result at the end of each task to verify that domain preparation completed successfully, close the log, and then click **Finish**.

> [!TIP]
> If you need to review the log files that are created by the Skype for Business Server Deployment Wizard, you can find them on the computer where the Deployment Wizard was run in the Users directory of the Active Directory Domain Services user who ran the step. For example, if the user logged in as the domain administrator in the domain Contoso.net, the log files are located in: C:\Users\Administrator.Contoso\AppData\Local\Temp.


