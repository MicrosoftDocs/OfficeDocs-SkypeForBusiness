---
title: "Remove an authorized host entry [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 56a04140-347e-4eef-bede-0e858534f71e
description: "This topic describes how to remove a legacy authorized host entry (known as a trusted application entry in Lync Server 2013). You must remove existing authorized host entries for any SIP/CSTA gateways in your Office Communications Server 2007 R2 deployment when you migrate remote call control to a Lync Server 2013 deployment. You must use the administrative tools included with Office Communications Server 2007 R2 to remove the existing authorized host entries."
---

# Remove an authorized host entry [OCS 2007 R2 to W15]
[]
This topic describes how to remove a legacy authorized host entry (known as a  *trusted application entry*  in Lync Server 2013). You must remove existing authorized host entries for any SIP/CSTA gateways in your Office Communications Server 2007 R2 deployment when you migrate remote call control to a Lync Server 2013 deployment. You must use the administrative tools included with Office Communications Server 2007 R2 to remove the existing authorized host entries. 
  
## To remove an authorized host entry in an Office Communications Server 2007 R2 deployment

1. Open the Office Communications Server 2007 R2 administrative console.
    
2. Expand the tree and right-click the pool where the authorized host was created.
    
3. Click **Properties**, and then click **Front End Properties**.
    
4. Click the **Host Authorization** tab. 
    
5. Select a server, and then click **Remove**.
    
6. In **Properties**, click **OK**.
    

