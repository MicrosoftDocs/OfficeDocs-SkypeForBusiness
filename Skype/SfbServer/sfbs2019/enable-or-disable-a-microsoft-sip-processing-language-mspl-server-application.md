---
title: "Enable or disable a Microsoft SIP Processing Language (MSPL) server application in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b20af38d-224a-4459-991d-0b7eabb3ca7c
description: "You can use Lync Server Control Panel to enable or disable Microsoft SIP Processing Language (MSPL) server applications that run in your Lync Server 2013 environment. These applications are script-only applications that use a scripting language instead of the Microsoft Lync 2013 Preview API."
---

# Enable or disable a Microsoft SIP Processing Language (MSPL) server application in Lync Server 2013
[]
You can use Lync Server Control Panel to enable or disable Microsoft SIP Processing Language (MSPL) server applications that run in your Lync Server 2013 environment. These applications are script-only applications that use a scripting language instead of the Microsoft Lync 2013 Preview API. 
  
Not all scripts can be enabled or disabled. For instance, the DefaultRouting script is enabled and this option cannot be changed for DefaultRouting.
  
### To enable or disable an MSPL server application

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Topology** and then click **Server Application**.
    
4. On the **Server Application** page, click a column heading to sort the applications, if needed, and then click the server application that you want to modify. 
    
5. Click **Action**.
    
6. Click **Enable application** or **Disable application** (that is, if the script supports this option). 
    
## See also

#### 

[Mark a Microsoft SIP Processing Language (MSPL) application as critical or not critical in Lync Server 2013](mark-a-microsoft-sip-processing-language-mspl-application-as-critical-or-not-cri.md)
#### 

[View Microsoft SIP Processing Language (MSPL) server applications in Lync Server 2013](view-microsoft-sip-processing-language-mspl-server-applications.md)
#### 

[Managing the Lync Server 2013 topology](managing-the-lync-server-2013-topology.md)

