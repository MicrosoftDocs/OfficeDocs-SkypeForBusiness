---
title: "Granting permissions in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d1c9ea66-bd07-480e-99a0-011108f97e42
description: "For setup, you can grant permissions to the RTCUniversalServerAdmins universal group for a specific Active Directory organizational unit (OU), enabling members of the RTCUniversalServerAdmins group in that OU to install Lync Server 2013 in the specified domain. When you grant permissions for an OU, the following permissions are granted:"
---

# Granting permissions in Lync Server 2013
[]
For setup, you can grant permissions to the RTCUniversalServerAdmins universal group for a specific Active Directory organizational unit (OU), enabling members of the RTCUniversalServerAdmins group in that OU to install Lync Server 2013 in the specified domain. When you grant permissions for an OU, the following permissions are granted:
  
- Read
    
- Write
    
- ReadSPN
    
- WriteSPN
    
For administration, you can add permissions to specified OUs so that members of the RTC universal groups created by forest preparation can access the OUs without needing to be members of the Domain Admins group. The permissions added to the specified OU are the same permissions that the **Enable-CsAdDomain** cmdlet adds to the computers and users OU containers. 
  
## In This Section

- [Granting setup permissions in Lync Server 2013](granting-setup-permissions.md)
    
- [Granting organizational unit permissions in Lync Server 2013](granting-organizational-unit-permissions.md)
    

