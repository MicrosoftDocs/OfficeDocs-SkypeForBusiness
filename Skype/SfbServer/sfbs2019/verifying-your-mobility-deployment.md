---
title: "Verifying your mobility deployment in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 72f9b4d3-57b0-4705-9480-cfdca313a70c
description: "After you deploy the Lync Server Mobility Service and Lync Server Autodiscover Service, run a test transaction to verify that your deployment works correctly. You can run Test-CsUcwaConference to test the ability of two users who are using Lync 2013 Mobile clients to create, join and communicate in a conference. To use this test transaction, you need two actual users or test users, and their full credentials."
---

# Verifying your mobility deployment in Lync Server 2013
[]
```
Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.
```

After you deploy the Lync Server Mobility Service and Lync Server Autodiscover Service, run a test transaction to verify that your deployment works correctly. You can run **Test-CsUcwaConference** to test the ability of two users who are using Lync 2013 Mobile clients to create, join and communicate in a conference. To use this test transaction, you need two actual users or test users, and their full credentials. 
  
You use **Test-CsMcxP2PIM** to test sending an instant message between two users who are using Lync 2010 Mobile. Similar to **Test-CsUcwaConference**, you use two actual users or two predefined test users. 
  
### To test conferencing for Lync 2013 Mobile clients

1. Log on as a member of the CsAdministrator role on any computer where Lync Server Management Shell and Ocscore are installed.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. At the command line, type:
    
  ```
  Test-CsUcwaConference -TargetFqdn <FQDN of Front End pool> -Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID> -OrganizerSipAddress sip:<SIP address of test user 1> -OrganizerCredential <test user 1 credentials> -ParticipantSipAddress sip:<SIP address of test user 2> -ParticipantCredential <test user 2 credentials> -v
  ```

    You can set credentials in a script and pass them to the test cmdlet. For example:
    
  ```
  $passwd1 = ConvertTo-SecureString "Password01" -AsPlainText -Force
  $passwd2 = ConvertTo-SecureString "Password02" -AsPlainText -Force
  $testuser1 = New-Object Management.Automation.PSCredential("contoso\UserName1", $passwd1)
  $testuser2 = New-Object Management.Automation.PSCredential("contoso\UserName2", $passwd2)
  Test-CsUcwaConference -TargetFqdn pool01.contoso.com -Authentication Negotiate -OrganizerSipAddress sip:UserName1@contoso.com -OrganizerCredential $testuser1 -ParticipantSipAddress sip:UserName2@contoso.com -ParticipantCredential $testuser2 -v
  
  ```

### To test person-to-person instant messaging (IM) for Lync 2010 Mobile

1. Log on as a member of the CsAdministrator role on any computer where Lync Server Management Shell and Ocscore are installed.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. At the command line, type:
    
  ```
  Test-CsMcxP2PIM -TargetFqdn <FQDN of Front End pool> -Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID> -SenderSipAddress sip:<SIP address of test user 1> -SenderCredential <test user 1 credentials> -ReceiverSipAddress sip:<SIP address of test user 2> -ReceiverCredential <test user 2 credentials> -v
  ```

    You can set credentials in a script and pass them to the test cmdlet. For example:
    
  ```
  $passwd1 = ConvertTo-SecureString "Password01" -AsPlainText -Force
  $passwd2 = ConvertTo-SecureString "Password02" -AsPlainText -Force
  $tuc1 = New-Object Management.Automation.PSCredential("contoso\UserName1", $passwd1)
  $tuc2 = New-Object Management.Automation.PSCredential("contoso\UserName2", $passwd2)
  Test-CsMcxP2PIM -TargetFqdn pool01.contoso.com -Authentication Negotiate -SenderSipAddress sip:UserName1@contoso.com -SenderCredential $tuc1 -ReceiverSipAddress sip:UserName2@contoso.com -ReceiverCredential $tuc2 -v
  
  ```

## See also

#### 

[Test-CsMcxP2PIM](test-csmcxp2pim.md)
  
[Test-CsUcwaConference](test-csucwaconference.md)

