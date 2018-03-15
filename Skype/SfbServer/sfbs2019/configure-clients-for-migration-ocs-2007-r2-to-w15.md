---
title: "Configure clients for migration [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8f17862b-d9d1-47f6-b248-51f4710f5030
description: "This topic contains the recommended client deployment steps you should take prior to migrating to Lync Server 2013. These configuration changes should be made on Office Communications Server 2007 R2. It is very important that you perform these steps prior to migrating. For details, see Planning for clients and devices in Lync Server 2013."
---

# Configure clients for migration [OCS 2007 R2 to W15]
[]
This topic contains the recommended client deployment steps you should take prior to migrating to Lync Server 2013. These configuration changes should be made on Office Communications Server 2007 R2. It is very important that you perform these steps prior to migrating. For details, see [Planning for clients and devices in Lync Server 2013](planning-for-clients-and-devices-in-lync-server.md). 
  
### To configure clients prior to migration

1. Deploy the most recent Office Communications Server 2007 R2 server, client, and device updates (hotfixes):
    
  - [Apply Office Communications Server 2007 R2 updates [OCS 2007 R2 to W15]](apply-office-communications-server-2007-r2-updates-ocs-2007-r2-to-w15.md)
    
  - [Description of the cumulative update package for Communicator 2007 R2](https://go.microsoft.com/fwlink/p/?LinkId=335808)
    
  - [Obtaining Software Updates for Devices](https://go.microsoft.com/fwlink/?LinkId=335809)
    
2. On Office Communications Server 2007 R2, use Client Version Filtering to allow only Office Communications Server 2007 R2 clients with the most current updates installed to sign in.
    
3. On Office Communications Server 2007 R2, use Client Version Filtering to block Lync Server 2013 clients from signing in. Follow the steps described in **Configuring Client Version Filtering** at [https://go.microsoft.com/fwlink/p/?linkId=202488](https://go.microsoft.com/fwlink/p/?linkId=202488) to add the version filters listed in the following table. For each version filter, assign the action **Block**.
    
|**Client**|**User agent header**|**Version**|
|:-----|:-----|:-----|
|Lync 2013  <br/> |OC  <br/> |15.\*.\*.\*  <br/> |
|Lync Web App  <br/> |CWA  <br/> |5.\*.\*.\*  <br/> |
|Lync Phone Edition  <br/> |OCPhone  <br/> |4.\*.\*.\*  <br/> |
   

