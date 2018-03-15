---
title: "External Application General Settings Expander"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.tb.ExternalApplicationGeneralSettingsExpander
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aa7268ac-b9e3-4d25-bff4-e59d305120f2
description: "In this articleGeneral SettingsNext Hop Settings"
---

# External Application General Settings Expander
[]
 **In this article**
  
[General Settings](#sectionSection0)
  
[Next Hop Settings](#sectionSection1)
  
[](#sectionSection2)
  
To edit the properties for a trusted application server that has already been defined, follow these instructions.
  
There are two sections that you can modify:
  
> General settings
    
> Next hop settings
    
## General Settings
<a name="sectionSection0"> </a>

You can modify the current fully qualified domain name (FQDN) for the trusted application server pool. Edit the name of the pool FQDN. The Domain Name System (DNS) host (A) records must exist for the new entry before clients or servers can connect to the new pool name.
  
Select **Enable replication of configuration data to this pool** if you need to have replication of configuration data to this pool. Clear the check mark if you do not want to replicate the configuration data. 
  
## Next Hop Settings
<a name="sectionSection1"> </a>

You can specify the trusted application server pool's next hop server by selecting the defined Enterprise Edition Front End pool or Standard Edition Front End Server from the drop-down list. A Director or Director pool is not a valid selection for a trusted application server next hop and will not appear in the list.
  
## 
<a name="sectionSection2"> </a>

Click **OK** to accept and save your changes. Click **Cancel** to discard your changes and exit the properties page. 
  

