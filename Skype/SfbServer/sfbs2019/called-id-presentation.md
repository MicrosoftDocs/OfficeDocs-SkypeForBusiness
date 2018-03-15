---
title: "Called ID presentation in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cf6c6af5-3418-411e-a50b-7a9cf8e100d4
description: "With Lync Server 2010, the called party's phone number (that is, the phone number called) can be translated from E.164 format to the local dialing format that is required by the trunk peer (that is, the associated gateway, private branch exchange (PBX), or SIP trunk). To do this, you must define one or more translation rules to translate the Request URI before routing it to the trunk peer."
---

# Called ID presentation in Lync Server 2013
[]
With Lync Server 2010, the called party's phone number (that is, the phone number called) can be translated from E.164 format to the local dialing format that is required by the  _trunk peer_ (that is, the associated gateway, private branch exchange (PBX), or SIP trunk). To do this, you must define one or more translation rules to translate the Request URI before routing it to the trunk peer. 
  
> [!IMPORTANT]
> The ability to associate one or more translation rules with an Enterprise Voice trunk configuration is intended to be used as an  *alternative*  to configuring translation rules on the trunk peer. Do not associate translation rules with an Enterprise Voice trunk configuration if you have configured translation rules on the trunk peer because the two rules might conflict. 
  
You can use either of the following methods to create or modify a translation rule:
  
- Use the **Build a Translation Rule** tool to specify values for the starting digits, length, digits to remove and digits to add, and then let Lync Server Control Panel generate the corresponding matching pattern and translation rule for you. 
    
- Write regular expressions manually to define the matching pattern and translation rule.
    
> [!NOTE]
> For information about how to write regular expressions, see ".NET Framework Regular Expressions" at [https://go.microsoft.com/fwlink/p/?linkId=140927](https://go.microsoft.com/fwlink/p/?linkId=140927). 
  
## In this section

- [Create or modify a translation rule by using the Build a Translation Rule tool in Lync Server 2013](create-or-modify-a-translation-rule-by-using-the-build-a-translation-rule-tool.md)
    
- [Create or modify a translation rule manually in Lync Server 2013](create-or-modify-a-translation-rule-manually.md)
    
## See also

#### 

[Caller ID presentation in Lync Server 2013](caller-id-presentation.md)

