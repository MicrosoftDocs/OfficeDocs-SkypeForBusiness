---
title: "Publish the location database from Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dd032b5b-df0e-4017-ac46-e17570c1ab1e
description: "The new locations that you added to the location database will not be made available to the client until they have been published."
---

# Publish the location database from Lync Server 2013
[]
The new locations that you added to the location database will not be made available to the client until they have been published.
  
For details, see the Lync Server Management Shell documentation for the following cmdlet:
  
- **Publish-CsLisConfiguration**
    
If you use Emergency Location Identification Number (ELIN) gateways, you also need to upload the ELINs to your public switched telephone network (PSTN) carrier's Automatic Location Identification (ALI) database. Your PSTN carrier may require you to use a specific format for the ELIN records. Contact your PSTN carrier for details. You can export the records from the Location Information service database and format them as required.
  
### To publish the location database

-  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
- Run the following cmdlet to publish the location database.
    
  ```
  Publish-CsLisConfiguration
  
  ```


