---
title: "Move Exchange Unified Messaging Contact objects [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 35c7e987-41b5-4798-b617-3303f20e52e3
description: "To migrate Auto Attendant (AA) and Subscriber Access (SA) contact objects to the new Lync Server 2013 deployment, you first move the objects from the legacy Office Communications Server 2007 R2 deployment to the new the Lync Server 2013 deployment using the Get-CsExUmContact and Move-CsExUmContact cmdlets. On the Exchange Server, you then run the ExchUCUtil Windows PowerShell script to do the following for the newly deployed Lync pool:"
---

# Move Exchange Unified Messaging Contact objects [OCS 2007 R2 to W15]
[]
To migrate Auto Attendant (AA) and Subscriber Access (SA) contact objects to the new Lync Server 2013 deployment, you first move the objects from the legacy Office Communications Server 2007 R2 deployment to the new the Lync Server 2013 deployment using the **Get-CsExUmContact** and **Move-CsExUmContact** cmdlets. On the Exchange Server, you then run the **ExchUCUtil** Windows PowerShell script to do the following for the newly deployed Lync pool: 
  
- Add it to the Unified Messaging IP gateways.
    
- Add it to the Unified Messaging hunt groups.
    
> [!NOTE]
> In order to use the **Get-CsExUmContact** and **Move-CsExUmContact** cmdlets, you must be a member of the RTCUniversalUserAdmins group and have organizational unit (OU) permission to the OU where the contacts objects are stored. OU permission can be granted using the **Grant-OUPermission** cmdlet. 
  
### To move contact objects by using the Lync Server Management Shell

1. Open the Lync Server Management Shell.
    
2. For each pool registered with Exchange UM (where pool1.contoso.net is a pool from the Office Communications Server 2007 R2 deployment and pool2.contoso.net is the pool from the Lync Server 2013 deployment) at the command line, type the following: 
    
  ```
  Get-CsExUmContact -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsExUmContact -Target pool02.contoso.net
  ```

    To verify that the contact objects are moved, run the **Get-CsExumContact** cmdlet and confirm that **RegistrarPool** is now pointing to the new pool. 
    
### To run the ExchUCUtil Windows PowerShell script

1. Log on to the Exchange UM Server as a user with Exchange Organization Administrator privileges.
    
2. Navigate to the ExchUCUtil Windows PowerShell script.
    
    In Exchange 2007, ExchUCUtil.ps1 is located at: **%Program Files%\Microsoft\Exchange Server\Scripts\ExchUCUtil.ps1**
    
    In Exchange 2010, ExchUCUtil.ps1 is located at: **%Program Files%\Microsoft\Exchange Server\V14\Scripts\ExchUCUtil.ps1**
    
3. If Exchange is deployed in a single forest, type:
    
  ```
  exchucutil.ps1
  ```

    Or, if Exchange is deployed in multiple forests, type:
    
  ```
  exchucutil.ps1 -Forest:" <forest FQDN>"
  ```

    where  _forest FQDN_ specifies the forest in which Lync Server 2013 is deployed. 
    
    > [!IMPORTANT]
    > Be sure to restart the **Lync Server Front-End** service (rtcsrv.exe)  *after*  you run exchucutil.ps1. Otherwise, Lync Server 2013 will not detect Unified Messaging in the topology. 
  

