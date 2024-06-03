---
title: "Verify Replication of Schema Partition"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/17/2018
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.dep.DeployMainVerifySchemaPrep
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: 0357f230-6d0c-41f1-942c-e14f76e55d31
description: "To verify that the schema extensions are successfully replicated in your Active Directory Domain Services forest, do the following:"
---

# Verify Replication of Schema Partition
 
To verify that the schema extensions are successfully replicated in your Active Directory Domain Services forest, do the following:
  
1. Sign in a domain controller (other than the domain controller that holds the schema master role) in your Active Directory Domain Services forest, where the schema extensions were applied as a member of the Enterprise Admins group.
    
2. Open ADSI Edit: Select **Start**, select **Administrative Tools**, and then select **ADSI Edit**.
    
    > [!TIP]
    > Alternatively, click **Start**, then click **Run**, type **adsiedit.msc** to start ADSI Edit.
  
3. In the Microsoft Management Console (MMC) tree, if it isn't already selected, select ADSI Edit.
    
4. On the **Action** menu, select **Connect to**.
    
5. In the **Connection Settings** dialog box under **Select a well known Naming Context**, select **Schema**, and then select **OK**.
    
6. Under the schema container, search for CN=ms-RTC-SIP-SchemaVersion. If this object exists, and the value of the **rangeUpper** attribute is 1150 and the value of the **rangeLower** attribute is 3, then the schema was successfully updated and replicated. If this object doesn't exist or if the values of the **rangeUpper** and **rangeLower** attributes aren't as specified, then the schema wasn't modified or hasn't replicated.
    
> [!NOTE]
> If your check of the replication of the schema does not yet show a successful replication, wait approximately 15 minutes and then check again. Active Directory replication is based on a loose consistency model and some replication latency can occur, based on a number of factors in the server and infrastructure. 
  

