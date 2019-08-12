---
title: "Testing admin permissions in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "How to test admin permissions in Skype for Business Server"
---

# Testing admin permissions in Skype for Business Server

| | |
|--|--|
|Verification schedule|After initial Skype for Business Server deployment. As needed if permission-related issues arise.|
|Testing tool|Windows PowerShell|
|Permissions required|When run locally using the Skype for Business Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.<br><br/>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsOUPermission cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:<br/><br/>Get-CsAdminRole \| Where-Object {$_.Cmdlets -match "Test-CsOUPermission"}|
|||

## Description

When you install Skype for Business Server, one of the tasks that was performed by the Setup program gives the RTCUniversalUserAdmins group the Active Directory permissions that are needed to manage users, computers, contacts, application contacts, and InetOrg persons. If you have disabled permission inheritance in Active Directory, setup won't be able to assign those permissions. As a result, members of the RTCUniversalUserAdmins group won't be able to manage Skype for Business Server entities. Those management privileges will only be available to domain administrators. 

The Test-CsOUPermission cmdlet verifies that the required permissions needed to manage users, computers, and other objects are set on an Active Directory container. If those permissions are not set, you can resolve this problem by running the [Grant-CsOUPermission cmdlet](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsOUPermission). 

Note that Grant-CsOUPermission can only assign permissions to members of the RTCUniversalUserAdmins group. You can’t use this cmdlet to grant permissions to an arbitrary user or group. If you want a different user or group to have user management permissions, you should add that user (or group) to the RTCUniversalUserAdmins group. 


## Running the test

To verify that management permissions are set on a container, run the Test-CsOUPermission cmdlet followed by the distinguished name of the container and by the type of permissions that you are verifying. For example, this command checks whether user permissions are set on the OU ou=Redmond,dc=litwareinc,dc=com:

`Test-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user"`

To verify multiple permissions by using a single command, enclose each permission type enclosed in quotation marks, then separate those types by using commas. For example, this one command verifies user, computer, and contact permissions:

`Test-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user", "computer", "contact"`

For more information, see the [help topic for the Test-CsOUPermission cmdlet](https://docs.microsoft.com/en-us/powershell/module/skype/test-csoupermission).

## Determining success or failure

If the required permissions have already been set, Test-CsOUPermission will return a one-word response:

True

If the required permissions are not set, Test-CsOUPermission will return the value False. You might have to search for a moment to find this value. It will typically be embedded inside several accompanying warnings. For example:

WARNING: access control entry (ACE) atl-cs-001\RTCUniversalUserReadOnlyGroup; allow; ReadProperty; ContainerInherit; Descendents; bf967aba-0de6-11d0-00aa003049e2; d819615a-3b9b-4738-b47e-f1bd8ee3aea4 

WARNING: The access control entries (ACEs) on the object "OU=NorthAmerica,DC=atl-cs-001\DC=litwareinc,DC=com" are not ready. 

False 

WARNING: "Test-CsOUPermission" processing has completed with warnings. "2" warnings were recorded during this run. 

WARNING: Detailed results can be found at "C:\Users\Admin\AppData\Local\Temp\Test-CsOUPermission-5d7a89af-f854-4a9c-87e3-69e37e58de.html". 

## Reasons why the test might have failed

If Test-CsOUPermission fails, it usually means that the specified permission has not been assigned to the RTCUniversalUserAdmins group. You can resolve this problem, and assign the required permissions, by using the Grant-CsOUPermission cmdlet. For example, this command gives OU permissions for users, contacts, and inetOrgPersons to the RTCUniversalUserAdmins group:

`Grant-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user", "contact", "inetOrgPerson"`

For more information, see the [help topic for the Test-CsOUPermission cmdlet](https://docs.microsoft.com/en-us/powershell/module/skype/test-csoupermission).
