---
title: "Client Version Policy"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.custom:
- ms.lync.lscp.ClientCVPolicyMain
ms.prod: skype-for-business-itpro
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.assetid: 4f84bc0f-e1df-4acb-b8ef-57f165b0153b
ROBOTS: NOINDEX, NOFOLLOW
description: "You can specify the version of clients that are supported in your environment. When two clients that are running different versions interact, the features that are available to either client can be limited by the capabilities of the other client."
---

# Client Version Policy

You can specify the version of clients that are supported in your environment. When two clients that are running different versions interact, the features that are available to either client can be limited by the capabilities of the other client. To make the greatest use of features included in Skype for Business Server and to improve the overall user experience, you can use the client version filter to restrict the client versions that are used in your environment. By using the client version filter, you can also help reduce costs associated with supporting multiple client versions.

## Tasks you can perform

You can perform the following tasks on the **Client Version Policy** page:

- Edit the default ( **Global**) client version policy.

- Create client version policies for a particular site or pool.

- Create client version policies that can be assigned to individual users.

> [!NOTE]
> Because anonymous users are not associated with a user, site, or service, anonymous users are affected by global-level policies only.

## UI Reference

The following lists describe the menus, commands, fields, and properties on the page.

- **New** You can create one or more of each of the following client version policies:

  - Site policy

  - Pool policy

  - User policy

- **Edit** You can change the options of any of the client version policies. Using this option, you can do the following:

  - **Show details** This option opens a dialog box in which you can change the options for a client version policy.

  - **Select All** This option selects all client version policies in the list.

  - **Delete** This option deletes all selected client version policies.

- **Refresh** You can refresh the client version policy list to verify the status of the options of all client version policies.

For details about interoperability among clients and client versions, see [Client Interoperability](/previous-versions/office/lync-server-2013/lync-server-2013-client-interoperability-in-lync-2013) in the Planning documentation. For details about working with client version policies, see [Specify the Client Versions Supported in Your Organization](/previous-versions/office/lync-server-2013/lync-server-2013-specifying-the-client-applications-that-can-be-used-to-log-on-to-lync-server-2013) in the Operations documentation.