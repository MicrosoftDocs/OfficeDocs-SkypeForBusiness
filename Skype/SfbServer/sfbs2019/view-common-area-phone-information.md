---
title: "View common area phone information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e652240c-6a3f-4be7-a083-32f24c08e655
description: "You can view information about the common area phones configured for use in your organization by using the Get-CsCommonAreaPhone cmdlet. Used without any parameters, this cmdlet returns information about all your common area phones. Optional parameters provide different ways for you to filter information. For example, you can return all the common area phones that have contact objects in a specified organizational unit (OU) or all the contacts objects located in a specified building. For details about Get-CsCommonAreaPhone parameters, see Get-CsCommonAreaPhone."
---

# View common area phone information in Lync Server 2013
[]
You can view information about the common area phones configured for use in your organization by using the **Get-CsCommonAreaPhone** cmdlet. Used without any parameters, this cmdlet returns information about all your common area phones. Optional parameters provide different ways for you to filter information. For example, you can return all the common area phones that have contact objects in a specified organizational unit (OU) or all the contacts objects located in a specified building. For details about **Get-CsCommonAreaPhone** parameters, see [Get-CsCommonAreaPhone](get-cscommonareaphone.md).
  
Run **Get-CsCommonAreaPhone** either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. 
  
## 

### Viewing Information about All Your Common Area Phones

- To view information about all your common area phones, type the following command in the Lync Server Management Shell, and then press Enter:
    
  ```
  Get-CsCommonAreaPhone
  ```

    You'll get information similar to this:
    
  ```
  Identity           : CN=Building 14 Lobby,OU=Redmond,
                       DC=litwareinc,DC=com
  RegistrarPool      : atl-cs-001.litwareinc.com
  Enabled            : True
  SipAddress         : sip:4714e34b-9781-421d-b07a-
                       52056b5b4a56@litwareinc.com
  ClientPolicy       :
  PinPolicy          :
  VoicePolicy        :
  MobilityPolicy     :
  GroupChatPolicy    :
  ConferencingPolicy :
  LineURI            : tel:+14255550712
  DisplayNumber      : 1-425-555-0712
  DisplayName        : Building 14 Lobby
  Description        :
  ExUmEnabled        : False
  
  ```

For details, see the Help topic for the [Get-CsCommonAreaPhone](get-cscommonareaphone.md) cmdlet. 
  

