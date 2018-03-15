---
title: "Installing the Lync Server 2013 core files and the RTCLocal database"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 206f0c1d-40f7-45b6-aa62-88aaef6cf7f6
description: "To install the Lync Server 2013 core files on a computer, complete the following procedure. The RTCLocal database is automatically installed when you install the core files. Note that you do not need to install SQL Server on the watcher nodes. Instead, SQL Server Express is automatically installed for you."
---

# Installing the Lync Server 2013 core files and the RTCLocal database
[]
To install the Lync Server 2013 core files on a computer, complete the following procedure. The RTCLocal database is automatically installed when you install the core files. Note that you do not need to install SQL Server on the watcher nodes. Instead, SQL Server Express is automatically installed for you.
  
To install the Lync Server 2013 core files and the RTCLocal database:
  
1. On the watcher node computer, click **Start**, click **All Programs**, click **Accessories**, right-click **Command Prompt**, and then click **Run as administrator**.
    
2. In the console window, type the following command and then press ENTER, using the appropriate path to your Lync Server setup files: 
    
  ```
  D:\Setup.exe /BootstrapLocalMgmt
  ```

To verify that the core Lync Server components were successfully installed, click **Start**, click **All Programs**, click **Lync Server 2013**, and then click **Lync Server Management Shell**. In the Lync Server 2013 Management Shell, type the following Windows PowerShell command, and then press ENTER:
  
```
Get-CsWatcherNodeConfiguration
```

The first time you run this command, you no data is returned because you have not configured any watcher node computers yet. As long as the command runs without returning an error, you can assume that the Lync Server setup completed successfully.
  
If your watcher node computer is located inside your perimeter network, you can run the following command to verify the installation of Lync Server 2013:
  
```
Get-CsPinPolicy
```

You will receive information similar to the following, depending on the number of personal identification number (PIN) policies configured for use in your organization:
  
```
Identity             : Global
Description          :
MinPasswordLength    : 5
PINHistoryCount      : 0
AllowCommonPatterns  : False
PINLifetime          : 0
MaximumLogonAttempts :

```

If you see information about your PIN policies, it means that you have successfully installed the core components.
  

