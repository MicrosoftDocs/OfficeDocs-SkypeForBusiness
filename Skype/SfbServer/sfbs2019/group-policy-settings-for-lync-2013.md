---
title: "Group Policy settings for Lync 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5917a52b-dae0-4ec0-8548-a68dc20ab71c
description: "In previous versions of Lync and Office Communicator, a stand-alone Communicator.adm administrative template was available for configuring client Group Policy settings. For Lync 2013, new administrative template files (.admx and .adml files) are included along with the Office Group Policy Administrative Template. The availability of Lync 2013 .admx and .adml files allows you to download templates and centrally manage Group Policy settings for all your Office programs and language packs. For details, seeOffice 2013 Administrative Template files (ADMX, ADML)in the Office 2013 documentation at https://go.microsoft.com/fwlink/p/?linkid=267516."
---

# Group Policy settings for Lync 2013
[]
In previous versions of Lync and Office Communicator, a stand-alone Communicator.adm administrative template was available for configuring client Group Policy settings. For Lync 2013, new administrative template files (.admx and .adml files) are included along with the Office Group Policy Administrative Template. The availability of Lync 2013 .admx and .adml files allows you to download templates and centrally manage Group Policy settings for all your Office programs and language packs. For details, see "Office 2013 Administrative Template files (ADMX, ADML)" in the Office 2013 documentation at [https://go.microsoft.com/fwlink/p/?linkid=267516](https://go.microsoft.com/fwlink/p/?linkid=267516).
  
## Client Bootstrapping Policies

There are several client bootstrapping policies that you should configure before users sign in to the server for the first time. Because these policies take effect before the client signs in and begins receiving in-band provisioning settings from the server, you can use Group Policy to configure them. For more information, see [Configuring client bootstrapping policies in Lync Server 2013](configuring-client-bootstrapping-policies.md) in the Deployment documentation. 
  

