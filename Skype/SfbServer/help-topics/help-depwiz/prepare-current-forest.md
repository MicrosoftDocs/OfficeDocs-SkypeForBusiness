---
title: "Prepare Current Forest"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/8/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployMainForestPrep
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 11f5e359-97eb-45f7-a730-9ddbbaa40b83
description: "To prepare the Active Directory Domain Services forest, you must successfully extend the schema, as described in the topic Running Schema Preparation, and make sure that the schema has replicated."
---

# Prepare Current Forest

To prepare the Active Directory Domain Services forest, you must successfully extend the schema, as described in the topic [Running Schema Preparation](https://technet.microsoft.com/library/067726ae-fd3f-4133-a32f-26d2603ac674.aspx), and make sure that the schema has replicated.

After completing these prerequisites, you can begin **Step 3: Prepare Current Forest**. To prepare the forest, log on to a computer in the forest root as a member of Domain Admins in the forest root, or as a member of the Enterprise Admins for the forest that you are preparing.

1. From the Deployment Wizard at **Step 3: Prepare Current Forest**, click **Run**.

2. From the **Prepare Forest** page, click **Next**.

    > [!NOTE]
    > Forest Preparation enables you to choose where to place the Universal Groups for Skype for Business Server 2015. Choose a location that is consistent with the requirements of your organization.

3. On the **Executing Commands** page, look for **Task status: Completed**, and then click **View Log**. Make sure that there are no errors. Review the warnings to determine if they are expected and typical for your infrastructure.

4. Under the **Action** column in the log, expand **Forest Prep**, look for a **\<Success\>** Execution Result at the end of each task to verify that forest preparation completed successfully, close the log, and then click **Finish**.

5. Wait for Active Directory Domain Services replication to complete, or force replication to all domain controllers listed in the **Active Directory Sites and Services** snap-in for the forest root domain controller, before running domain preparation. Force replication between the domain controllers in all Active Directory sites to cause replication within the sites to occur within minutes.

    > [!TIP]
    > If you need to review the log files that are created by the Skype for Business Server Deployment Wizard, you can find them on the computer where the Deployment Wizard was run, in the Users directory of the Active Directory Domain Services user who ran the step. For example, if the user logged in as the domain administrator in the domain Contoso.net, the log files are located in: C:\Users\Administrator.Contoso\AppData\Local\Temp


