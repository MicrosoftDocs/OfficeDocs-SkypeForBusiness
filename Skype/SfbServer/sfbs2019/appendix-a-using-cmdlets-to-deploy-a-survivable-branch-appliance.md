---
title: "Appendix A Using cmdlets to deploy a Survivable Branch Appliance in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 796a26cf-7ec9-453b-8757-6153a6dd86c5
description: "This topic describes how to deploy a Survivable Branch Appliance using the Lync Server Management Shell. Perform this procedure at the central site."
---

# Appendix A: Using cmdlets to deploy a Survivable Branch Appliance in Lync Server 2013
[]
This topic describes how to deploy a Survivable Branch Appliance using the Lync Server Management Shell. Perform this procedure at the central site.
  
### To deploy a Survivable Branch Appliance remotely

1. Follow the procedure in [Add branch sites to your topology in Lync Server 2013](add-branch-sites-to-your-topology.md) to add a new branch site. 
    
2. Join the branch site to the domain.
    
3. Add the RTCUniversalSBATechnicians group to the local Administrators group.
    
4. Restart the server, and log on to it as a member of the RTCUniversalSBATechnicians group.
    
5. In the Lync Server Management Shell, type the following commands, replacing the placeholders with the correct information for your organization:
    
  ```
  Export-CsConfiguration -FileName C:\CSConfig.zip
  Import-CsConfiguration -LocalStore -FileName C:\CSConfig.zip -Verbose
  Enable-CSReplica -Verbose
  Enable-CsComputer -Verbose
  Request-CsCertificate -New -Type default -CA <YourCA> -Verbose
  Set-CsCertificate -Type Default -Thumbprint <YourCertThumbprint>
  Start-cswindowsservice -verbose
  
  ```


