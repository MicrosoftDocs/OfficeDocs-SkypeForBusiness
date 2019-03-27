---
title: "External Application General Settings Expander"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.ExternalApplicationGeneralSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: aa7268ac-b9e3-4d25-bff4-e59d305120f2
description: "To edit the properties for a trusted application server that has already been defined, follow these instructions."
---

# External Application General Settings Expander
 
To edit the properties for a trusted application server that has already been defined, follow these instructions.
  
There are two sections that you can modify:
  
> General settings
> 
> Next hop settings
    
## General Settings

You can modify the current fully qualified domain name (FQDN) for the trusted application server pool. Edit the name of the pool FQDN. The Domain Name System (DNS) host (A) records must exist for the new entry before clients or servers can connect to the new pool name.
  
Select **Enable replication of configuration data to this pool** if you need to have replication of configuration data to this pool. Clear the check mark if you do not want to replicate the configuration data.
  
## Next Hop Settings

You can specify the trusted application server pool's next hop server by selecting the defined Enterprise Edition Front End pool or Standard Edition Front End Server from the drop-down list. A Director or Director pool is not a valid selection for a trusted application server next hop and will not appear in the list.
  


Click **OK** to accept and save your changes. Click **Cancel** to discard your changes and exit the properties page.
  

