---
title: "Client Version Configuration"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/17/2018
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.lscp.ClientCVSettingMain
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: cb17314e-b89e-4821-8855-12f8fd2edc9b
description: "In addition to specifying the version of clients that you want to support in your environment, you can also specify a default action for clients that do not already have a version policy defined. This enables you to restrict which client versions are used in your environment, which can help you to control the costs associated with supporting multiple client versions."
---

# Client Version Configuration

In addition to specifying the version of clients that you want to support in your environment, you can also specify a default action for clients that do not already have a version policy defined. This enables you to restrict which client versions are used in your environment, which can help you to control the costs associated with supporting multiple client versions.

## Tasks you can perform

You can perform the following tasks on the **Client Version Configuration** page:

- Edit the default ( **Global**) client version configuration.

- Create client version configuration for a particular site.

- Enable and disable existing client version configurations.

> [!NOTE]
> Because anonymous users are not associated with a site, anonymous users are affected by global-level policies only.

## UI Reference

The following lists describe the menus, command, fields, and properties on the page.

- **New** You can create a client version configuration for a particular site.

- **Edit** You can change the options of any of the client version policies. Using this option, you can do the following:

  - **Show details** This option opens a dialog box in which you can change the options for a client version configuration.

  - **Select All** This option selects all client version configurations in the list.

  - **Delete** This option deletes all selected client version configurations.

- **Refresh** You can refresh the client version configuration list to verify the status of the options of all client version configurations.

For details about interoperability among clients and client versions, see [Client Interoperability in Lync 2013 Preview](/previous-versions/office/lync-server-2013/lync-server-2013-client-interoperability-in-lync-2013) in the Planning documentation. For details about working with client version configurations, see [Modify the Default Action for Clients Not Explicitly Supported or Restricted](/previous-versions/office/lync-server-2013/lync-server-2013-modify-the-default-action-for-clients-not-explicitly-supported-or-restricted) in the Operations documentation.