---
title: "Trunk Settings Expander"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.tb.TrunkSettingsExpander
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3d00e8f4-e599-4094-a4a1-34fd6e8a5580
description: "To edit or modify the settings for a SIP trunk, you do the following:"
---

# Trunk Settings Expander
[]
To edit or modify the settings for a SIP trunk, you do the following:
  
 **Trunk name** is a required entry and uniquely identifies the SIP trunk in the deployment. 
  
 **Associated PSTN gateway**: Select an existing PSTN gateway that has been defined in the deployment.
  
 **Listening port for IP/PSTN gateway**: Indicates what TCP/IP port the gateway will be listening for requests on. The required value may differ, based on the vendor of the gateway, but the default is port 5067.
  
 **SIP Transport Protocol**: The protocol used is either TCP or TLS. TLS is the default. Refer to the gateway vendor documentation for what you gateway supports. The default is TLS, and should be considered the more secure selection, if the gateway supports TLS.
  
 **Associated Mediation Server**: Select an existing Mediation Server from the deployment to associate with the SIP trunk.
  
> [!NOTE]
> Only the root trunk can be associated with a Lync Server 2010 Mediation Server. 
  
 **Associated Mediation Server port**: A required value, this is set to the value that the Mediation Server is configured to listen on.
  
![Trunks Settings Expander](media/Trunk_Settings_Expander.jpg)
  
## See also

#### 

[SIP trunk deployment checklist for Lync Server 2013](sip-trunk-deployment-checklist.md)
  
[Components and topologies for SIP trunking in Lync Server 2013](components-and-topologies-for-sip-trunking.md)

