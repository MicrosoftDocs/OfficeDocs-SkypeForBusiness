---
title: "Mediation Service Settings Expander for Lync Server 2010"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/26/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.MediationServiceSettingsExpander2010
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 230e0a08-9e16-4bbd-b550-1f04bad8ddbc
description: "You edit the properties of the Mediation service by defining the following properties:"
---

# Mediation Service Settings Expander for Lync Server 2010
 
You edit the properties of the Mediation service by defining the following properties:
  
- **Listening ports**: Define the **TLS** port that the Mediation service will listen on. By default, the port value is TCP 5067 over transport layer security (TLS)
    
    Optionally, you define a **TCP** port value. By default, the value is TCP 5068.
    
    > [!NOTE]
    > The TCP port value setting is enabled by selecting **Enable TCP port**. You should refer to the documentation for your Public Switched Telephone Network (PSTN) Gateway or Internet Protocol Private Branch Exchange (IP-PBX) for the requirements for the port settings required to communicate with the Mediation service. 
  
- You **Enable TCP port** to define the port value for TCP communications from your PSTN gateway or IP-PBX.
    
- A listing of currently associated and existing **Trunk** (that is, Session Initiation Protocol (SIP) Trunks), **Gateway** (PSTN gateway or IP-PBX) and **Site** (configured site for the trunk and gateway).
    
- You select a Trunk, Gateway and Site and click **Make Default** to set the selection as the default for this Mediation service. You select the current default and click **Unmake Default** to remove the selection as the current default. You then select a new default and click **Make Default**.
    
  **OK** Accepts and commits changes to the dialog.
  
  **Cancel** Discards changes and closes the dialog.
  
  **Help** Displays this help screen.
  

