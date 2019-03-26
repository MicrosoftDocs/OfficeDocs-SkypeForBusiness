---
title: 'Lync Server 2013: Setting up public instant messaging connectivity'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Setting up public instant messaging connectivity
ms:assetid: 816dea2a-96fa-4a36-b6c2-a9402675868b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205041(v=OCS.15)
ms:contentKeyID: 48184661
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Setting up public instant messaging connectivity in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-08_

If your organization wants to support public instant messaging (IM) connectivity with AOL, you cannot use the Lync Server Deployment Wizard to request the certificate. Instead, perform the steps in the following procedure.

<div>

## Setting Up Public Instant Messaging Connectivity

1.  On a Front End server, open Topology Builder. Expand Edge pools, then right click your Edge server or Edge server pool. Select Edit properties.

2.  In Edit Properties under General, select Enable federation for this Edge pool (Port 5061). Click OK.

3.  Click Action, select Topology, select Publish. When prompted on Publish the topology, click Next. When the Publish is finished, click Finish.

4.  On the Edge server, open the Lync Server Deployment wizard. Click Install or Update Lync Server System, then click Setup or Remove Lync Server Components. Click Run Again.

5.  At Setup Lync Server components, click Next. The summary screen will show actions as they are executed. Once the deployment is done, click View Log to view available log files. Click Finish to complete the deployment.

</div>

<div>

## To create a certificate request for the external interface of the Edge Server to support public IM connectivity with AOL

1.  When the required template is available to the CA, use the following Windows PowerShell cmdlet from at the Edge Server to request the certificate
    
        Request-CsCertificate -New -Type AccessEdgeExternal  -Output C:\ <certfilename.txt or certfilename.csr>  -ClientEku $true -Template <template name>
    
    The default certificate name of the template used for Lync Server is Web Server. Only specify the \<template name\> if you need to use a template that is different from the default template.
    
    <div>
    

    > [!IMPORTANT]  
    > If your organization wants to support public IM connectivity with AOL, you must use Windows PowerShell instead of the Certificate Wizard to request the certificate to be assigned to the external edge for the Access Edge service. This is because the Certificate Authority (CA) Web Server template that the Certificate Wizard uses to request a certificate does not support client EKU configuration. Before using Windows PowerShell to create the certificate, the CA administrator must create and deploy a new template that supports client EKU.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

