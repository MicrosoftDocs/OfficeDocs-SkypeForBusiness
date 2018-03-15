---
title: "Test admin topology rights in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.custom: httpsfix
ms.assetid: 0c03b7fd-449a-47ad-8263-ce811164cbce

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Test admin topology rights in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsSetupPermission cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsSetupPermission"}```|
   
## Description
<a name="sectionSection0"> </a>

By default, only domain administrators can enable a Lync Server topology and make large changes to the Lync Server infrastructure. This won't be a problem as long as your domain administrators and your Lync Server administrators are one and the same.In many organizations Lync Server administrators do not hold administrative rights to the whole domain. By default, that means that these administrators (defined as members of the RTCUniversalServerAdmins group) can't make Lync Server topology changes. To give members of the RTCUniversalServerAdmins group the right to make topology changes, you must assign the required Active Directory permissions by using the [Grant-CsSetupPermission](grant-cssetuppermission.md) cmdlet. 
  
The Test-CsSetupPermission cmdlet verifies that the required permissions that are needed to install Lync Server or one of its components are configured on the specified Active Directory container. If the permissions are not assigned, you can then run the Grant-CsSetupPermission cmdlet to give members of the RTCUniversalServerAdmins group the right to install and enable Lync Server.
  
> [!NOTE]
> For a detailed list of permissions assigned by Grant-CsSetupPermission, see the blog post [Grant-CsSetupPermission and Grant-CsOUPermission](https://blogs.technet.com/b/jenstr/archive/2011/02/07/grant-cssetuppermission-and-grant-csoupermission.aspx). 
  
## Running the test
<a name="sectionSection1"> </a>

To determine whether setup permissions are assigned for an Active Directory container, call the Test-CsSetupPermission cmdlet. Specify the distinguished name of the container to be checked. For example, this command verifies setup permissions on the container ou=CsServers,dc=litwareinc,dc=com:
  
```
Test-CsSetupPermission -ComputerOU "ou=CsServers,dc=litwareinc,dc=com"
```

For more information, see the help topic for the [Test-CsSetupPermission](test-cssetuppermission.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If Test-CsSetupPermission determines that the required permissions have already been set on an Active Directory container then the cmdlet will return the value True:
  
True
  
If permissions are not set, Test-CsSetupPermission will return the value False. Note that this value will typically be enclosed in many warning messages. For example:
  
WARNING: Access control entry (ACE) atl-cs-001\RTCUniversalServerAdmins; Allow; ExtendedRight; None; None; 1131f6aa-9c07-11d1-f79f-00c04fc2dcd2
  
WARNING: The access control entries (ACEs) on the object "CN=Computers,DC=litwareinc,DC=com" are not ready.
  
False
  
WARNING: "Test-CsSetupPermission" processing has completed with warnings. "2" warnings were recorded during this run.
  
WARNING: Detailed results can be found at "C:\Users\Admin\AppData\Local\Temp\Test-CsSetupPermission-1da99ba6-abe2-45e4-8b16-dfd244763118.html".
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Although there are rare exceptions, if Test-CsSetupPermission fails that typically means that setup permissions are not assigned for the specified Active Directory container. Those permissions can be assigned by using the Grant-CsSetupPermission cmdlet. For example, this command grants setup permissions to the Computers container in the domain litwareinc.com:
  
```
Grant-CsSetupPermission -ComputerOU "cn=Computers,dc=litwareinc,dc=com"
```

For more information, see the help topic for the [Test-CsSetupPermission](test-cssetuppermission.md) cmdlet. 
  

