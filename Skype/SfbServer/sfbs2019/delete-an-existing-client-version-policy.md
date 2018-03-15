---
title: "Delete an existing client version policy in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b88aaa25-97ff-4eb6-bd34-b97332cd6890
description: "If you want to delete a client version policy that was previously configured, you can delete it from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell."
---

# Delete an existing client version policy in Lync Server 2013
[]
If you want to delete a client version policy that was previously configured, you can delete it from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.
  
### To delete client version policies by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Client Version Policy** navigation button. 
    
4. On the **Client Version Policy** page, select the client version policy or policies you want to delete, click **Edit**, and then click **Delete**.
    
## Deleting Client Version Policies by Using Windows PowerShell Cmdlets

You can delete client version policies by using the **Remove-CsClientVersionPolicy** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To remove a specific client version policy

- This command deletes the client version policy applied to the Redmond site:
    
  ```
  Remove-CsClientVersionPolicy -Identity site:Redmond
  ```

### To remove all the client version policies applied to the site scope

- This command removes all the client version policies configured at the site scope:
    
  ```
  Get-CsClientVersionPolicy -Fiter "site:*" | Remove-CsClientVersionPolicy
  ```

### To remove client version policies that do not include a specific user agent

- And this command removes any client version policies that do not include a rule for the Windows Phone Lync (WPLync) user agent:
    
  ```
  Get-CsClientVersionPolicy | Where-Object {$_.Rules -notmatch "UserAgent=WPLync" | Remove-CsClientVersionPolicy
  ```

For details, see the Help topic for the [Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md) cmdlet. 
  

