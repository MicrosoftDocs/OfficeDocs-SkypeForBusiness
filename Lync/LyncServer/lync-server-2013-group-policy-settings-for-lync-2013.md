---
title: 'Lync Server 2013: Group Policy settings for Lync 2013'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Group Policy settings for Lync 2013
ms:assetid: 5917a52b-dae0-4ec0-8548-a68dc20ab71c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204924(v=OCS.15)
ms:contentKeyID: 48184235
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Group Policy settings for Lync 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-03_

In previous versions of Lync and Office Communicator, a stand-alone Communicator.adm administrative template was available for configuring client Group Policy settings. For Lync 2013, new administrative template files (.admx and .adml files) are included along with the Office Group Policy Administrative Template. The availability of Lync 2013 .admx and .adml files allows you to download templates and centrally manage Group Policy settings for all your Office programs and language packs. For details, see “Office 2013 Administrative Template files (ADMX, ADML)” in the Office 2013 documentation at <http://go.microsoft.com/fwlink/p/?linkid=267516>.

<div>

## Client Bootstrapping Policies

There are several client bootstrapping policies that you should configure before users sign in to the server for the first time. Because these policies take effect before the client signs in and begins receiving in-band provisioning settings from the server, you can use Group Policy to configure them. For more information, see [Configuring client bootstrapping policies in Lync Server 2013](lync-server-2013-configuring-client-bootstrapping-policies.md) in the Deployment documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

