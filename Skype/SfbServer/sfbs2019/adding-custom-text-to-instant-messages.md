---
title: "Adding custom text to instant messages in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cabcc3ec-9d35-42ac-a403-e21b7d538c2c
description: "Add a disclaimer or warning to the beginning of every Lync 2013 instant messaging (IM) conversation by using the New-CSClientPolicy or Set-CSClientPolicy Lync Server Management Shell cmdlets with the IMWarning parameter."
---

# Adding custom text to instant messages in Lync Server 2013
[]
Add a disclaimer or warning to the beginning of every Lync 2013 instant messaging (IM) conversation by using the **New-CSClientPolicy** or **Set-CSClientPolicy** Lync Server Management Shell cmdlets with the IMWarning parameter. 
  
The command in the following example adds a security reminder at the top of the Conversation window whenever a new IM conversation begins:
  
```
New-CsClientPolicy -Identity IMSecurityNotice -IMWarning 
"Remember, security is everyone's responsibility. Keep it confidential."

```

Use **Grant-CSClientPolicy** to assign this new policy to users. For details, see **New-CSClientPolicy** and **Grant-CSClientPolicy** in the Lync Server Management Shell documentation. 
  

