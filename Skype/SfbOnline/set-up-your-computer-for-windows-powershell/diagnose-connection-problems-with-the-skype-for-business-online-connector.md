---
title: "Diagnose connection problems in the Skype for Business Online Connector"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: 866fadfd-16e2-4134-95db-c6aed7678416
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.custom:
- PowerShell
description: "Troubleshoot creation of a remote PowerShell session to connect to Skype for Business Online, including Import-Module, concurrent shell, Live ID, and permission errors."
---

# Diagnose connection problems in the Skype for Business Online Connector

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

This topic provides information that will help you diagnose and resolve problems that can occur when you try to create a remote Microsoft PowerShell session that connects to Skype for Business Online. See the following sections:
  
- [Import-Module error caused by Windows PowerShell execution policy](diagnose-connection-problems-with-the-skype-for-business-online-connector.md#BKMKPowerShellExecutionPolicy)
    
- [Import-Module Error caused by incorrect version of Windows PowerShell](diagnose-connection-problems-with-the-skype-for-business-online-connector.md#BKMKIncorrectVersion)
    
- [Failed to connect to Live ID Server](diagnose-connection-problems-with-the-skype-for-business-online-connector.md#BKMKFailedConnect)
    
- [Failed to load Live ID module](diagnose-connection-problems-with-the-skype-for-business-online-connector.md#BKMKFailedLoad)
    
- [Logon failed for the user](diagnose-connection-problems-with-the-skype-for-business-online-connector.md#BKMKLogonFailed)
    
- [The user does not have permission to manage this tenant](diagnose-connection-problems-with-the-skype-for-business-online-connector.md#BKMKUserPermission)
    
- [Ability to connect to tenant has been disabled in Skype for Business Online](diagnose-connection-problems-with-the-skype-for-business-online-connector.md#BKMKAbilityConnect)

- [The maximum number of concurrent shells for this user in Skype for Business Online has been exceeded](#the-maximum-number-of-concurrent-shells-for-this-user-in-skype-for-business-online-has-been-exceeded)

- [The maximum number of concurrent shells for this tenant in Skype for Business Online has been exceeded](#the-maximum-number-of-concurrent-shells-for-this-tenant-in-skype-for-business-online-has-been-exceeded)

    
## Import-Module error caused by Windows PowerShell execution policy
<a name="BKMKPowerShellExecutionPolicy"> </a>

The PowerShell execution policy helps to determine which configuration files can be loaded into the PowerShell console, and which scripts a user can run from that console. At a minimum, you can't import the Skype for Business Online Connector module unless the execution policy has been set to RemoteSigned. If it hasn't, you'll get the following error message when you attempt to import the module:
  
- **Error**: <em>Import-Module : File C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\Modules\\LyncOnlineConnector\\LyncOnlineConnectorStartup.psm1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.</em>

- **Resolution**: To resolve this issue, start PowerShell as an administrator, and then run the following command:
    ```PowerShell
    Set-ExecutionPolicy RemoteSigned
    ```
    For details about execution policy, see [About Execution Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).
  
## Import-Module Error caused by incorrect version of Windows PowerShell
<a name="BKMKIncorrectVersion"> </a>

The Skype for Business Online Connector module can be run only under Windows PowerShell 3.0. If you try to import the module under a previous version of PowerShell, the import process will fail with an error message similar to this one:
  
  - **Error**: *Import-Module : The version of the loaded PowerShell is '2.0'. The module 'D:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\Modules\\LyncOnlineConnector\\LyncOnlineConnector.psd1' requires a minimum PowerShell version of '3.0' to execute. Please verify the installation of the PowerShell and try again.*

- **Resolution**: The only way to fix this problem is to install Windows PowerShell 3.0, which is available from the Microsoft Download Center at [https://www.microsoft.com/download/details.aspx?id=34595](https://www.microsoft.com/download/details.aspx?id=34595).
  
## Failed to connect to Live ID Server
<a name="BKMKFailedConnect"> </a>

There are typically three reasons why your connection attempt might fail with the following error message:

  - **Error**: *Get-CsWebTicket : Failed to connect live id servers. Make sure proxy is enabled or machine has network connection to live id servers.*

- **Resolution**: Often this error means that the Microsoft Online Services Sign-in Assistant isn't running. You can verify the status of this service by running the following command from the PowerShell prompt: 
    ```PowerShell
    Get-Service "msoidsvc"
    ```
    If the service isn't running, start the service by using this command:
    ```PowerShell
    Start-Service "msoidsvc"
    ```

    If the service is running, you might be encountering problems with the network connection between your computer and the Microsoft Live ID Authentication Server. To check this, open Internet Explorer and navigate to [https://login.microsoftonline.com/.](https://login.microsoftonline.com/.) Try logging on to Microsoft 365 or Office 365 from there. If you can't, you're probably experiencing network connection issues.
  
    Less commonly, it's possible that the Connection URI for Microsoft Live ID Authentication Server has been configured to the wrong value. If you've already determined that the Sign-In Assistant is running and that you're not experiencing network issues, this configuration might be the problem. In this case, contact Microsoft Support.
  
## Failed to load Live ID module
<a name="BKMKFailedLoad"> </a>

One of the prerequisites for using PowerShell to manage Skype for Business Online is to install the Microsoft Online Services Sign-in Assistant. If the Sign-in Assistant isn't installed, you will receive the following error message when you try to establish a remote session with Skype for Business Online:

- **Error**: *Get-CsWebTicket : Can not load Live Id module. Make sure correct version of Live Id Sign-in assistant is installed.*

- **Resolution**: The Microsoft Online Services Sign-in Assistant is available in the Microsoft Download Center at Microsoft Online Services Sign-In Assistant for IT Professionals RTW.

## Logon failed for the user
<a name="BKMKLogonFailed"> </a>

When you attempt to make a remote connection to Skype for Business Online, you must supply the user name and password of a valid Skype for Business Online user account. If you do not, logon will fail along with an error message similar to this one:

- **Error**: *Get-CsWebTicket : Logon failed for the user 'kenmyer@litwareinc.com'. Please create a new PSCredential object, making sure that you have used the correct user name and password.*

- **Resolution**: If you think that you're using a valid user account and that you have the correct password, try logging on again. If that fails, use the same credentials and try to log on at [https://login.microsoftonline.com/](https://login.microsoftonline.com/). If you can't log on there, contact Microsoft Support. 

  
## The user doesn't have permission to manage this tenant
<a name="BKMKUserPermission"> </a>

You cannot make a remote PowerShell connection toSkype for Business Online unless you're a member of the Tenant Administrators group. If you're not, your connection attempt will fail, and you'll receive the following error message:

- **Error**: *New-PSSession : [admin.vdomain.com] Processing data from remote server admin.vdomain.com failed with the following error message: The user 'user@foo.com' does not have permission to manage this tenant. Permissions can be granted by assigning the user to the appropriate RBAC role. For more information, see the [Remote Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting).*

- **Resolution**: If you think that you are, or are supposed to be, a member of the Tenant Administrators group, contact Microsoft Support.
  
## Ability to connect to tenant has been disabled in Skype for Business Online
<a name="BKMKAbilityConnect"> </a>

To use PowerShell to manage Skype for Business Online, the EnableRemotePowerShellAccess property of your tenant PowerShell policy must be set to  `True`. If it's not, your connection will fail, and you'll receive the following error message:

- **Error**: *New-PSSession : [admin.vdomain.com] Processing data from remote server admin.vdomain.com failed with the following error message: The ability to connect to this tenant by using a remote PowerShell session has been disabled. Please contact Lync Help to check Tenant Powershell Policy of this tenant. For more information, see the [Remote Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting).*

- **Resolution**: If you see this error message, you'll need to contact Microsoft Support and get remote PowerShell access enabled.
  
## The maximum number of concurrent shells for this user in Skype for Business Online has been exceeded
<a name="BKMKMaxNumberShellsUser"> </a>

Each administrator is allowed a maximum of three simultaneous remote connections to Skype for Business Online. If you have three remote PowerShell connections up and running, any attempt to make a fourth simultaneous connection will fail, with the following error message:

- **Error**: *New-PSSession : [admin.vdomain.com] Connecting to remote server admin.vdomain.com failed with the following error message : The WS-Management service cannot process the request. The maximum number of concurrent shells for this user has been exceeded. Close existing shells or raise the quota for this user. For more information, see the [Remote Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting).*

- **Resolution**: The only way to resolve this issue is to close one or more of the previous connections. When you're finished with a Skype for Business Online session, we recommend that you use the **Remove-PSSession** cmdlet to end the session. This action will help you prevent this issue.
  
## The maximum number of concurrent shells for this tenant in Skype for Business Online has been exceeded
<a name="BKMKMaxNumberShellsTenant"> </a>

Although each administrator can have as many as three simultaneous connections to a Skype for Business Online tenant, no single tenant can have more than 20 simultaneous connections. For example, six administrators might each have three open sessions. If a seventh administrator tries to open more than two connections (resulting in a total of 21 simultaneous connections), this attempt will fail, with the following error message:
  
- **Error**: *New-PSSession : [admin.vdomain.com] Connecting to remote server admin.vdomain.com failed with the following error message : The WS-Management service cannot process the request. The maximum number of concurrent shells for this tenant has been exceeded. Close existing shells or raise the quota for this tenant. For more information, see the [Remote Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting)*

- **Resolution**: The only way to resolve this issue is to close one or more of the previous connections. When you're finished with a Skype for Business Online session, we recommend that you use the **Remove-PSSession** cmdlet to terminate that session. This will help you prevent this issue.  
 
## Related topics
[Set up your computer for skype for business online management using Windows PowerShell](set-up-your-computer-for-windows-powershell.md)

  
