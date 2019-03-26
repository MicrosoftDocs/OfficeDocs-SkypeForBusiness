---
title: "Install Database Options Page"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.InstallDatabaseOptionPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 926c47a0-3957-4892-b61a-7a4b569552c3
ROBOTS: NOINDEX, NOFOLLOW
description: "You configure advanced options for the placement of database and log files on your SQL Server. The options available are:"
---

# Install Database Options Page

You configure advanced options for the placement of database and log files on your SQL Server. The options available are:

> [!IMPORTANT]
> Select the option that best fits your requirements and policies pertaining to data and log file placement on your SQL Server computers.

 **Automatically determine database file location**: The default option uses an algorithm that determines the available space on the SQL Server and distributes the database and log files for optimal performance.

 **Use SQL Server instance defaults**: Select this option to place database file and log files based on the instance settings at SQL Server. The options are typically managed and configured by your Database Administrator.

 **Us these path on target SQL Server**: Select this option to define your own paths for SQL Server database and log files by typing the full path to the drive and folder where the database and log files will be placed.

> [!IMPORTANT]
> The paths that you enter may be modified based on performance optimization algorithms in the installation. For details, see [Database Installation Using Lync Server Management Shell](https://technet.microsoft.com/library/c90a6449-4dd5-4b18-b21c-ea2c2a64dc3c.aspx).

 **OK**: Click the OK button to commit your changes.

 **Cancel**: Click Cancel to discard any changes and return to the Install Database screen.

 **Help**: Click the Help button to access this Help page.

## See also

[SQL Server Data and Log File Placement](https://technet.microsoft.com/library/67aa525b-8aa3-474f-827e-8e1d4697f30f.aspx)
