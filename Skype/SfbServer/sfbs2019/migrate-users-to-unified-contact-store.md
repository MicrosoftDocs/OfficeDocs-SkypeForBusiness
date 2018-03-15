---
title: "Migrate users to unified contact store in Lync Server 2013"
ms.author: tonysmit
author: tonysmit
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 215a8ec1-d63e-4fdf-b73d-75aeb9dddb43
description: "A user's contacts are automatically migrated to the Exchange 2013 server when the user:"
---

# Migrate users to unified contact store in Lync Server 2013
[]
A user's contacts are automatically migrated to the Exchange 2013 server when the user:
  
- Has been assigned a user services policy that has UcsAllowed set to True.
    
- Has been provisioned with an Exchange 2013 mailbox and has signed into the mailbox at least once.
    
- Logs in by using a Lync 2013 rich client.
    
If the user logs in with a Lync 2010 or earlier client, or if the user is not connected to an Exchange 2013 server, the user services policy is ignored and the user's contacts remain in Lync Server.
  
You can determine whether a user's contacts have been migrated by using either of the following methods: 
  
- Check the following registry key on the client computer:
    
    HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\\<SIP URL\>\UCS
    
    If the user's contacts are stored in Exchange 2013, this key contains a value of InUCSMode with a value of 2165.
    
- Run the **Test-CsUnifiedContactStore** cmdlet. At the Lync Server Management Shell command line, type: 
    
  ```
  Test-CsUnifiedContactStore -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetFqdn "atl-cs-001.litwareinc.com"
  ```

    If **Test-CsUnifiedContactStore** succeeds, the user's contacts were migrated to unified contact store. 
    

