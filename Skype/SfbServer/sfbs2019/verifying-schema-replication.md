---
title: "Verifying Active Directory schema replication in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ad01a7cf-aa79-4648-ba5a-a7a09172db36
description: "Before you run forest preparation, manually verify that the schema partition has been replicated."
---

# Verifying Active Directory schema replication in Lync Server 2013
[]
 Before you run forest preparation, manually verify that the schema partition has been replicated. 
  
### To manually verify schema replication

1. Log on to a domain controller as a member of the Enterprise Admins group.
    
2. Open ADSI Edit by clicking **Start**, clicking **Administrative Tools**, and then clicking **ADSI Edit**.
    
    > [!TIP]
    > Alternatively, you can run **adsiedit.msc** from the command line. 
  
3. In the Microsoft Management Console (MMC) tree, if it is not already selected, click **ADSI Edit**.
    
4. On the **Action** menu, click **Connect to**.
    
5. In the **Connection Settings** dialog box under **Select a well known Naming Context**, select **Schema**, and then click **OK**.
    
6. Under the schema container, search for CN=ms-RTC-SIP-SchemaVersion. If this object exists, and the value of the **rangeUpper** attribute is 1150 and the value of the **rangeLower** attribute is 3, then the schema was successfully updated and replicated. If this object does not exist or the values of the **rangeUpper** and **rangeLower** attributes are not as specified, then the schema was not modified or has not replicated. 
    
## See also

#### 

[Running Active Directory schema preparation in Lync Server 2013](running-schema-preparation.md)
#### 

[Preparing the Active Directory schema in Lync Server 2013](preparing-the-active-directory-schema.md)

