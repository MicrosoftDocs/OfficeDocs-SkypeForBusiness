---
title: "Front End Mediation Service Settings Expander for Lync Server 2010"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.FeMediationServiceSettingsExpander2010
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 37166b87-8a43-42a6-a2aa-5a45bed8a6f3
description: "You edit the properties of the Mediation Server PSTN gateway settings in this dialog. You define the following settings:"
---

# Front End Mediation Service Settings Expander for Lync Server 2010
 
You edit the properties of the **Mediation Server PSTN gateway** settings in this dialog. You define the following settings:
  
- Select the **Collocated Mediation Server enabled** if you want to collocate the Mediation Server with this Front End Server or Front End pools.
    
- **Listening ports**: Define the ports that the Mediation Server will listen on. You can define a port for **TLS** or transport layer security, or **TCP**, or transport control protocol. For the port entry for TCP to be available, you must select the check box for **Enable TCP port**. 
    
    > [!IMPORTANT]
    > Refer to the documentation and configuration settings for your public switched telephone network (PSTN) gateway to determine if you need to enable and define port values TLS, TCP or both. TLS is a more secure protocol, using certificates to encrypt the traffic between the Mediation Server and the PSTN gateway. Not all PSTN gateways support TLS. 
  
- A listing of currently associated and existing **Trunk** (that is, Session Initiation Protocol (SIP) Trunks), **Gateway** (PSTN gateway or IP-PBX) and **Site** (configured site for the trunk and gateway).
    
- You select a Trunk, Gateway and Site and click **Make Default** to set the selection as the default for this Mediation service. You select the current default and click **Unmake Default** to remove the selection as the current default. You then select a new default and click **Make Default**.
    
  **OK** Accepts and commits changes to the dialog.
  
  **Cancel** Discards changes and closes the dialog.
  
  **Help** Displays this help screen.
  

