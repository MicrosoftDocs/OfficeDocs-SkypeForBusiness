---
title: "Persistent Chat General Settings Expander"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
manager: serdars
ms.date: 3/27/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.PersistentChatGeneralSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 275ee1ae-ca58-4963-bc95-523319f90d96
description: "You edit the General settings for the Persistent Chat Server or Persistent Chat Server pool by configuring or defining these properties:"
---

# Persistent Chat General Settings Expander
 
You edit the **General** settings for the Persistent Chat Server or Persistent Chat Server pool by configuring or defining these properties:
  
 **General**
  
- **FQDN**: Edit this setting to define the fully qualified domain name of your Persistent Chat Server or Persistent Chat Server pool
    
- **Display name of the Persistent Chat pool**: Define this setting to provide a user friendly and user readable setting for the server or pool. This setting will make it easier for your users to associate a given Persistent Chat Server or Persistent Chat Server pool based on the display name instead of a more difficult to understand fully qualified domain name.
    
- **Persistent Chat port**: Specify the port to use for Persistent Chat.
    
You edit the **Associations** settings for the Persistent Chat Server or Persistent Chat Server pool by configuring or defining these properties:
  
 **Associations**
  
- **SQL Server store**: Select the SQL Server store and optional named instance from the list.
    
    Click **New** to define a new SQL Server store and optional instance.
    
- Select the **Enable SQL Server store mirroring** check box if you want to enable mirroring for the primary SQL Server store.
    
    If you chose to enable SQL Server store mirroring, select the store and instance from the list **Mirroring SQL Server store**.
    
    Click **New** to define a new SQL Server store and optional instance.
    
- Select the **Use SQL Server mirroring witness to enable automatic failover** check box if you want automatic failover of the primary SQL Server store.
    
    If you chose to enable SQL Server store mirroring witness to enable automatic failover, select the store and instance from the list.
    
    Click **New** to define a new SQL Server store and optional instance for the witness store.
    
- Select the **Use backup SQL Server stores to enable disaster recovery** check box if you want to enable the use of SQL Server disaster recovery
    
    If you chose to enable disaster recovery, select a store and instance from the **Backup SQL Server store** list.
    
    Click **New** to define a new SQL Server store and optional instance.
    
- Select the **Enable SQL Server store mirroring** check box if you want to enable mirroring for the backup SQL Server mirroring store.
    
    If you chose to enable backup SQL Server store mirroring, select the store and instance from the list **Backup SQL Server store mirror**.
    
    Click **New** to define a new SQL Server store and optional instance.
    
- Select the **Use SQL Server mirroring witness to enable automatic failover** check box if you want automatic failover of the backup SQL Server store.
    
    If you chose to enable SQL Server store mirroring witness to enable automatic failover, select the store and instance from the list.
    
    Click **New** to define a new SQL Server store and optional instance for the witness store.
    
- Select the **Enable compliance** check box if you want to enable the use of a compliance database
    
    If you chose to enable compliance, select a store and instance from the **Compliance SQL Server store** list.
    
    Click **New** to define a new SQL Server store and optional instance.
    
- Select the **Enable SQL Server store mirroring** check box if you want to enable mirroring for the compliance SQL Server store.
    
    If you chose to enable compliance SQL Server store mirroring, select the store and instance from the list **Compliance SQL Server store mirror**.
    
    Click **New** to define a new SQL Server store and optional instance.
    
- Select the **Use SQL Server mirroring witness to enable automatic failover** check box if you want automatic failover of the compliance SQL Server store.
    
    If you chose to enable SQL Server store mirroring witness to enable automatic failover, select the store and instance from the list.
    
    Click **New** to define a new SQL Server store and optional instance for the witness store.
    
- If you chose to enable compliance, select a store and instance from the **Backup compliance SQL Server store** list.
    
    Click **New** to define a new SQL Server store and optional instance.
    
- Select the **Enable SQL Server store mirroring** check box if you want to enable mirroring for the compliance SQL Server store.
    
    If you chose to enable compliance SQL Server store mirroring, select the store and instance from the list **Backup compliance SQL Server store mirror**.
    
    Click **New** to define a new SQL Server store and optional instance.
    
- Select the **Use SQL Server mirroring witness to enable automatic failover** check box if you want automatic failover of the backup compliance SQL Server store.
    
    If you chose to enable SQL Server store mirroring witness to enable automatic failover, select the store and instance from the list.
    
    Click **New** to define a new SQL Server store and optional instance for the witness store.
    
- **File store** Select a file store location from the list, or click **New** to create a new file store.
    
  **OK** Accepts and commits changes to the dialog.
  
  **Cancel** Discards changes and closes the dialog.
  
  **Help** Displays this help screen.
  
## See also

[Plan for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/persistent-chat-server.md)
  
[Add Persistent Chat Server to your Skype for Business Server 2015 topology](../../deploy/deploy-persistent-chat-server/add-persistent-chat-server.md)
  
[Configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015](../../deploy/deploy-persistent-chat-server/configure-hadr-for-persistent-chat.md)
