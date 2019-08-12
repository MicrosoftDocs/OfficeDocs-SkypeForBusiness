---
title: "Manage services for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c99ee134-8294-4481-bb4e-710fe85a39ca
description: "This article describes how to manage services running in a Skype for Business Server topology."
---

# Manage services for Skype for Business Server

This article describes how to manage services running in a Skype for Business Server topology.
  
## View a list of computers running Skype for Business Server
<a name="view_list"> </a>

You can use Skype for Business Server Control Panel to view a list of all the computers that are running Skype for Business Server in your topology and see the service status of each. You can sort the list by computer, pool, or site. 
  
### To view a list of computers running Skype for Business Server

1. From a user account that is assigned to any of the predefined administrative roles for Skype for Business Server, log on to any computer in your internal deployment. For details about the predefined administrative roles available in Skype for Business Server, see **Planning for Role-Based Access Control**.   
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.   
3. In the left navigation bar, click **Topology** and then click **Status**.   
4. On the **Status** page, do any of the following as needed:
   - Sort the list by clicking the **Computer**, **Pool**, or **Site** column heading, and then clicking the up arrow or the down arrow. 
   - Click **Refresh** to view the most up-to-date list.  
   - Search for a specific computer by typing the computer name in the search field.
    
## View the status of services running on a Skype for Business server
<a name="view-status"> </a>

You can use Skype for Business Server Control Panel to view all the services that are running on a specific computer in your Skype for Business Server topology and see the status of each service.
  
### To view the status of services running on a computer

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
3. In the left navigation bar, click **Topology**. 
4. On the **Status** page, sort or search the list, as required, to find the computer you're interested in, and then click the computer name.
5. Do any of the following:
   - To see the latest status of services running on the computer, click **Get service status**.
   - To see a list of specific services running on the computer and the status of each service, click **Properties**, and then click **Close** to return to the list.
    
### Viewing service status with Windows Powershell cmdlets

You can also view service status by using Windows PowerShell and the **Get-CsWindowsService** cmdlet. You can run this cmdlet from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To view service status

To view service status on a computer, type a command similar to the following in the Skype for Business Server Management Shell and then press Enter:
  
```
Get-CsWindowsService -ComputerName atl-cs-001.litwareinc.com | Select-Object RoleName, Status
```

This command returns information similar to the following:
  
|**RoleName**|**Status**|
|:-----|:-----|
|{W3SVC}  <br/> |Running  <br/> |
|{CentralManagement}  <br/> | Running <br/> |
|{ClsAgent}  <br/> |Running  <br/> |
|{Registrar, UserServer, EdgeServer}  <br/> |Running  <br/> |
|{ApplicationServer}  <br/> |Running  <br/> |
|{ConferencingServer}  <br/> |Running  <br/> |
|{MediationServer}  <br/> |Running  <br/> |
   
For details, see [Get-CsWindowsService](https://docs.microsoft.com/powershell/module/skype/get-cswindowsservice.md?view=skype-ps).
  
## View details about a service
<a name="view_details"> </a>

You can use Skype for Business Server Control Panel to view details about each service that is running on a specific computer in your topology. You can view the status of each service and details such as the associated databases, ports, and dependent services.
  
### To view details for a service

1. From a user account that is assigned to any of the predefined administrative roles for Skype for Business Server, log on to any computer in your internal deployment. For details about the predefined administrative roles available in Skype for Business Server, see **Planning for Role-Based Access Control**.
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
3. In the left navigation bar, click **Topology** and then click **Status**.
4. In the **Status** page, sort or search through the list and then click the computer that you want to view.
5. Click **Properties**.
6. In the **View Computer Detail** window, sort the list of services, if necessary, and click the service you want to view.
7. Do any of the following as needed:
   - To see the latest status of that specific service, click **Get service status**.
   - To see the details for that specific service, click **Properties** and then click **Close**.
   - To return to the list of all computers in your topology, click **Close**.
    
## Start or stop Skype for Business Server services
<a name="StartStop"> </a>

You can use Skype for Business Server Control Panel to start or stop all the Skype for Business Server services running on a specific computer or to start or stop a specific service.
  
### To start or stop all Skype for Business services on a computer

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server. You can determine whether you have been assigned the CsServerAdministrator or the CsAdministrator RBAC role by running a command similar to the following:
    
   ```
   Get-CsAdminRoleAssignment -Identity "kenmyer"
   ```

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
3. In the left navigation bar, click **Topology** and then click **Status**.
4. On the **Status** page, sort or search through the list as needed to find the computer that is running the services you want to start or stop, and then click it.
5. Click **Action**.
6. Click **Start All services** or **Stop All services**.
    
### To start or stop a specific service

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
3. In the left navigation bar, click **Topology** and then click **Status**.
4. On the **Status** page, sort or search through the list as needed to find the computer that is running the service you want to start or stop, and then click it.
5. Click **Properties**.
6. Sort the list of services, if necessary, and click the service you want to start or stop.
7. Click **Action**.
8. Click **Start service** or **Stop service**.
9. Click **Close**.
    
## Prevent sessions for services
<a name="prevent_session"> </a>

You can use Skype for Business Server Control Panel to prevent new sessions for all the Skype for Business Server services running on a specific computer or to prevent new sessions for a specific Skype for Business Server service.
  
### To prevent new sessions for all Skype for Business services on a computer

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
3. In the left navigation bar, click **Topology** and then click **Status**.
4. On the **Status** page, sort or search through the list as needed to find the computer that is running the services for which you want to prevent new sessions, and then click it.
5. Click **Action**.
6. Click **Prevent new sessions for all services**.
    
### To prevent new sessions for a specific service

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
3. In the left navigation bar, click **Topology** and then click **Status**.
4. On the **Status** page, sort or search through the list as needed to find the computer that is running the service you want to start or stop, and then click it. 
5. Click **Properties**.
6. Sort the list of services, if necessary, and click the service for which you want to prevent new sessions.
7. Click **Action**.
8. Click **Prevent new sessions for service**.
9. Click **Close**.
    

