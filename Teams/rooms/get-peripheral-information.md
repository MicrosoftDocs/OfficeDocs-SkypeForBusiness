---
title: Get information for connected peripherals
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: prashibadkur
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
description: Learn how to gather information about connected devices in Microsoft Teams using PowerShell and upload the data to the Teams Pro Management portal for BYOD monitoring and reporting.
---
  
# Using PowerShell to gather and upload information on devices in BYOD Rooms and Bookable Desks to Teams Rooms Pro Management Portal 

The script utilizes PowerShell cmdlets and native Windows API functions to gather information about connected devices (peripherals). 

It distinguishes between different types of peripherals such as USB devices, monitors, cameras, speakers, microphones, etc. 

Data is exported to a CSV file for uploading to Teams Pro Management Portal for monitoring and reporting of devices in BYOD rooms and Bookable Desks . 

## Steps:

1. Download the **Get-TeamsBYODRoomDevices.ps1** script from the provided location or by selecting the "Download zip" option from the source code page.

1. Unblock and extract the downloaded zip file. Move the **Get-TeamsBYODRoomDevices.ps1** script to your preferred location on your computer.

1. Open a new PowerShell window and navigate to the location where you moved the **Get-TeamsBYODRoomDevices.ps1** script.

4. Run the script by executing the following command in the PowerShell window:

   ```powershell
   \Get-TeamsBYODRoomDevices.ps1
   ```
5. Follow the prompts to guide you through the this process:

- Wait for the script to detect and gather information about the connected devices. 

- Connect the external devices when prompted 

- Enter the required details such as User Principal Name (UPN), Display Name, and Grouping ID for data collection when prompted 

- Provide the folder path where the PERIPHERALS.csv file will be saved when prompted 

- The script will process the discovered peripheral data and export it to the specified file path. 

- Review the exported data to ensure accuracy. 

- If finished, enter 'y' when prompted to end the collection process. 

6. Open the CSV created on the set area path and notice the device details collected including Account, Display Name, Product ID, Vendor ID, Serial Number, Peripheral Name, Peripheral Type and Group ID. 

Note: The purpose of the Group ID, if while individual collecting the peripheral data does not know the UPN or Display Name for the group of peripherals being collected, and is a way to still 'group them' for later assignment. Since PMP won't have any understanding of Group ID, it is more for keep the peripherals grouped in the output csv so an account+display name could be assigned to each properly at a later time. 

7. Copy the data from this Excel.  

8. Go to Teams Pro Management Portal, in the Devices page, click Export to download the device inventory. 

9. Open the Excel file and verify that it contains all the devices and room information. 

10. In the Excel file, select the PERIPHERALS tab and paste the device information copied in Step 7. 

11. Save the file after pasting that information. 

12. Go back to the Inventory Devices page and click Import to upload the modified file. 

13. Verify that the device-desk association is updated successfully on Teams Pro Management Portal. 