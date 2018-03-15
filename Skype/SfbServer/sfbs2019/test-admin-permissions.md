---
title: "Test admin permissions in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5dda3efd-0f84-4848-819e-87b1551066b1

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Test admin permissions in Lync Server 2013
[]
 **In this article**
  
[Description](#sectionSection0)
  
[Running the test](#sectionSection1)
  
[Determining success or failure](#sectionSection2)
  
[Reasons why the test might have failed](#sectionSection3)
  
****

|||
|:-----|:-----|
|Verification schedule  <br/> |After initial Lync Server deployment. As needed if permission-related issues arise.  <br/> |
|Testing tool  <br/> |Windows PowerShell  <br/> |
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsOUPermission cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsOUPermission"}```|
   
## Description
<a name="sectionSection0"> </a>

When you install Lync Server 2013 one of the tasks that were performed by the Setup program gives the RTCUniversalUserAdmins group the Active Directory permissions that are needed to manage users, computers, contacts, application contacts, and InetOrg persons. If you have disabled permission inheritance in Active Directory setup won't be able to assign those permissions. As a result, members of the RTCUniversalUserAdmins group won't be able to manage Lync Server entities. Those management privileges will only be available to domain administrators. 
  
The Test-CsOUPermission cmdlet verifies that the required permissions that are needed to manage users, computers, and other objects are set on an Active Directory container. If those permissions are not set, you can resolve this problem by running the [Grant-CsOUPermission](grant-csoupermission.md) cmdlet. 
  
Note that Grant-CsOUPermission can only assign permissions to members of the RTCUniversalUserAdmins group. You can't use this cmdlet to grant permissions to an arbitrary user or group. If you want a different user or group to have user management permissions, you should add that user (or group) to the RTCUniversalUserAdmins group. 
  
For more information on OU permissions, see the article [Permissions inheritance Is disabled on computers, users, or InetOrgPerson containers in Lync Server 2013](permissions-inheritance-is-disabled-on-computers-users-or-inetorgperson-containe.md).
  
## Running the test
<a name="sectionSection1"> </a>

To verify that management permissions are set on a container, run the Test-CsOUPermission cmdlet followed by the distinguished name of the container and by the type of permissions that you are verifying. For example, this command checks whether user permissions are set on the OU ou=Redmond,dc=litwareinc,dc=com:
  
```
Test-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user"
```

To verify multiple permissions by using a single command, enclose each permission type enclosed in quotation marks, then separate those types by using commas. For example, this one command verifies user, computer, and contact permissions:
  
```
Test-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user", "computer", "contact"
```

For more information, see the help topic for the [Test-CsOUPermission](test-csoupermission.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the required permissions have already been set then Test-CsOUPermission will return a one-word response:
  
True
  
If the required permissions are not set then Test-CsOUPermission will return the value False. You might have to search for a moment to find this value. It will typically be embedded inside several accompanying warnings. For example:
  
WARNING: access control entry (ACE) atl-cs-001\RTCUniversalUserReadOnlyGroup; allow; ReadProperty; ContainerInherit; Descendents; bf967aba-0de6-11d0-00aa003049e2; d819615a-3b9b-4738-b47e-f1bd8ee3aea4
  
WARNING: The access control entries (ACEs) on the object "OU=NorthAmerica,DC=atl-cs-001\DC=litwareinc,DC=com" are not ready.
  
False
  
WARNING: "Test-CsOUPermission" processing has completed with warnings. "2" warnings were recorded during this run.
  
WARNING: Detailed results can be found at "C:\Users\Admin\AppData\Local\Temp\Test-CsOUPermission-5d7a89af-f854-4a9c-87e3-69e37e58de.html".
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

If Test-CsOUPermission fails that will usually mean that the specified permission has not been assign to the RTCUniversalUserAdmins group. You can resolve this problem, and assign the required permissions, by using the Grant-CsOUPermission cmdlet. For example, this command gives OU permissions for users, contacts, and inetOrgPersons to the RTCUniversalUserAdmins group:
  
```
Grant-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user", "contact", "inetOrgPerson"
```

For more information, see the help topic for the Grant-CsOUPermission cmdlet.
  

