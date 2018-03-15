---
title: "Certificate Request (Specify Termplate)"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.dep.DeployCertRequestTemplate
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d00ed98f-46f2-4367-b34c-513e5eafdd06
description: "The Specify Alternate Certificate Template page enables you to define a certificate template other than the WebServer certificate template that is used by default. Select the check box Use alternate certificate template for selected certification authority, and then define the name of the alternate certificate template in the text box Certificate template name. You must use the name of the template as it is defined in the certification authority (CA). Click Back to go back to the previous page. Click Cancel to end the certificate request process."
---

# Certificate Request (Specify Termplate)
[]
The **Specify Alternate Certificate Template** page enables you to define a certificate template other than the WebServer certificate template that is used by default. Select the check box **Use alternate certificate template for selected certification authority**, and then define the name of the alternate certificate template in the text box **Certificate template name**. You must use the name of the template as it is defined in the certification authority (CA). Click **Back** to go back to the previous page. Click **Cancel** to end the certificate request process. 
  
> [!CAUTION]
> You should use this option only if you are advised by your public CA that you should use a specific template that is defined on their system for issuing certificates. If the certificate is being issued by your internal CA, your CA administrator should advise you what name to use for the alternate certificate template. This option is extremely valuable in cases where your organization has defined a new WebServer template and has disabled the default WebServer template. 
  
![Specify Alternate Certificate Template dialog box](media/Step_6_SE_Cert.jpg)
  

