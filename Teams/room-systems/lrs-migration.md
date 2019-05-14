---
title: "Migrate Lync Room System devices to Microsoft Teams Rooms"
ms.author: v-lanac
author: lanachin
ms.reviewer: sohailta
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: M365-voice
ms.assetid: 
description: "Read this topic to learn how to migrate Lync Room System devices to use the Microsoft Teams Rooms software."
---

# Migrate Lync Room System (LRS) devices to Microsoft Teams Rooms

Lync Room System (LRS) devices with Skype Room System Version 1 (SRS v1) software has reached [end of support on October 9, 2018](https://support.microsoft.com/en-us/help/4043450/products-reaching-end-of-support-for-2018). This means Skype Room Systems v1 software will no longer get any product updates or fixes anymore. Customers with Lync Room System devices using Skype Room System v1 software are advised to upgrade their devices to Microsoft Teams Rooms.

Microsoft Teams Rooms software works with Microsoft Teams in addition to Skype for Business Server and Online services for meetings and calling on all Microsoft Teams Rooms supported devices.

Your existing devices **may** continue to work after the end of Skype Room System v1 software support. However, if this software hits a software bug that needs Microsoft to release a fix, it will not be supported. SRS v1 uses TLS 1.0/ 1.1 which will be deprecated by Microsoft in the future. You can learn more about [Preparing for TLS 1.0/1.1 Deprecation](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/bc-p/223608). Microsoft Teams Rooms is adding support for TLS 1.2 and will continue to work past October 31, 2018. Skype for Business on-premises customers should not disable TLS 1.0/1.1 until Microsoft Teams Rooms announces support for TLS 1.2 regardless of general guidelines on TLS 1.0/1.1 deprecation.

## Which devices are affected?

Here is the list of the devices that are affected by this change:

- Crestron RL
- [Crestron RL2](https://www.crestron.com/en-US/Products/Featured-Solutions/Crestron-RL-2)
- [SMART Room systems](https://support.smarttech.com/en/hardware/room-systems-skype)
- [Polycom CX8000](http://www.polycom.com/products-services/products-for-microsoft/skype-for-business/cx8000.html)

## Upgrade options

There are multiple options for upgrading Lync Room Systems to the next generation of Microsoft Teams Rooms.

### Crestron hardware Trade-in program

Crestron will provide an upgrade to the [Crestron SR system](https://www.crestron.com/en-us/products/featured-solutions/crestron-sr) or equivalent for all Non-Crestron Lync Room System customers (e.g Smart or Polycom LRS). See details of this program [here](https://support.crestron.com/app/answers/answer_view/a_id/1000220) or <!-- For details, -->[email](mailto:lrsupgrade@crestron.com) Crestron LRS support.  

### Crestron RL2 upgrade to Microsoft Teams Rooms

Existing Crestron RL2 (also referred to as Crestron RL200) customers can acquire an upgrade kit to upgrade current RL2 to RL3 using a for a minimal cost per device. See details of this program [here](https://crestron.com/en-US/Products/Workspace-Solutions/Unified-Communications/Crestron-RL-2/CCS-UC-250-KIT).

### SMART Room Systems upgrade

For SMART LRS customers, apart from Crestron hardware trade-in program, SMART is also working on providing a solution to upgrade to Microsoft Teams Rooms. This upgrade will be provided by SMART Technologies Inc. to customer under product support. Please see more about this [here](https://support.smarttech.com/docs/hardware/room-systems-skype/srs-skype-v2/en/about/default.cshtml).


## What should you do?

We recommend you plan to update Lync Room System devices to Microsoft Teams Rooms before TLS 1.0/1.1 deprecation using upgrade options mentioned above. Additionally, you may also consider replacing existing devices with new devices certified for Microsoft Teams Rooms. See [Room devices](https://aka.ms/roomdevices) for details and also take a look at [Microsoft Teams Rooms requirements](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/clients-and-devices/requirements).  

> [!NOTE]
> Touch and whiteboard functionality is not yet supported in Microsoft Teams Rooms. Touch and whiteboard support is currently planned for Microsoft Teams Rooms and will be added in 2019.

> [!NOTE]
> Microsoft Teams Rooms software supports the TLS 1.2 protocol as of December 14, 2018 with app version 4.0.64.0. For on-premises customers, enabling communication over TLS 1.2 for Microsoft Teams Rooms requires Skype for Business Server 2015 Cumulative Update 9 (CU9) or Skype for Business Server 2019 Cumulative Update 1 (CU1). The change should not affect Skype for Business Online customers as client changes are forward and backward compliant.
