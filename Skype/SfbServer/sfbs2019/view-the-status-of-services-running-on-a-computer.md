---
title: "View the status of services running on a computer in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f41918e7-4c02-431e-840a-88a1f36ae499
description: "You can use Lync Server 2013 Control Panel to view all the services that are running on a specific computer in your Lync Server topology and see the status of each service."
---

# View the status of services running on a computer in Lync Server 2013
[]
You can use Lync Server 2013 Control Panel to view all the services that are running on a specific computer in your Lync Server topology and see the status of each service.
  
### To view the status of services running on a computer

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Topology**.
    
4. On the **Status** page, sort or search the list, as required, to find the computer you're interested in, and then click the computer name. 
    
5. Do any of the following:
    
  - To see the latest status of services running on the computer, click **Get service status**.
    
  - To see a list of specific services running on the computer and the status of each service, click **Properties**, and then click **Close** to return to the list. 
    
## Viewing Service Status by Using Windows PowerShell Cmdlets

You can also view service status by using Windows PowerShell and the **Get-CsWindowsService** cmdlet. You can run this cmdlet from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view service status

- To view service status on a computer, type a command similar to the following in the Lync Server Management Shell and then press Enter:
    
  ```
  Get-CsWindowsService -ComputerName atl-cs-001.litwareinc.com | Select-Object RoleName, Status
  ```

    This command returns information similar to the following:
    
  ```
  RoleName                                  Status
  --------                                  ------
  {W3SVC}                                   Running
  {CentralManagement}                       Running
  {ClsAgent}                                Running
  {Registrar, UserServer, EdgeServer}       Running
  {ApplicationServer}                       Running
  {ConferencingServer}                      Running
  {MediationServer}                         Running
  ```

For details, see [Get-CsWindowsService](get-cswindowsservice.md).
  
## See also

#### 

[Managing devices, phones, and client applications in Lync Server 2013](managing-devices-phones-and-client-applications.md)

