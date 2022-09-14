---
title: "Client Version Policy Create New or Edit Existing"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/23/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.lscp.ClientCVPolicyEdit
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: e32c6712-6dc9-4de9-8d74-9fdccf3de1ba
description: "You can specify the version of clients that are supported in your environment. When two clients that are running different versions interact, the features that are available to either client can be limited by the capabilities of the other client. To make the greatest use of features included in Skype for Business Server 2015 and to improve the overall user experience, you can use the client version filter to restrict the client versions that are used in your environment. By using the client version filter, you can also help reduce costs associated with supporting multiple client versions."
---

# Client Version Policy: Create New or Edit Existing

You can specify the version of clients that are supported in your environment. When two clients that are running different versions interact, the features that are available to either client can be limited by the capabilities of the other client. To make the greatest use of features included in Skype for Business Server 2015 and to improve the overall user experience, you can use the client version filter to restrict the client versions that are used in your environment. By using the client version filter, you can also help reduce costs associated with supporting multiple client versions.

> [!IMPORTANT]
> Filters are listed in order of precedence. For example, if you have a filter that allows clients running version 1.5 to connect, followed by a filter that blocks clients running a version earlier than 2.0, the first filter takes precedence, and clients running version 1.5 are allowed to connect.

## Tasks you can perform

You can perform the following tasks on the **New Client Version Policy** or **Edit Client Version Policy** page:

- Add or modify the name or description of the client version policy.

- Add or modify client version rules for the client version policy.

## UI Reference

The following lists describe the menus, commands, fields, and properties on the page.

- **Scope** Identifies the scope (Site, Pool, or User) of the client version policy.

- **Name** You can add or modify the name of the client version policy.

- **Description** You can add a description to help in identifying the policy in the list on the Client Version Policy page.

- **New** You can add a new client version rule to the policy.

- **Show details** This option opens a dialog box in which you can change the options for a client version rule.

- **Remove** This option removes the selected client version rule from the policy.

- **Up and down arrows** This option moves the selected client version rule up or down in priority. Rules are processed in the order listed.

For details about interoperability among clients and client versions, see [Client Interoperability in Lync 2013 Preview](/previous-versions/office/lync-server-2013/lync-server-2013-client-interoperability-in-lync-2013) in the Planning documentation. For details about working with client version policies, see [Specify the Client Versions Supported in Your Organization](/previous-versions/office/lync-server-2013/lync-server-2013-specifying-the-client-applications-that-can-be-used-to-log-on-to-lync-server-2013) in the Operations documentation.