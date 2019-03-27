---
title: 'Lync Server 2013: Issues with the environment test'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Issues with the environment test
ms:assetid: ff1fe0d3-35b2-41ef-87e7-6a61e9e1d2ca
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205421(v=OCS.15)
ms:contentKeyID: 48185970
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Issues with the environment test in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

Best Practices Analyzer provides a way for you to verify that your Lync Server 2013 environment is a supported configuration. As part of the Active Directory Domain Services check, Best Practices Analyzer does the following:

  - Verifies the Active Directory Domain Services forest and schema preparation.

  - Identifies the number of Active Directory Domain Services sites and domains in the deployment.

  - Checks the forest and domain levels.

  - Checks the domain controller version.

  - Identifies the domain, configuration, and schema naming context.

  - Identifies the number of enabled users.

  - Checks where the global Active Directory Domain Services settings are stored.

  - Checks for the service connection points (SCPs) for Lync Server.

  - Identifies the database version.

<div>

## Resolving Issues with the Environment

If the environment test found problems with your environment, these problems are probably caused by issues with your Active Directory configuration or the level of software running on specific servers. For example, if Best Practices Analyzer identifies any domain controllers in your environment that are running Windows Server 2000, it will issue a warning and you will need to upgrade those domain controllers to a supported version of Windows Server.

</div>

</div>

<span> </span>

</div>

</div>

</div>

