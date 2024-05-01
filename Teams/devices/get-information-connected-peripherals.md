---  
title: "How to guide to fetch information on connected devices (peripherals)"  
description:  
author:  
ms.author: prashibadkur  
manager:  
ms.date: 04/26/2024  
ms.topic:  
ms.service: msteams  
ms.subservice:  
ms.localizationpriority:  
ms.collection:  
ms.custom: QuickDraft  
ms.reviewer:  
search.appverid: MET150  
f1.keywords:  
audience:  
ai-usage:  
- ai-assisted  
---  

Customer Intent for this Article: Learn how to gather information about connected devices in Microsoft Teams using PowerShell and upload the data to the Teams Pro Management Portal for BYOD monitoring and reporting.
Article:

# Using PowerShell to Gather and Upload Teams BYOD Peripheral Data

In this article, we will guide you through the process of using a PowerShell script to gather information about connected devices (peripherals) in Microsoft Teams and upload the data to the Teams Pro Management Portal for Bring Your Own Device (BYOD) monitoring and reporting.

## Procedure

1.  Download the **Get-TeamsBYODRoomDevices.ps1** script from the provided location or by selecting the "Download zip" option from the source code page.

2.  Unblock and extract the downloaded zip file. Move the **Get-TeamsBYODRoomDevices.ps1** script to your preferred location on your computer.

3.  Open a new PowerShell window and navigate to the location where you moved the **Get-TeamsBYODRoomDevices.ps1** script.

4.  Run the script by executing the following command in the PowerShell window: `.\Get-TeamsBYODRoomDevices.ps1`

5.  Follow the prompts to guide you through the peripheral data collection process:

6.  1.  Wait for the script to detect and gather information about the connected devices.
    2.  Connect the external devices when prompted.
    3.  Enter the required details such as User Principal Name (UPN), Display Name, and Grouping ID for data collection when prompted.
    4.  Provide the folder path where the **PERIPHERALS.csv** file will be saved when prompted.
    5.  The script will process the discovered peripheral data and export it to the specified file path.
    6.  Review the exported data to ensure accuracy.
    7.  If finished, enter 'y' when prompted to end the collection process.

7.  Upload the **PERIPHERALS.csv** file to the Teams Pro Management Portal.

## Recommendations
