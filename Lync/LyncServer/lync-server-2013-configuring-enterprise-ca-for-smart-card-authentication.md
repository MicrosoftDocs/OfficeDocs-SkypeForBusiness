---
title: 'Lync Server 2013: Configuring Enterprise CA for smart card authentication'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring Enterprise CA for smart card authentication
ms:assetid: c24e0891-e108-4cb6-9902-c6a4c8e68455
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn308571(v=OCS.15)
ms:contentKeyID: 54973692
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Enterprise CA for smart card authentication in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-03_

The following section describes how to configure an Enterprise Root Certification Authority (CA) to support smart card authentication. For information on how to install an Enterprise Root CA, see Install an Enterprise Root Certification Authority at [http://go.microsoft.com/fwlink/p/?LinkID=313364](http://go.microsoft.com/fwlink/p/?linkid=313364).

<div>

## Configuring an Enterprise Root Certificate Authority to Support Smart Card Authentication

The following steps describe how to configure an Enterprise Root CA to support Smart Card Authentication:

1.  Log in to the Enterprise CA computer using a Domain Admin account.

2.  Launch System Manager, and verify that the Certificate Authority Web Enrollment role is installed.

3.  From the **Administrative Tools** menu, open the **Certification Authority** management console.

4.  In the Navigation pane, expand **Certification Authority**.

5.  Right click on **Certificate Templates**, select **New**, then select **Certificate Template to Issue**.

6.  Select **Enrollment Agent**, **Smartcard User**, and **Smartcard Logon**.

7.  Click **OK**.

8.  Right click on **Certificate Templates**.

9.  Select **Manage**.

10. Open the properties of the Smartcard User template.

11. Click on the **Security** tab.

12. Change the permissions as follows:
    
      - Add individual user AD accounts with Read/Enroll (Allow) permissions, or
    
      - Add a security group containing smart card users with Read/Enroll (Allow) permissions, or
    
      - Add the Domain Users group with Read/Enroll (Allow) permissions

</div>

</div>

<span> </span>

</div>

</div>

</div>

