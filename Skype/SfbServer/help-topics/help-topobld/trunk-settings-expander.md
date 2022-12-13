---
title: "Trunk Settings Expander"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/27/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.TrunkSettingsExpander
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 3d00e8f4-e599-4094-a4a1-34fd6e8a5580
description: "To edit or modify the settings for a SIP trunk, you do the following:"
---

# Trunk Settings Expander

To edit or modify the settings for a SIP trunk, you do the following:

 **Trunk name** is a required entry and uniquely identifies the SIP trunk in the deployment.

 **Associated PSTN gateway**: Select an existing PSTN gateway that has been defined in the deployment.

 **Listening port for IP/PSTN gateway**: Indicates what TCP/IP port the gateway will be listening for requests on. The required value may differ, based on the vendor of the gateway, but the default is port 5067.

 **SIP Transport Protocol**: The protocol used is either TCP or TLS. TLS is the default. Refer to the gateway vendor documentation for what you gateway supports. The default is TLS, and should be considered the more secure selection, if the gateway supports TLS.

 **Associated Mediation Server**: Select an existing Mediation Server from the deployment to associate with the SIP trunk.

> [!NOTE]
> Only the root trunk can be associated with a Lync Server 2010 or Lync Server 2013 Mediation Server.

 **Associated Mediation Server port**: A required value, this is set to the value that the Mediation Server is configured to listen on.

![Trunk Settings Expander.](../../media/Trunk_Settings_Expander.jpg)

## See also

[SIP Trunking Deployment Checklist](/previous-versions/office/lync-server-2013/lync-server-2013-sip-trunk-deployment-checklist)

[Components and Topologies for SIP Trunking](/previous-versions/office/lync-server-2013/lync-server-2013-components-and-topologies-for-sip-trunking)