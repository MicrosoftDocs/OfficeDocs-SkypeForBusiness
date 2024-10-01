---
title: Add peripherals to inventory
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: eviegrimshaw
ms.date: 05/02/2024  
ms.topic: article
audience: Admin
appliesto: 
  - Microsoft Teams
ms.service: msteams  
ms.subservice: itpro-rooms
ms.localizationpriority: medium
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Rooms
  - Tier1
ms.custom: QuickDraft 
search.appverid: MET150  
f1.keywords:
  - NOCSH
description: Learn how to gather information about connected devices and add them to your inventory in Microsoft Teams
---

  # Add peripherals to inventory

The script utilizes PowerShell cmdlets and native Windows API functions to gather information about connected devices (peripherals). It can tell the differences between different types of peripherals such as USB devices, monitors, cameras, speakers, and microphones.

When you run the PowerShell script, the data is exported to a CSV file that can be upload to Teams Pro Management Portal for managing, monitoring, and reporting usage of devices in BYOD rooms and Bookable Desks.

## Steps

1. Go [here](https://www.microsoft.com/en-us/download/details.aspx?id=106063) to download the **Get-TeamsBYODRoomDevices.ps1** PowerShell script.
1. Unblock and extract the downloaded zip file. Move the **Get-TeamsBYODRoomDevices.ps1** script to your preferred location on your PC.
1. Open a new PowerShell window and navigate to the location where you moved the **Get-TeamsBYODRoomDevices.ps1** script.

   > [!NOTE]
   > You can optionally open the script and customize it before you run it. However, don't change the sheet name. The sheet name must be named **PERIPHERALS**.

1. Run the script by executing the following command in the PowerShell window:

   ```powershell
   \Get-TeamsBYODRoomDevices.ps1
   ```
   
1. The script prompts will guide you through the process:

   - Wait for the script to detect and gather information about the connected devices.
   - Connect the external devices when prompted.
   - Enter the required details such as User Principal Name (UPN), Display Name, and Grouping ID for data collection when prompted.
   - Provide the folder path where the PERIPHERALS.csv file will be saved when prompted.
   - The script will process the discovered peripheral data and export it to the specified file path.
      
1. Review the exported data to verify accuracy. 
1. When finished, enter 'Y' when prompted to end the collection process.
1. Open the CSV created on the set area path and notice the device details collected including Account, Display Name, Product ID, Vendor ID, Serial Number, Peripheral Name, Peripheral Type and Group ID. 

   > [!NOTE]
   > Group ID is a way to still 'group them' for later assignment if while individually collecting the peripheral data you do not know the UPN or Display Name for the group of peripherals being collected. This is because Teams Pro Management portal won't have any understanding of Group ID, it is more for keep the peripherals grouped in the output CSV so an account plus the display name could be assigned to each at a later time.

1. Save the CSV file in .XLSX format. The first sheet in the CSV file must be titled **PERIPHERALS**.

   > [!IMPORTANT]
   > If sensitivity labels are enabled in your tenant, verify that the Excel file has a label of non-business, public, or general.  

1. Sign in and open the [Microsoft Teams Pro Management portal](https://portal.rooms.microsoft.com/), in the **Devices** page, select __Import__ to add the device inventory to upload the file you modified.

1. Verify that the device and desk association is updated successfully in the Teams Pro Management portal.
