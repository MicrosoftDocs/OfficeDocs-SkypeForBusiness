---
title: "Create or modify a common area phone Contact object in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: eec33ad1-e4f2-49b2-91d6-d5a9d2e1714b
description: "To create Active Directory Domain Services contact objects for all your common area phones, use the New-CsCommonAreaPhone cmdlet. This cmdlet can either create new contact objects for use with common area phones, or it can associate existing contact objects with a new common area phone. To modify the properties of the contact objects associated with common area phones, use the Set-CsCommonAreaPhone cmdlet. Optional parameters for Set-CsCommonAreaPhone enable you to change items, such as the contact's Active Directory display name or the line Uniform Resource Identifier (URI) associated with the phone, and enable and disable the account for use with Lync Server. For details about all the available modifications, see the Parameters section at Set-CsCommonAreaPhone. For details about New-CsCommonAreaPhone parameters, see New-CsCommonAreaPhone."
---

# Create or modify a common area phone Contact object in Lync Server 2013
[]
To create Active Directory Domain Services contact objects for all your common area phones, use the **New-CsCommonAreaPhone** cmdlet. This cmdlet can either create new contact objects for use with common area phones, or it can associate existing contact objects with a new common area phone. To modify the properties of the contact objects associated with common area phones, use the **Set-CsCommonAreaPhone** cmdlet. Optional parameters for **Set-CsCommonAreaPhone** enable you to change items, such as the contact's Active Directory display name or the line Uniform Resource Identifier (URI) associated with the phone, and enable and disable the account for use with Lync Server. For details about all the available modifications, see the Parameters section at [Set-CsCommonAreaPhone](set-cscommonareaphone.md). For details about **New-CsCommonAreaPhone** parameters, see [New-CsCommonAreaPhone](new-cscommonareaphone.md).
  
You can run these two cmdlets from either the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
## 

### Creating a common area phone contact object

- To create a new common area phone contact object, use the **New-CsCommonAreaPhone** cmdlet. At a minimum, you must supply the following information when creating a contact object: 
    
  - **LineUri**: The telephone number assigned to the common area phone. Note that you must use the E.164 format when specifying the phone number. 
    
  - **RegistrarPool**: The fully qualified domain name (FQDN) of the Registrar pool that will host the contact object. 
    
  - **OU**: Distinguished name of the Active Directory container where the contact object will be created. 
    
    We also recommend that you provide an Active Directory Domain Services display name. Otherwise, you will need to use a GUID to specify the phone Identity. For example:
    
  ```
  New-CsCommonAreaPhone -LineUri "tel:+12065551219" -RegistrarPool "atl-cs-001.litwareinc.com" -OU "OU=Phones,dc=litwareinc,dc=com" -DisplayName "Lobby"
  ```

### Modifying a common area phone contact object

- To modify the properties of an existing common area phone, contact object use the **Set-CsCommonAreaPhone** cmdlet. For example, this command configures the SIP address for the common area phone with the DisplayName Lobby: 
    
  ```
  Set-CsCommonAreaPhone -Identity "Lobby" -SipAddress "sip:lobby@litwareinc.com"
  ```

For details, see the Help topics for the [New-CsCommonAreaPhone](new-cscommonareaphone.md) cmdlet and the [Set-CsCommonAreaPhone](set-cscommonareaphone.md) cmdlet. 
  

