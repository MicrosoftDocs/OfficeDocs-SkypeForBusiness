---
title: "Registrar Settings Expander for Lync Server for 2010"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.RegistrarSettingsExpander2010
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 17dcd75c-bd9a-407e-af9b-c61cb1201c07
description: "You edit the settings for Resiliency and configure the following properties:"
---

# Registrar Settings Expander for Lync Server for 2010
 
You edit the settings for **Resiliency** and configure the following properties:
  
- Select **Associated backup Registrar pool** from the list.
    
    Optionally, select the **Automatic failover and failback for Voice** check box.
    
    Configure the **Voice failure detection interval (sec)** and the **Voice failback interval (sec)**. By default, the intervals are 120 seconds for Voice failure detection and 240 seconds for Voice failback.
    
    > [!CAUTION]
    > The number of seconds that you define for the failover and failback intervals should be carefully tested to ensure that the resiliency works as expected. Setting the interval to low (that is, less than 120 seconds) or the failover and failback set too closely may result in the actual failover and failback not working as expected. 
  
  **OK** Accepts and commits changes to the dialog.
  
  **Cancel** Discards changes and closes the dialog.
  
  **Help** Displays this help screen.
  

