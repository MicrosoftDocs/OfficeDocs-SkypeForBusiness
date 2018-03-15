---
title: "Assign a per-user hosted voice mail policy in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d44c71a0-4407-4ab4-b7e0-d671dde3425f
description: "Deploying one or more per-user hosted voice mail policies is optional. If you do deploy per-user policies, you must explicitly assign them to users, groups, or contact objects."
---

# Assign a per-user hosted voice mail policy in Lync Server 2013
[]
Deploying one or more per-user hosted voice mail policies is optional. If you do deploy per-user policies, you must explicitly assign them to users, groups, or contact objects.
  
For details about assigning or removing the assignment of per-user hosted voice mail policies, see the Lync Server Management Shell documentation for the following cmdlets:
  
- Grant-CsHostedVoicemailPolicy
    
- Remove-CsHostedVoicemailPolicy
    
### To assign a per-user hosted voice mail policy

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the Grant-CsHostedVoicemailPolicy cmdlet to assign the per-user hosted voice mail policy to individual users, groups, and contact objects. For example, run:
    
  ```
  Grant-CsHostedVoicemailPolicy -Identity "Ken Myer" -PolicyName ExRedmond
  ```

    This example assigned the ExRedmond hosted voice mail policy to user Ken Myer.
    
    **Identity** specifies the user account to be modified. The Identity value can be specified using any of the following formats: 
    
  - The user's SIP address
    
  - The user's Active Directory User-Principal-Name
    
  - The user's domain\logon name (for example, contoso\kenmyer)
    
  - The user's Active Directory Domain Services Display-Name (for example, Ken Myer). If using the Display-Name as the Identity value, you can use the asterisk (\*) wildcard character. For example, the Identity "\* Smith" returns all the users who have a Display-Name that ends with the string value "Smith".
    
    > [!NOTE]
    > The user's Active Directory SAM-Account-Name cannot be used as the Identity value because the SAM-Account-Name is not necessarily unique in the forest. 
  

