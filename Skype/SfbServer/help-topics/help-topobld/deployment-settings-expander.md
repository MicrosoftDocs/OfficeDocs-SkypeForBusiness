---
title: "Deployment Settings Expander"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/25/2015
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.DeploymentSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7220ec1f-38cb-4297-870e-591a832cd2f2
description: "You can edit the properties for an existing deployment with the following sections:"
---

# Deployment Settings Expander

You can edit the properties for an existing deployment with the following sections:

- SIP domain

- Simple URLs

- Central Management Server

## SIP Domain

To edit the **Default SIP domain**, enter the new domain name.

To add **Additional supported SIP domains**, type the name of the domain name that you need to add. Click **Add** to accept it as a new Session Initiation Protocol (SIP) domain name.

To update an existing additional SIP domain name, select the domain name and make changes in the text box. Click **Update** to accept the change.

To remove a defined additional SIP domain name, select the domain name, and then click **Remove**.

When you are finished with all changes on the Edit Properties page, click **OK** to save the changes. Click **Cancel** to discard changes.

## Simple URLs

To modify or define the simple URLs, you decide which of the three simple URLs that you will edit or change. You can choose from the Phone access URL, the Meeting URL, and the Administrative access URL.

To modify either the Phone access URL or the Meeting URL, select the URL that you need to change. Click **Edit URL**. You then edit the URL, and click **OK** to save the URL. Click **Cancel** to discard any changes.

To add a new URL, click **Add**. In the **Add simple URL** dialog, specify the URL and click **OK** to save the URL. Select **Make this the active URL for the selected domain** if you need to set the new URL as the active URL. Click **Cancel** to discard any changes.

To make a different URL the active URL (as noted by the green checkmark next to the URL), select the URL, and then click **Make Active**.

> [!NOTE]
> There can be only one active URL for each SIP domain.

If you need to remove a URL, select the URL and click **Remove**.

> [!CAUTION]
> Read the information on the simple URLs settings dialog page carefully. Removing a meeting URL can cause meetings that have been scheduled by users to be inaccessible. Consider leaving the former URL after you make the new meeting URL active. When you are sure that users are no longer using the old meeting URL, you can safely remove it.

To edit or change the Administrative access URL, edit the entry.

When you are finished with all changes on the Edit Properties page, click **OK** to save the changes. Click **Cancel** to discard changes.

## Central Management Server

The Central Management Server can be changed from one defined Front End pool to another defined Front End pool. To change the location of the Central Management Server, select the Front End pool from the drop-down list under **Front End server to install Central Management Server on**. A Front End Server can be an Enterprise Edition Front End pool or a Standard Edition Front End Server.

> [!IMPORTANT]
> After you have defined, published, and deployed the Central Management store for the infrastructure, you cannot change the location of the Central Management store without relocating the Central Management store to another Front End by an external process.

For details about moving the Central Management store, see [Move-CsManagementServer](https://docs.microsoft.com/powershell/module/skype/move-csmanagementserver?view=skype-ps) in the Windows PowerShell cmdlet reference.

## See also

For details about defining and configuring these settings, see [Defining and Configuring the Topology](https://technet.microsoft.com/library/51d1601e-4f83-48d4-ad08-3b4d5e2003aa.aspx).


