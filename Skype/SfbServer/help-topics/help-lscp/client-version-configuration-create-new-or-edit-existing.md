---
title: "Client Version Configuration Create New or Edit Existing"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/23/2015
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.ClientCVSettingEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 07fec57c-5cd3-422a-829a-0b62cb0092c4
description: "Client version configuration settings are used to turn client version control on or off. The Global client version configuration installs with Skype for Business Server and is used to enable or disable client version control for the entire server deployment. When the Global configuration is enabled, any client version policies you have in place will take effect when users attempt to log on. You can disable the Global client version configuration if you do not want any client version control to occur."
---

# Client Version Configuration: Create New or Edit Existing

Client version configuration settings are used to turn client version control on or off. The Global client version configuration installs with Skype for Business Server and is used to enable or disable client version control for the entire server deployment. When the Global configuration is enabled, any client version policies you have in place will take effect when users attempt to log on. You can disable the Global client version configuration if you do not want any client version control to occur.

You can also create site-specific client version configurations, allowing you to enable or disable client version control by site. Site-specific configurations take precedence over the Global configuration.

## Tasks you can perform

You can perform the following tasks on the **New Client Version Configuration** or **Edit Client Version Configuration** page:

- Add or modify the name of the client version configuration.

- Enable or disable client version control globally or for the specific site.

- Add or modify the default action for the client version configuration.

## UI Reference

The following lists describe the menus, command, fields, and properties on the page.

- **Scope** Identifies the scope (Global or Site) of the client version configuration.

- **Name** You can add or modify the name of the client version configuration.

- **Enable version control** You can enable or disable client version control globally or for the site, depending on the scope of the configuration.

- **Default action** You can select the default action that will be applied when a user attempts to log on using a client application for which there is no specific client version policy. You have the following options:

  - **Allow** Allows the client to log on if the client version does not match any filter in the client version policies list.

  - **Block** Prevents the client from logging on if the client version does not match any filter in the client version policies list.

  - **Block with URL** Prevents the client from logging on if the client version does not match any filter in the client version policies list, and includes an error message containing a URL where a newer client can be downloaded.

  - **Allow with URL** Allows the client to log on if the client version does not match any filter in the client version policies list, and includes an error message containing a URL where a newer client can be downloaded.

  - **URL** If you selected **Block with URL** or **Allow with URL**, you can specify the client download URL to include in the error message.

For details about interoperability among clients and client versions, see [Client Interoperability in Lync 2013 Preview](https://technet.microsoft.com/library/0f126571-91a2-45d5-855c-1e4ddb45fc04.aspx) in the Planning documentation. For details about working with client version configurations, see [Modify the Default Action for Clients Not Explicitly Supported or Restricted](https://technet.microsoft.com/library/548dd0f5-62fe-4c3f-8952-2b9fd4c5fff3.aspx) in the Operations documentation.

