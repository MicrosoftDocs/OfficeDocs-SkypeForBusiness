---
title: "Meeting Configuration"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 3/24/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.ConfMeetingSettingMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 24e8f749-d54c-4315-a8fe-bb9303b356ef
description: "Meeting configuration settings define the type of conferences (also calledmeetings) that users can create, and control how (or whether) anonymous users and dial-in conferencing users can join these conferences. These settings only apply to scheduled meetings. They do not apply to ad-hoc meetings created by clicking the Meet Now option in the client."
---

# Meeting Configuration

Meeting configuration settings define the type of conferences (also called "meetings") that users can create, and control how (or whether) anonymous users and dial-in conferencing users can join these conferences. These settings only apply to scheduled meetings. They do not apply to ad-hoc meetings created by clicking the Meet Now option in the client.

Meeting configurations apply on the global, site, or pool level:

- **Global meeting configuration:** The global meeting configuration is created by default. You can edit the global meeting configuration, but you cannot delete it. If you try to remove the global meeting configuration, all the settings are reset to the default values.

- **Site meeting configuration (optional):** You can create one or more site meeting configurations, each of which applies to a specific site. Site configurations override the global configuration.

- **Pool meeting configuration (optional):** You can create one or more pool meeting configurations, each of which applies to a specific pool. Pool configurations override the global configuration and site configurations.

The **Meeting Configuration** page displays a list of all the meeting configurations that are defined for your organization.

## Tasks you can perform

You can perform the following tasks from the **Meeting Configuration** page:

- Create a new site meeting configuration or pool meeting configuration

- Change the global configuration or an existing site configuration or pool configuration

- Delete a site configuration or pool configuration

## UI Reference

The following list describes the commands on the page.

- **New** Starts a new site meeting configuration or pool meeting configuration.

- **Edit** Opens the selected meeting configuration to edit it, selects all meeting configurations in the list, or deletes the selected site configuration or pool configuration.

    > [!NOTE]
    > For the global meeting configuration, **Delete** resets the settings to the default values.

- **Refresh** Refreshes the list of meeting configurations.

The following list describes the fields on the page.

- **Name** Identifies the meeting configuration.

- **Scope** Identifies the scope of the meeting configuration: global, site, or pool.

For details about working with meeting configurations, see [Create a or modify a Collection of Meeting Configuration Settings](https://technet.microsoft.com/library/ce6773c1-a0d5-4405-8e32-33a6f3a46a1a.aspx) in the Operations documentation.


