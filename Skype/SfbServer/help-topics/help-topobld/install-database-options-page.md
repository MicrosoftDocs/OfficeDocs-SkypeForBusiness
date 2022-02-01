---
title: "Install Database Options Page"
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
- ms.lync.tb.InstallDatabaseOptionPage
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 926c47a0-3957-4892-b61a-7a4b569552c3
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
> The paths that you enter may be modified based on performance optimization algorithms in the installation. For details, see [Database Installation Using Lync Server Management Shell](/previous-versions/office/lync-server-2013/lync-server-2013-database-installation-using-lync-server-management-shell).

 **OK**: Click the OK button to commit your changes.

 **Cancel**: Click Cancel to discard any changes and return to the Install Database screen.

 **Help**: Click the Help button to access this Help page.

## See also

[SQL Server Data and Log File Placement](/previous-versions/office/lync-server-2013/lync-server-2013-sql-server-data-and-log-file-placement)