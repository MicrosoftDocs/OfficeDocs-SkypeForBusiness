---
title: Teams files and folders to exclude from antivirus scanning
author: msdmaguire
ms.author: dmaguire
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: ramesa
audience: admin
description: Improve Teams performance by excluding certain files and folders from regular antivirus scanning.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_PracticalGuidance
appliesto: 
- Microsoft Teams
---

Teams files and folders to exclude from antivirus scanning
=================================

You can improve the overall performance of your Teams deployment by preventing your antivirus programs from scanning certain Teams files and folders. This will avoid the expenditure of system resources on scanning files and folders that don't need to be scanned.

> [!NOTE]
> When your users download files or share files with each other, those files don't pass through the locations listed in the following section. The locations where your users do upload, download, or share files will still be regularly scanned by your antivirus program.

## Files and folders to add to your antivirus safe lists

Use the procedures supported by your antivirus program to add the following files and folders to your safe lists. Doing so will conserve system resources by avoiding antivirus scans of these locations.

### Programs

Add the following Teams programs to your antivirus safe list.

**%localappdata%\Microsoft\Teams\current\Teams.exe
%localappdata%\Microsoft\Teams\Update.exe**

### Folders

Add the following Teams folders to your antivirus safe list.

|Category  |Location  |
|---------|---------|
|Program files  |%localappdata%\Microsoft\Teams|
|Data files     |%appdata%\Microsoft\Teams\|