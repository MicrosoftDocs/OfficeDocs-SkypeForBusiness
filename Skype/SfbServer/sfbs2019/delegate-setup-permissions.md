---
title: "Delegate setup permissions in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9dca1683-4c69-4534-8ebe-6bd635cbae49
description: "If you do not want to grant membership in the Domain Admins group to users or groups who are deploying Lync Server 2013, you can enable members of the RTCUniversalServerAdmins group to run the Enable-CsTopology Windows PowerShell cmdlet on servers running Lync Server 2013. By default, members of the RTCUniversalServerAdmins group do not have the ability to run this cmdlet. You grant administrator rights and permissions to run Enable-CsTopology on servers running Lync Server by using the Grant-CsSetupPermission cmdlet and specifying an organizational unit (OU) where computer objects for the server running Lync Server 2013 are located."
---

# Delegate setup permissions in Lync Server 2013
[]
If you do not want to grant membership in the Domain Admins group to users or groups who are deploying Lync Server 2013, you can enable members of the RTCUniversalServerAdmins group to run the **Enable-CsTopology** Windows PowerShell cmdlet on servers running Lync Server 2013. By default, members of the RTCUniversalServerAdmins group do not have the ability to run this cmdlet. You grant administrator rights and permissions to run **Enable-CsTopology** on servers running Lync Server by using the **Grant-CsSetupPermission** cmdlet and specifying an organizational unit (OU) where computer objects for the server running Lync Server 2013 are located. 
  
The domain preparation that takes place when you install Lync Server does not automatically add the permissions that enable members of the RTCUniversalServerAdmins group to run the Enable-CsTopology cmdlet. That means that, by default, you must be a domain administrator in order to enable a topology. To give members of the RTCUniversalServerAdmins group the right to enable a topology you must run the Grant-CsSetupPermissions cmdlet. In addition, you will need to run this cmdlet against each Active Directory container that houses computers running Lync Server.
  
Keep in mind that this cmdlet only grants permissions to the RTCUniversalServerAdmins group; the cmdlet cannot be used to grant permissions to other security groups or to individual users.
  
> [!NOTE]
> **Enable-CsTopology** is the key cmdlet to allow the RTCUniversalServerAdmins group members to set up and deploy Lync Server 2013. 
  
### To add the ability to run Enable-CsTopology to the RTCUniversalServerAdmins group

1. Log on to a server as a member of the Domain Admins group for the domain on which the delegated user will run **Enable-CsTopology**. 
    
2. Open the Lync Server 2013 Management Shell. The Lync Server 2013 Management Shell is automatically installed on each Front End Server or any computer where the Lync Server 2013 administrative tools have been installed. For details about the Lync Server 2013 Management Shell, see [Lync Server 2013 Management Shell](lync-server-management-shell.md) in the Operations documentation. 
    
3. Run the following cmdlet from the Lync Server 2013 Management Shell:
    
  ```
  Grant-CsSetupPermission -ComputerOU <DN of the OU> -Domain <Domain FQDN>
  ```

    > [!NOTE]
    > If the OU is not top level, you must provide the full domain name. 
  
    In the following example, the OU is "Lync Servers," which is in the contoso.com domain. 
    
  ```
  Grant-CsSetupPermission -ComputerOU "OU=Lync Servers" -Domain contoso.com
  ```


