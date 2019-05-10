---
title: "Testing admin topology rights in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "How to test topology rights in Skype for Business Server"
---

# Testing admin topology rights in Skype for Business Server

| | |
|--|--|
|Verification schedule|After initial Skype for Business Server deployment. As needed if permission-related issues arise.|
|Testing tool|Windows PowerShell|
|Permissions required|When run locally using the Skype for Business Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.<br/><br/>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsSetupPermission cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:<br/><br/>Get-CsAdminRole \| Where-Object {$_.Cmdlets -match "Test-CsSetupPermission"}|
|||

## Description

By default, only domain administrators can enable a Skype for Business Server topology and make large changes to the Skype for Business Server infrastructure. This won't be a problem as long as your domain administrators and your Skype for Business Server administrators are one and the same. In many organizations, Skype for Business Server administrators do not hold administrative rights to the whole domain. By default, that means that these administrators (defined as members of the RTCUniversalServerAdmins group) can't make Skype for Business Server topology changes. To give members of the RTCUniversalServerAdmins group the right to make topology changes, you must assign the required Active Directory permissions by using the [Grant-CsSetupPermission](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsSetupPermission) cmdlet.
 
The Test-CsSetupPermission cmdlet verifies that the required permissions that are needed to install Skype for Business Server or one of its components are configured on the specified Active Directory container. If the permissions are not assigned, you can then run the Grant-CsSetupPermission cmdlet to give members of the RTCUniversalServerAdmins group the right to install and enable Skype for Business Server.

## Running the test

To determine whether setup permissions are assigned for an Active Directory container, call the Test-CsSetupPermission cmdlet. Specify the distinguished name of the container to be checked. For example, this command verifies setup permissions on the container ou=CsServers,dc=litwareinc,dc=com:

`Test-CsSetupPermission -ComputerOU "ou=CsServers,dc=litwareinc,dc=com"`

For more information, see the help topic for the [Test-CsSetupPermission](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsSetupPermission) cmdlet.

## Determining success or failure

If Test-CsSetupPermission determines that the required permissions have already been set on an Active Directory container then the cmdlet will return the value True:

True 

If permissions are not set, Test-CsSetupPermission will return the value False. Note that this value will typically be enclosed in many warning messages. For example:

WARNING: Access control entry (ACE) atl-cs-001\RTCUniversalServerAdmins; Allow; ExtendedRight; None; None; 1131f6aa-9c07-11d1-f79f-00c04fc2dcd2 

WARNING: The access control entries (ACEs) on the object "CN=Computers,DC=litwareinc,DC=com" are not ready. 

False 

WARNING: "Test-CsSetupPermission" processing has completed with warnings. "2" warnings were recorded during this run. 

WARNING: Detailed results can be found at "C:\Users\Admin\AppData\Local\Temp\Test-CsSetupPermission-1da99ba6-abe2-45e4-8b16-dfd244763118.html". 

## Reasons why the test might have failed

Although there are rare exceptions, if Test-CsSetupPermission fails that typically means that setup permissions are not assigned for the specified Active Directory container. Those permissions can be assigned by using the Grant-CsSetupPermission cmdlet. For example, this command grants setup permissions to the Computers container in the domain litwareinc.com:

`Grant-CsSetupPermission -ComputerOU "cn=Computers,dc=litwareinc,dc=com"`

For more information, see the help topic for the [Test-CsSetupPermission](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsSetupPermission) cmdlet.
