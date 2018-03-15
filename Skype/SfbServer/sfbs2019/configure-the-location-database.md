---
title: "Configure the location database in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8544be31-6958-47ef-b926-fdc80d56191c
description: "To enable clients to automatically detect their location within a network, you first need to configure the location database. If you do not configure a location database, and Location Required in the location policy is set to Yes or Disclaimer, the user will be prompted to manually enter a location."
---

# Configure the location database in Lync Server 2013
[]
To enable clients to automatically detect their location within a network, you first need to configure the location database. If you do not configure a location database, and **Location Required** in the location policy is set to **Yes** or **Disclaimer**, the user will be prompted to manually enter a location.
  
To configure the location database, you will perform the following tasks: 
  
1. Populate the database with a mapping of network elements to locations. If you use an Emergency Location Identification Number (ELIN) gateway, you need to include the ELIN in the \<CompanyName\> field.
    
2. Validate the addresses against the master street address guide (MSAG) that is maintained by the E9-1-1 service provider.
    
3. Publish the updated database.
    
> [!NOTE]
> Alternately, you can define a secondary location source database that can be used in placed of the location database. For details, see [Configure a secondary Location Information service in Lync Server 2013](configure-a-secondary-location-information-service.md). 
  
## In this section

- [Populate the location database in Lync Server 2013](populate-the-location-database.md)
    
- [Validate addresses in Lync Server 2013](validate-addresses.md)
    
- [Publish the location database from Lync Server 2013](publish-the-location-database.md)
    

