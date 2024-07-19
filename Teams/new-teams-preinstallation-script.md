---
title:  Pre-installation script for new Teams client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 07/12/2024
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: daro
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article documents a script that administrators can run before beginning an organization's upgrade to new Teams clients, or after an upgrade fails for some or all clients. This script should help determine what may be blocking the installation of new Teams client on a device or devices.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# New Teams client pre-installation script

Microsoft has a [pre-installation check script](https://aka.ms/NewTeamsReadinessCheck) designed to identify why devices can't be updated to the new Teams client. The script also suggests solutions to any problems it finds. Admins can save time moving to new Teams by running the script in these two use cases:

- Before you install new Teams for the first time.
- After the new Teams client installation fails on some devices.

Admins, by running this script, can proactively identify and resolve issues, making it easier to install the new Teams client across their organization.

> [!NOTE]
> If you want to get pre-install check status across all devices, run this script using device management software like Intune. If you want to have the pre-install script check the status for a single device, you can run it directly on the device.

## Using the script

You can run the script locally on a device, in Intune, or using some other device management software.

We have sample instructions to run the script in Intune at this location: [Sample instructions](https://github.com/microsoft/MDE-PowerBI-Templates/blob/master/ASR_scripts/AddShortcuts_with_Intune.md)

After running the script:

- If run locally, admins will see the failures and suggested resolutions in the command line. Admin can fix the issues and run the new Teams client installation again.
- If the script is run in Intune or other device management software:
  - Administrators can see issues and suggested resolutions for each device.
  - Administrators can download these results as a CSV file.
  - Admins can filter the CSV file for each error to identify all devices requiring a specific fix.
  - Admin can fix one error at a time across all machines and rerun the new Teams installation.
