---
title: "Delete existing Registrar configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ae43cd75-cae4-4f78-b037-779a2cdb583b
description: "Follow these steps to delete a Registrar."
---

# Delete existing Registrar configuration settings in Lync Server 2013
[]
Follow these steps to delete a Registrar.
  
### To delete Registrar configuration settings

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Security** and then click **Registrar**.
    
4. On the **Registrar** page, and in the search field, type all or part of the name of the Registrar you want to delete. 
    
5. In the list, click the Registrar that you want, click **Edit**, and then click **Delete**.
    
6. Click **OK**.
    
## Removing Registrar Configuration Settings by Using Windows PowerShell Cmdlets

You can delete the Registrar configuration settings by using Windows PowerShell and the **Remove-CsProxyConfiguration** cmdlet. You can run this cmdlet from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To remove a specific set of Registrar security settings

- The following command removes the Registrar security settings applied to the edge Server atl-edge-011.litwareinc.com:
    
  ```
  Remove-CsProxyConfiguration -Identity service:EdgeServer:atl-edge-011.litwareinc.com
  ```

### To remove all of the Registrar security settings applied to the site scope

- The following command removes all the Registrar security settings applied to the Registrar service:
    
  ```
  Get-CsProxyConfiguration -Filter "service:Registrar:*" | Remove-CsProxyConfiguration
  ```

### To remove all of the Registrar security settings that allow NTLM authentication

- The following command deletes all the Registrar security settings that allow the use of NTLM for client authentication:
    
  ```
  Get-CsProxyConfiguration | Where-Object {$_.UseNtlmForClientToProxyAuth -eq $True}| Remove-CsProxyConfiguration
  ```

For details, see [Remove-CsProxyConfiguration](remove-csproxyconfiguration.md).
  

