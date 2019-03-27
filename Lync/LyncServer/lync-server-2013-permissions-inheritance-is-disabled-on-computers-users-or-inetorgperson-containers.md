---
title: 'Lync Server 2013: Permissions inheritance Is disabled on computers, users, or InetOrgPerson containers'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Permissions inheritance Is disabled on computers, users, or InetOrgPerson containers
ms:assetid: c472ad21-a93d-4fcb-a3d9-60a2134a87fa
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412970(v=OCS.15)
ms:contentKeyID: 48185348
ms.date: 12/19/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Permissions inheritance Is disabled on computers, users, or InetOrgPerson containers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-12-19_

In a locked-down Active Directory Domain Services, Users and Computer objects are often placed in specific organizational units (OUs) with permissions inheritance disabled to help secure administrative delegation and to enable use of Group Policy objects (GPOs) to enforce security policies.

Domain preparation and server activation set the access control entries (ACEs) required by Lync Server 2013. When permissions inheritance is disabled, the Lync Server security groups cannot inherit these ACEs. When these permissions are not inherited, Lync Server security groups cannot access settings, and the following two issues arise:

  - To administer Users, InetOrgPersons, and Contacts, and to operate servers, the Lync Server security groups require ACEs set by the domain preparation procedure on each user’s property sets, real-time communications (RTC), RTC User Search, and Public Information. When permissions inheritance is disabled, security groups do not inherit these ACEs and cannot manage servers or users.

  - To discover servers and pools, servers running Lync Server rely on ACEs set by activation on computer-related objects, including the Microsoft Container and Server object. When permissions inheritance is disabled, security groups, servers, and pools do not inherit these ACEs and cannot take advantage of these ACEs.

To address these issues, Lync Server provides the **Grant-CsOuPermission** cmdlet. This cmdlet sets required Lync Server ACEs directly on a specified container and organizational units and the objects within the container or organizational unit.

<div>

## Set Permissions for User, InetOrgPerson, and Contact Objects after Running Domain Preparation

In a locked-down Active Directory environment where permissions inheritance is disabled, domain preparation does not set the necessary ACEs on the containers or organizational units holding Users or InetOrgPerson objects within the domain. In this situation, you must run the **Grant-CsOuPermission** cmdlet on each container or OU that has User or InetOrgPerson objects for which permissions inheritance is disabled. If you have a central forest topology, you must also perform this procedure on the containers or OUs that hold contact objects. For details about central forest topologies, see [Supported Active Directory topologies in Lync Server 2013](lync-server-2013-supported-active-directory-topologies.md) in the Supportability documentation. The ObjectType parameter specifies the object type. The OU parameter specifies the organizational unit.

This cmdlet adds the required ACEs directly on the specified containers or OUs and the User or InetOrgPerson objects within the container. If the OU on which this command is executed has child OUs with User or InetOrgPerson objects, the permissions will not be applied on those. You will need to run the command on each child OU individually. This is a common scenario with Lync Hosting Deployments e.g. Parent OU=OCS Tenants, DC=CONTOSO,DC=LOCAL and child OU=Tenant1, OU=OCS Tenants ,DC=CONTOSO,DC=LOCAL.

You need user rights equivalent to Domain Admins group membership to run this cmdlet. If the authenticated user ACEs have also been removed in the locked-down environment, you must grant this account read-access ACEs on the relevant containers or OUs in the forest root domain as described in [Authenticated user permissions are removed in Lync Server 2013](lync-server-2013-authenticated-user-permissions-are-removed.md) or use an account that is a member of the Enterprise Admins group.

**To set required ACEs for User, InetOrgPerson, and Contact objects**

1.  Log on to a computer joined to the domain with an account that is a member of the Domain Admins group or that has equivalent user rights.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Run:
    
        Grant-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> 
        -OU <DN name for the OU container relative to the domain root container DN> [-Domain <Domain FQDN>]
    
    If you do not specify the Domain parameter, the default value is the local domain.
    
    For example:
    
        Grant-CsOuPermission -ObjectType "User" -OU "cn=Redmond,dc=contoso,dc=net" -Domain "contoso.net"

4.  In the log file, look for **\<Success\>** Execution Result at the end of each task to verify that the permissions were set, and then close the log window. Or, you can run the following command to determine whether the permissions were set:
    
        Test-CsOuPermission -ObjectType <type of object> 
        -OU <DN name for the OU container relative to the domain root container DN> 
        [-Domain <Domain FQDN>] [-Report <fully qualified path and name of file to create>]
    
    For example:
    
        Test-CsOuPermission -ObjectType "User" -OU "cn=Redmond,dc=contoso,dc=net" -Domain "contoso.net" -Report "C:\Log\OUPermissionsTest.html"

</div>

<div>

## Set Permissions for Computer Objects after Running Domain Preparation

In a locked-down Active Directory environment where permissions inheritance is disabled, domain preparation does not set the necessary ACEs on the containers or OUs that hold Computer objects within the domain. In this situation, you must run the **Grant-CsOuPermission** cmdlet on each container or OU that has computers running Lync Server where permissions inheritance is disabled. The ObjectType parameter specifies the object type.

This procedure adds the required ACEs directly on the specified containers.

You need user rights equivalent to Domain Admins group membership to run this cmdlet. If the authenticated user ACEs have also been removed, you must grant this account read-access ACEs on the relevant containers in the forest root domain as described in [Authenticated user permissions are removed in Lync Server 2013](lync-server-2013-authenticated-user-permissions-are-removed.md) or use an account that is a member of the Enterprise Admins group.

**To set required ACEs for computer objects**

1.  Log on to the domain computer with an account that is a member of the Domain Admins group or that has equivalent user rights.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Run:
    
        Grant-CsOuPermission -ObjectType <Computer> 
        -OU <DN name for the computer OU container relative to the domain root container DN> 
        [-Domain <Domain FQDN>][-Report <fully qualified path and name of output report>]
    
    If you do not specify the Domain parameter, the default value is the local domain.
    
    For example:
    
        Grant-CsOuPermission -ObjectType "Computer" -OU "ou=Lync Servers,dc=litwareinc,dc=com" -Report "C:\Logs\OUPermissions.xml"

4.  In the example log file C:\\Logs\\OUPermissions.xml, you would look for **\<Success\>** Execution Result at the end of each task and verify that there are no errors, and then close the log. You can run the following cmdlet to test permissions:
    
        Test-CsOuPermission -ObjectType <type of object> 
        -OU <DN name for the OU container relative to the domain root container DN> [-Domain <Domain FQDN>]
    
    For example:
    
        Test-CsOuPermission -ObjectType "user","contact" -OU "cn=Bellevue,dc=contoso,dc=net" -Domain "contoso.net"
    
    <div>
    

    > [!NOTE]  
    > If you run domain preparation on the forest root domain in a locked-down Active Directory environment, be aware that Lync Server requires access to the Active Directory Schema and Configuration containers.<BR>If the default authenticated user permission is removed from the Schema or the Configuration containers in AD&nbsp;DS, only members of the Schema Admins group (for Schema container) or Enterprise Admins group (for Configuration container) are permitted to access the given container. Because Setup.exe, Lync Server Management Shell cmdlets, and Lync Server Control Panel require access to these containers, Setup and installation of the administrative tools will fail unless the user running the installation has user rights equivalent to Schema Admins and Enterprise Admins group membership.<BR>To remedy this situation, you must grant RTCUniversalGlobalWriteGroup group Read, Write access to the Schema and Configuration containers.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

