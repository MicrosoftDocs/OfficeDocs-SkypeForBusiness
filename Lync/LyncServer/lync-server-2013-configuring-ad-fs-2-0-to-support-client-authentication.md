---
title: 'Lync Server 2013: Configuring AD FS 2.0 to support client authentication'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring AD FS 2.0 to support client authentication
ms:assetid: 4d93d400-ccaa-4da8-a71b-d05d7ba79d93
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn308565(v=OCS.15)
ms:contentKeyID: 54973687
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring AD FS 2.0 to support client authentication in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-03_

There are two possible authentication types that can be configured to allow AD FS 2.0 to support authentication using smart cards:

  - Forms-based authentication (FBA)

  - Transport Layer Security Client Authentication

Using forms-based authentication, you can develop a web page that allows users to authenticate either by using their username/password or by using their smart card and PIN. This topic focuses on how to implement Transport Layer Security Client Authentication with AD FS 2.0. For more information about AD FS 2.0 authentication types, see AD FS 2.0: How to Change the Local Authentication Type at [http://go.microsoft.com/fwlink/p/?LinkId=313384](http://go.microsoft.com/fwlink/p/?linkid=313384).

<div>


**To Configure AD FS 2.0 to Support Client Authentication**

1.  Log in to the AD FS 2.0 computer using a Domain Admin account.

2.  Launch Windows Explorer.

3.  Browse to C:\\inetpub\\adfs\\ls

4.  Make a backup copy of the existing web.config file.

5.  Open the existing web.config file using Notepad.

6.  From the Menu bar, select **Edit** and then select **Find**.

7.  Search for **\<localAuthenticationTypes\>**.
    
    Note that there are four authentication types listed, one per line.

8.  Move the line containing the TLSClient authentication type to the top of the list in the section.

9.  Save and Close the web.config file.

10. Launch a Command Prompt with elevated privileges.

11. Restart IIS by running the following command:
    
        IISReset /Restart /NoForce

</div>

</div>

<span> </span>

</div>

</div>

</div>

