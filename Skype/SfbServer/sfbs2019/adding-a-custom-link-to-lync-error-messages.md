---
title: "Adding a custom link to Lync error messages in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: de756088-fcc3-4e47-bde8-4fa4cc852fd1
description: "Customize Lync 2013 error messages by adding a link to your own troubleshooting or help desk information. To do this, use the New-CSClientPolicy or Set-CSClientPolicy Lync Server Management Shell cmdlets with the CustomLinkInErrorMessages parameter. The text of the custom link isClick here for support topics from your administrator,and it cannot be customized."
---

# Adding a custom link to Lync error messages in Lync Server 2013
[]
Customize Lync 2013 error messages by adding a link to your own troubleshooting or help desk information. To do this, use the **New-CSClientPolicy** or **Set-CSClientPolicy** Lync Server Management Shell cmdlets with the CustomLinkInErrorMessages parameter. The text of the custom link is "Click here for support topics from your administrator," and it cannot be customized. 
  
For example, the following command causes the custom link to appear in the footnote area of every Lync 2013 error message and sets the link destination to http://contoso.com/help/LyncHelpDesk.aspx: 
  
```
New-CsClientPolicy -Identity LyncErrorLink -CustomLinkInErrorMessages "http://contoso/help/LyncHelpDesk.aspx"

```

Use **Grant-CSClientPolicy** to assign this new policy to users. For details, see **New-CSClientPolicy** and **Grant-CSClientPolicy** in the Lync Server Management Shell documentation. 
  

