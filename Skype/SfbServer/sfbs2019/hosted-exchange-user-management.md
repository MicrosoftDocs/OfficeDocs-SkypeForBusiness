---
title: "Hosted Exchange user management in Lync Server 2013"
ms.author: tonysmit
author: tonysmit
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e8723af5-0604-4d7d-bad2-463a9832efb4
description: "To provide voice mail services for Lync Server 2013 users whose mailboxes are located on a hosted Exchange service, you must enable their user accounts for hosted voice mail."
---

# Hosted Exchange user management in Lync Server 2013
[]
To provide voice mail services for Lync Server 2013 users whose mailboxes are located on a hosted Exchange service, you must enable their user accounts for hosted voice mail.
  
> [!NOTE]
> Before a Lync Server 2013 user can be enabled for hosted voice mail, a hosted voice mail policy that applies to the corresponding user account must be deployed. The policy can be global, site, or per-user in scope, as long as it applies to the user whom you want to enable. For details, see [Hosted voice mail policies in Lync Server 2013](hosted-voice-mail-policies.md). 
  
## The msExchUCVoiceMailSettings Attribute

Lync Server 2013 introduces a new user attribute named **msExchUCVoiceMailSettings**, which is created as part of the Lync Server 2013 Active Directory schema preparation. This multivalued attribute holds voice mail settings that are shared by Lync Server 2013 and the hosted Exchange service.
  
The hosted Exchange service may in some cases set the value of the msExchUCVoiceMailSettings attribute in the process of enabling Exchange UM, or during the process of transferring mailboxes to a hosted Exchange Server. If this attribute is not set by Exchange, the Lync Server 2013 administrator must set it by running the Set-CsUser cmdlet, as described earlier in this topic.
  
The attribute's key/value pairs and their authors are shown in the following table.
  
**The msExchUCVoiceMailSettings Attribute Key/Value Pairs**

|**Value**|**Author**|**Meaning**|
|:-----|:-----|:-----|
|ExchangeHostedVoiceMail=1  <br/> |Exchange  <br/> |User has been enabled for hosted UM access by Exchange Server. The Exchange UM Routing application will check the user's hosted voice mail policy for routing details.  <br/> |
|ExchangeHostedVoiceMail=0  <br/> |Exchange  <br/> |User has been disabled for hosted UM access by Exchange Server.  <br/> |
|CsHostedVoiceMail=1  <br/> |Lync Server  <br/> |User has been enabled for hosted UM access by Lync Server 2013. The Lync Server 2013 ExUM Routing application will check the user's hosted voice mail policy for routing details.  <br/> |
|CsHostedVoiceMail=0  <br/> |Lync Server  <br/> |User has been disabled for hosted UM access by Lync Server 2013.  <br/> |
   
> [!NOTE]
> If the attribute already has values other than one of the Lync Server 2013 key/value pairs (CSHostedVoiceMail=0 or CSHostedVoiceMail=1), a warning will indicate that the attribute may be managed by a different application. For example, a warning is displayed if the key/value pair ExchangeHostedVoiceMail=0 or ExchangeHostedVoiceMail=1 is already present. In that case, you can change the value by editing it the Active Directory, or run the following cmdlet to set the value to null: > Set-CsUser -identity user -HostedVoicemail $null 
  
## Enabling Users for Hosted Voice Mail

To enable a user's voice mail calls to be routed to hosted Exchange UM, you must run the Set-CsUser cmdlet to set the value of the HostedVoiceMail parameter. This parameter also signals Lync Server 2013 to light up the "call voice mail" indicator. 
  
- The following example enables Pilar Ackerman's user account for hosted voice mail:
    
  ```
  Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $True
  ```

    The cmdlet verifies that a hosted voice mail policy (global, site-level or per-user) applies to this user. If no policy applies, the cmdlet fails.
    
- The following example disables Pilar Ackerman's user account for hosted voice mail:
    
  ```
  Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $False
  ```

    The cmdlet verifies that no hosted voice mail policy (global, site-level or per-user) applies to this user. If a policy does apply, the cmdlet fails.
    
For details about using the Set-CsUser cmdlet, see the Lync Server Management Shell documentation.
  

