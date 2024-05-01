---  
title: Get information for connected peripherals
author: tonysmit
ms.author: mstonysmith 
manager: pamgreen
ms.reviewer: prashibadkur
ms.date: 04/26/2024  
ms.topic: article
audience: Admin
appliesto: 
  - Microsoft Teams
ms.service: msteams  
ms.subservice:  itpro-devices + itpro-rooms
ms.localizationpriority: medium
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
ms.custom: QuickDraft 
search.appverid: MET150  
f1.keywords:
  - NOCSH
description: Learn how to gather information about connected devices in Microsoft Teams using PowerShell and upload the data to the Teams Pro Management portal for BYOD monitoring and reporting.
---  
# Using PowerShell to Gather and Upload Teams BYOD Peripheral Data

This article will guide you through the process of using a PowerShell script to gather information about connected devices (peripherals) in Microsoft Teams and then upload that information to the Microsoft Teams Pro Management portal for Bring Your Own Device (BYOD) monitoring and reporting.

## Steps

1.  Download the **Get-TeamsBYODRoomDevices.ps1** script from the provided location or by selecting the "Download zip" option from the source code page.
2.  Unblock and extract the downloaded zip file. Move the **Get-TeamsBYODRoomDevices.ps1** script to your preferred location on your computer.
3.  Open a new PowerShell window and navigate to the location where you moved the **Get-TeamsBYODRoomDevices.ps1** script.
4.  Run the script by executing the following command in the PowerShell window:
   ```powershell
   \Get-TeamsBYODRoomDevices.ps1
   ```
6.  Follow the prompts to guide you through the this process:

    - 1. Wait for the script to detect and gather information about the connected devices.
    - 2. Connect the external devices when prompted.
    - 3. Enter the required details such as User Principal Name (UPN), Display Name, and Grouping ID for data collection when prompted.
    - 4. Provide the folder path where the **PERIPHERALS.csv** file will be saved when prompted.
    - 5. The script will process the discovered peripheral data and export it to the file path you specified.
    - 6. Review the exported data to ensure accuracy.
    - 7. When finished, type 'Y' when prompted to end the collection process.

7.  Upload the **PERIPHERALS.csv** file to the Teams Pro Management Portal.


