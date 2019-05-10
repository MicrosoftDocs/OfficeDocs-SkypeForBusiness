---
title: "Mediation Server General Settings Expander for Lync Server 2010"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.MediationServerGeneralSettingsExpander2010
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 48e434c1-0c3c-4502-9441-c0a3c340f51f
description: "You edit the properties of the Mediation Servers in this dialog. Along the left side is a set of quick links to take you to settings for General settings, Next hop settings, and PSTN gateway settings. In each section are the following settings:"
---

# Mediation Server General Settings Expander for Lync Server 2010

You edit the properties of the Mediation Servers in this dialog. Along the left side is a set of quick links to take you to settings for General settings, Next hop settings, and PSTN gateway settings. In each section are the following settings:

 **General**:

- **FQDN**: You edit the fully qualified domain name of the Mediation Server

- **Associations**: Select the **Associate Edge pool (for media components)** check box and select an Edge Server or Edge pool for the Mediation Server to use as the media path for external access.

  **Next hop**:

- **Next hop selection**: Select from a list the Front End Server or Front End pool to use as the path for the Mediation Server to use for communicating with your deployment.

  **PSTN gateway**:

  **Mediation Server PSTN gateway**:

- **Listening ports**: Define the ports that the Mediation Server will listen on. You can define a port for **TLS** or transport layer security, or **TCP**, or transport control protocol. For the port entry for TCP to be available, you must select the check box for **Enable TCP port**.

    > [!IMPORTANT]
    > Refer to the documentation and configuration settings for your public switched telephone network (PSTN) gateway to determine if you need to enable and define port values TLS, TCP or both. TLS is a more secure protocol, using certificates to encrypt the traffic between the Mediation Server and the PSTN gateway. Not all PSTN gateways support TLS.

- A listing of SIP trunks and the gateways that are defined and configured for your deployment is listed. If no entries are present, there are no SIP trunks or PSTN gateways configured for your deployment. You define and configure trunks and gateways under **Shared Components** in Topology Builder.

## See also

[Overview of SIP Trunking](https://technet.microsoft.com/library/204f2c21-436f-4b2d-93ea-d6db98fa2952.aspx)

[PSTN Gateway Deployment Options](https://technet.microsoft.com/library/d1ab4f74-18aa-40c7-a8cf-ec806cf6e28a.aspx)
