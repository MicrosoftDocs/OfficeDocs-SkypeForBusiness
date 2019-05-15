---
title: "Manage services in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Learn how to view service status, start and stop services, and prevent sessions for services."
---

# Manage services in Skype for Business Server

You can use the Skype for Business Server Control Panel to view a list of all the computers that are running Skype for Business Server in your topology, view the status of services, start or stop services, and prevent sessions for services.

- [View a list of computers running Skype for Business Server](#view-a-list-of-computers-running-skype-for-business-server)
- [View the status of services running on a computer in Skype for Business](#view-the-status-of-services-running-on-a-computer-in-skype-for-business)
- [Start or stop Skype for Business services](#start-or-stop-skype-for-business-services)
- [Prevent sessions for services](#prevent-sessions-for-services)

## View a list of computers running Skype for Business Server

Use the Skype for Business Server Control Panel to view a list of all the computers that are running Skype for Business in your topology and see the service status of each. You can sort the list by computer, pool, or site. 

1. From a user account that is assigned to any of the predefined administrative roles for Skype for Business Server, log on to any computer in your internal deployment. For more information, see [Role-based access control (RBAC) for Skype for Business Server](../../plan-your-deployment/security/role-based-access-control-rbac.md).
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. For details about the different methods you can use to start the Skype for Business Server Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. In the left navigation bar, click **Topology**, and then click **Status**.
4. On the Status page, do either of the following as needed:
    - Sort the list by clicking the **Computer**, **Pool**, or **Site** column heading, and then clicking the up arrow or the down arrow.
    - Click **Refresh** to view the most up-to-date list.
    - Search for a specific computer by typing the computer name in the search field.
   
## View the status of services running on a computer in Skype for Business

Use the Skype for Business Server Control Panel to view all the services that are running on a specific computer in your Skype for Business Server topology and see the status of each service.

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
2. Open a browser window, and then enter the Admin URL to open the Control Panel. For details about the different methods you can use to start the Skype for Business Server Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. In the left navigation bar, click **Topology**.
4. On the Status page, sort or search the list, as required, to find the computer you’re interested in, and then click the computer name.
5. Do either of the following:
    - To see the latest status of services running on the computer, click **Get service status**.
    - To see a list of specific services running on the computer and the status of each service, click **Properties**, and then click **Close** to return to the list.

### Viewing service status by using Windows PowerShell Cmdlets

You can also view service status by using Windows PowerShell and the Get-CsWindowsService cmdlet. You can run this cmdlet from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For more information, see [Skype for Business Server Management Shell](../management-shell.md).

**To view service status**

To view service status on a computer, type a command similar to the following in the Skype for Business Server Management Shell, and then press Enter:

`Get-CsWindowsService -ComputerName atl-cs-001.litwareinc.com | Select-Object RoleName, Status`

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

For details, see [Get-CsWindowsService](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsWindowsService).

## Start or stop Skype for Business services

Use the Skype for Business Server Control Panel to start or stop all the Skype for Business Server services running on a specific computer or to start or stop a specific service.

### Start or stop all Skype for Business Server services on a computer

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server. You can determine whether you have been assigned the CsServerAdministrator or the CsAdministrator RBAC role by running a command similar to the following:

    `Get-CsAdminRoleAssignment -Identity "kenmyer"`

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. For details about the different methods you can use to start the Skype for Business Server Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. In the left navigation bar, click **Topology**, and then click **Status**.
4. On the Status page, sort or search through the list as needed to find the computer that is running the services you want to start or stop, and then click it.
5. Click **Action**.
6. Click **Start All services** or **Stop All services**.

### Start or stop a specific service

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
2. Open a browser window, and then enter the Admin URL to open the Control Panel. For details about the different methods you can use to start the Skype for Business Server Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. In the left navigation bar, click **Topology**, and then click **Status**.
4. On the Status page, sort or search through the list as needed to find the computer that is running the service you want to start or stop, and then click it.
5. Click **Properties**.
6. Sort the list of services, if necessary, and click the service you want to start or stop.
7. Click **Action**.
8. Click **Start service** or **Stop service**.
9. Click **Close**.


## Prevent sessions for services

Use the Skype for Business Control Panel to prevent new sessions for all the Skype for Business Server services running on a specific computer or to prevent new sessions for a specific service.

### Prevent new sessions for all  Skype for Business Server services on a computer

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
2. Open a browser window, and then enter the Admin URL to open the Control Panel. For details about the different methods you can use to start the Skype for Business Server Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. In the left navigation bar, click **Topology** and then click **Status**.
4. On the Status page, sort or search through the list as needed to find the computer that is running the services for which you want to prevent new sessions, and then click it.
5. Click **Action**.
6. Click **Prevent new sessions for all services**.

### Prevent new sessions for a specific service

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
2. Open a browser window, and then enter the Admin URL to open the Control Panel. For details about the different methods you can use to start the Skype for Business Server Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. In the left navigation bar, click **Topology**, and then click **Status**.
4. Click **Properties**.
5. Sort the list of services, if necessary, and click the service for which you want to prevent new sessions.
6. Click **Action**.
7. Click **Prevent new sessions for service**.
8. Click **Close**.
