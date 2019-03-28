---
title: "Persistent Chat Add-in Main Page"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 3/27/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.PersistentChatAddinMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0c0ecf64-258d-4b43-8fac-fa5ffa4e7646
description: "You can use the Add-in section of the Persistent Chat page to associate URLs with Persistent Chat rooms. These URLs appear in the client in the chat room in the conversation extensibility pane. An administrator must add Add-ins to the list of registered add-ins, and chat room managers/Creators must associate rooms with one of the registered add-ins before users can see this upgrade in their client."
---

# Persistent Chat Add-in Main Page

You can use the **Add-in** section of the **Persistent Chat** page to associate URLs with Persistent Chat rooms. These URLs appear in the client in the chat room in the conversation extensibility pane. An administrator must add Add-ins to the list of registered add-ins, and chat room managers/Creators must associate rooms with one of the registered add-ins before users can see this upgrade in their client.

Add-ins are used to extend the in-room experience. A typical add-in might include a URL pointing to a Silverlight application that intercepts when a stock ticker is posted to a chat room, and shows the stock history in the extensibility pane. Other examples include embedding a OneNote 2013 URL in the chat room as an add-in to include some shared context, such as "Top of mind" or "Topic of the day."

To create Add-ins for Persistent Chat rooms, see [Configure add-ins for Persistent Chat rooms in Skype for Business Server 2015](../../manage/persistent-chat/configure-add-ins.md). If you are a Persistent Chat Administrator, you can create add-ins by using the control panel or Windows PowerShell cmdlets.

## Tasks you can perform

You can perform the following tasks on the **Add-in** page:

- [Configure add-ins for Persistent Chat rooms in Skype for Business Server 2015](../../manage/persistent-chat/configure-add-ins.md)

## To configure Add-ins for chat rooms

The following lists describe the menus, command, fields, and properties on the page.

1. From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.

2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods that you can use to start control panel, see [Open Lync Server Administrative Tools](https://technet.microsoft.com/library/8c58de94-9e0a-4368-9e14-9afcaa1142d0.aspx).

3. In the left navigation bar, click **Persistent Chat**, and then click **Add-in**.

    For multiple Persistent Chat Server pool deployments, select the appropriate pool from the drop-down list.

4. On the **Add-in** page, click **New**.

5. In **Select a Service**, select the service corresponding to the Persistent Chat Server pool where you need to create the Add-in. Add-ins cannot be moved from one pool to another or shared between different pools.

6. In **New Add-in**, do the following:

   - In **Name**, specify a name for the new add-in.

   - In **URL**, specify the URL to be associated with the add-in. URLs are limited to http and https protocols.

7. Click **Commit**.

## See also

For details about Persistent Chat Server features and capabilities, see [Plan for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/persistent-chat-server.md), [Deploy Persistent Chat Server in Skype for Business Server 2015](../../deploy/deploy-persistent-chat-server/deploy-persistent-chat-server.md), and [Manage Persistent Chat Server in Skype for Business Server 2015](../../manage/persistent-chat/persistent-chat.md).


